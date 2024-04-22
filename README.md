# 1:50 FPV RC Car

## BOM

-   Brains - [ESP32S3 Sense](https://www.unmannedtechshop.co.uk/product/seeedxiao-esp32s3-sense/) ([alternative shop](https://thepihut.com/products/seeed-studio-xiao-esp32s3-sense))
-   Battery - [14500 cell with >= 2A discharge](https://www.ecoluxshopdirect.co.uk/ampsplus-14500-1000mah-3-7v-battery-protected)
-   Battery terminals
-   Switch

### Drivetrain

-   Wheels and Tyres - [Slot car 10" alloy](https://www.pendleslotracing.co.uk/pcs-classic-10-alloy-wheels-tyres-15-5x5-7mm-x2.html)
-   Motor -
-   Gears -
-   H Bridge -

### Steering

-   Servo - [1.7g low voltage](https://stevewebb.co.uk/index.php?pid=SM17GMICRO&area=Servo)
-   Bearings - 3/32 x 3/16 x 3/32 [SFR133ZZ](https://simplybearings.co.uk/shop/p155063/SFR133ZZ-Budget-Metal-Shielded-Stainless-Steel-Flanged-Deep-Groove-Ball-Bearing-3/32x3/16x3/32-inch/product_info.html)
-   Fasteners -
-   3/32 ID spacer - Can probably 3D print this

## Deplying the web page

The webpage to be used by the software needs to be compressed with gzip and then placed in an array. This takes a few steps to accomplish:

1. Remove excess whitespace from `index.html` to minimise final size. Specifically tabs and newlines can be removed by using find and replace
2. Compress the html with the command `gzip -c index.html | xxd -p` and copy the contents into a file
3. Prepend `0x` and append a comma to each byte by searching with the find regex `(\S{2})` and replace with `0x$1,`
4. Replace the contents of `const uint8_t index_ov2640_html_gz[]` found in **camera/camera_index.hpp**
5. Update `index_ov2640_html_gz_len` with the length of the array. _TODO: This should really not be a thing_
