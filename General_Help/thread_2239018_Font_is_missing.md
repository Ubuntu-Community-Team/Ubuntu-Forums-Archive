---
title: "Font is missing"
date: 2014-08-11
forum: General Help
---

### Post by Andy_Crowd on 2014-08-11
Hello! Where can I download this font?
I am getting an error like:
wmmount: font -*-helvetica-bold-r-*-*-10-*-*-*-*-*-*-* not found

---

### Post by Kiran_Kankipati on 2014-08-11
Hi,

Generally you can download the choice of fonts (.ttf files) from any online websites.

To install just create a custom folder and copy the .ttf file(s).

After you do the same open Libreoffice and you can see your font being displayed, which means installation is done.

For example here I am installing fonts (a barcode font) in my laptop:

root@sanvi:/usr/share/fonts# cp /backups/YDD/
barcode_black_blue.odt  barcode.odt             Kuchu_selected/         YDD_strips.pdf          Y_square.png            
barcode_font.zip        grid.png                YDD_strips.odt          Y.png                   Y.svg                   
root@sanvi:/usr/share/fonts# cp /backups/YDD/barcode_font.zip .
root@sanvi:/usr/share/fonts# unzip barcode_font.zip 
Archive:  barcode_font.zip
  inflating: BarcodeFont.ttf         
  inflating: anke-art-README-english.txt  
  inflating: anke-art-README-deutsch.txt  
root@sanvi:/usr/share/fonts# ls
anke-art-README-deutsch.txt  anke-art-README-english.txt  BarcodeFont.ttf  barcode_font.zip  cmap  truetype  type1  X11
root@sanvi:/usr/share/fonts# mkdir barcode_font
root@sanvi:/usr/share/fonts# mv anke-art-README-* ./barcode_font/.
root@sanvi:/usr/share/fonts# mv BarcodeFont.ttf ./barcode_font/.
root@sanvi:/usr/share/fonts# ls
barcode_font  barcode_font.zip  cmap  truetype  type1  X11
root@sanvi:/usr/share/fonts#

You can search and download fonts via any of these websites:
[http://www.1001freefonts.com/](http://www.1001freefonts.com/)
[http://www.dafont.com/](http://www.dafont.com/)

May be you are missing the font due to file corruption or something.
Anyway you can install with the steps above.

cheers, Kiran

---

### Post by Andy_Crowd on 2014-08-11
I downloaded a lot of fonts, which included *helvetica* in the name but still I cannot find this specific font. I used all needed commands mkfontdir, mkfontscale, fc-cache.
I need find this font or another _*mount dockapp*_ for WindowMaker that will work.

---

### Post by buzzingrobot on 2014-08-11
"fc-match helvetica" will tell you if your system is mapping Helvetica to another font.  WM is pretty old code, though, so I wonder if it's aware of the typical Linux font stack these days.

(Good luck with WM.  I got nostalgic a few weeks ago and built a 14.04 system using it.  Sadly, it ignored everything Ubuntu does to polish font rendering, and GKT apps weren't handled well, so the experiment didn't last very long.)

---

### Post by Andy_Crowd on 2014-08-11
It found only: *Helvetica-Compressed.otf: "Helvetica Compressed" "Regular"*

---

### Post by Andy_Crowd on 2014-08-12
I had to reloging to windowmaker for updating of enviroment settings.  
And font settings could be changed in those files for wmmount:
~/.wmmount
/etc/system.wmmount

---

### Post by buzzingrobot on 2014-08-12
I seem to remember that WmakerPrefs has a panel that displays the font paths WM uses and allows them to be edited, removed, or added.

---

