---
title: "Converting RGB TIFF and RGB PS to CMYK TIFF and CMYK PS?"
date: 2006-10-19
forum: General Help
---

### Post by TuxCrafter on 2006-10-19
Converting RGB TIFF and RGB PS to CMYK TIFF and CMYK PS?

Hello,

I used the gimp for making some print work. But I now have a problem gimp don't support CMYK and i can't find other good working tools.

I tried the Separate Plugin for the gimp but it does not work enough. I don't have icc profiles.
[http://www.blackfiveservices.co.uk/separate.shtml](http://www.blackfiveservices.co.uk/separate.shtml)

I installed Krita that clams to have CMYK support and loaded my TIFF and converted the image. But there is a know bug it can't save a TIFF with CMYK so that doesn't work either.

I also tried bitcmyk2tiff it works for a small part, but it used a fix sized output of A4.
[http://www.blackfiveservices.co.uk/bitcmyk2tiff.shtml](http://www.blackfiveservices.co.uk/bitcmyk2tiff.shtml)

I also tried this script:
[http://www.met.rdg.ac.uk/~dan/work/H2ConvertToCMYK.html](http://www.met.rdg.ac.uk/~dan/work/H2ConvertToCMYK.html)

I think it also generate a PDF file in CMYK format but it is A4.

How do I check if a PDF file is CMYK under Linux?

The print shops want only the image so that they can fit it in there programs i think?

So how do I prepare my artwork for a print studio under linux?

Please help :confused:

---

### Post by peterazor on 2007-11-25
This is exactly a problem of mine as well...
At home I use Scribus, Inkscape and GIMP. But the problem is that GIMP doesn't support CMYK colourspace which is essential when preparing images for press. What I usually do is that I use spot colours in Scribus and when exporting to .pdf I choose 'Convert spot colors to process' option. When printing, I import this .pdf to InDesign or Quark and print using Trueflow, which works fine but it's not a real solution.
I tried to use Krita to convert .tiffs to CMYK, there's a bug TuxCrafter mentioned. So I tried to go for the worst possible option and use .jpgs. But when I import those images to Scribus, it imports it as 72dpi pics for some strange reason. This is also a bug in Krita, since when I import the same pic edited in GIMP, Scribus imports it as 300dpi image.
Hopefully GIMP will support CMYK colourspace soon...

---

### Post by TuxCrafter on 2007-11-25
Hopes this helps you converting your images! Feedback is appreciated.

```
convert "TuxCrafter - Visitekaartje v1.5 - Front - RGB.tiff" -font Courier -colorspace CMYK -density 300x300 "TuxCrafter - Visitekaartje v1.5 - Front - CMYK.tiff"
identify -verbose "TuxCrafter - Visitekaartje v1.5 - Front - CMYK.tiff" > identify_front_1.txt

convert "TuxCrafter - Visitekaartje v1.5 - Back - RGB.tiff" -font Courier -colorspace CMYK -density 300x300 "TuxCrafter - Visitekaartje v1.5 - Back - CMYK.tiff"
identify -verbose "TuxCrafter - Visitekaartje v1.5 - Back - CMYK.tiff" > identify_back_1.txt

convert "TuxCrafter - Visitekaartje v1.5 - Front - RGB.tiff" -colorspace CMYK -resize 1028x673 -font Courier "TuxCrafter - Visitekaartje v1.5 - Front - CMYK.tif"
identify -verbose "TuxCrafter - Visitekaartje v1.5 - Front - CMYK.tif" > identify_front_2.txt

convert "TuxCrafter - Visitekaartje v1.5 - Back - RGB.tiff" -colorspace CMYK -resize 1028x673 -font Courier "TuxCrafter - Visitekaartje v1.5 - Back - CMYK.tif"
identify -verbose "TuxCrafter - Visitekaartje v1.5 - Back - CMYK.tif" > identify_back_2.txt

convert "TuxCrafter - Visitekaartje v1.5 - Front - RGB.tiff" -colorspace CMYK -resize 1028x673 -density 300x300 -font Courier "TuxCrafter - Visitekaartje v1.5 - Front - CMYK.tif"
identify -verbose "TuxCrafter - Visitekaartje v1.5 - Front - CMYK.tif" > identify_front_cmyk_resize.txt

convert "TuxCrafter - Visitekaartje v1.5 - Front - RGB.tiff" -colorspace CMYK -colors 3 -resize 1028x673 -density 300x300 -font Courier "TuxCrafter - Visitekaartje v1.5 - Front - Color - CMYK.tif"
identify -verbose "TuxCrafter - Visitekaartje v1.5 - Front - Color - CMYK.tif" > identify_front_cmyk_color.txt
```

---

### Post by TuxCrafter on 2007-11-25
```
gs -sDEVICE=pswrite -sOutputFile=frontpages.ps -dNOPAUSE -dBATCH front_1.ps front_2.ps front_3.ps
gs -sDEVICE=pswrite -sOutputFile=backpages.ps -dNOPAUSE -dBATCH back_1.ps back_2.ps back_3.ps
psnup -n 3 -p a4 frontpages.ps frontpages_combined.ps
psnup -n 3 -p a4 backpages.ps backpages_combined.ps
gs -sDEVICE=pswrite -sOutputFile=printfile_combined.ps -dNOPAUSE -dBATCH frontpages_combined.ps backpages_combined.ps
lp -s -d 'HP_Color_LaserJet_8500DN' printfile_combined.ps

gs -sDEVICE=pswrite -sOutputFile="TuxCrafter - Visitekaartje v1.5.ps" -dNOPAUSE -dBATCH "TuxCrafter - Visitekaartje v1.5 - Front - RGB.ps" "TuxCrafter - Visitekaartje v1.5 - Back - RGB.ps"
./ps2pdfcmyk.sh "TuxCrafter - Visitekaartje v1.5.ps"

gs -sDEVICE=bitcmyk -sOutputFile=front_1.bitcmyk -r300x300 -dGrayValues=256 "TuxCrafter - Visitekaartje v1.5 - Front - RGB.ps"
bitcmyk2tiff front_1.bitcmyk "TuxCrafter - Visitekaartje v1.5 - Front - 300 - CMYK.tiff"

gs -sDEVICE=bitcmyk -sOutputFile=back_1.bitcmyk -r300x300 -dGrayValues=256 "TuxCrafter - Visitekaartje v1.5 - Back - RGB.ps"
bitcmyk2tiff back_1.bitcmyk "TuxCrafter - Visitekaartje v1.5 - Back - 300 - CMYK.tiff"

gs -sDEVICE=bitcmyk -sOutputFile=front_1.bitcmyk -r600x600 -dGrayValues=256 "TuxCrafter - Visitekaartje v1.5 - Front - RGB.ps"
bitcmyk2tiff front_1.bitcmyk "TuxCrafter - Visitekaartje v1.5 - Front - 600 - CMYK.tiff"

gs -sDEVICE=bitcmyk -sOutputFile=back_1.bitcmyk -r600x600 -dGrayValues=256 "TuxCrafter - Visitekaartje v1.5 - Back - RGB.ps"
bitcmyk2tiff back_1.bitcmyk "TuxCrafter - Visitekaartje v1.5 - Back - 600 - CMYK.tiff"

lp -d 'HP_Color_LaserJet_8500DN' "TuxCrafter - Visitekaartje v1.5.ps"
lp -d 'HP_Color_LaserJet_8500DN' "TuxCrafter - Visitekaartje v1.5_cmyk.pdf"

```

---

