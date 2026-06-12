---
title: "Cannot Open image file '*.jpg,*.png,*.bmp'"
date: 2015-08-31
forum: General Help
---

### Post by abdillah2 on 2015-08-31
hi anyone ):P

i got this problem ... my default image viewer is gone then i istall eog  ( Eye of gnome )
but still cannot open any image file like '*.jpg,*.png,*.bmp'

in example i try to open survey.png
for make you sure this is image i show this 

> 
root@hasnydes:/home/abdilahrf/Documents/CTF/asis# file survey.png 
survey.png: PNG image data, 508 x 466, 8-bit/color RGB, non-interlaced

root@hasnydes:/home/abdilahrf/Documents/CTF/asis# exiftool survey.png 
ExifTool Version Number         : 8.60
File Name                       : survey.png
Directory                       : .
File Size                       : 100 kB
File Modification Date/Time     : 2015:05:11 07:33:52+07:00
File Permissions                : rw-r--r--
File Type                       : PNG
MIME Type                       : image/png
Image Width                     : 508
Image Height                    : 466
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Significant Bits                : 8 8 8
Software                        : gnome-screenshot
Image Size                      : 508x466


but when i try to open the image file always happen error 
" **File type PNG image (image/png) is not supported** "
or 
" [B]Could not load image 'survey.png'. 
Unrecognized image file format[/B]
 "

can someone help me to figure this out , Thanks :)

---

### Post by flaymond on 2015-08-31
What is your default image viewer? Maybe you removed the depends for those formats.

---

### Post by ajgreeny on 2015-08-31
What version of Ubuntu are you using?

Is it 12.04, Precise, as the version of exiftool you have, 8.6, is quite a bit behind mine in Xubuntu 14.04, which is 9.46?

Can you open the images in any other image viewer application, such as gimp, gthumb, mirage, gpicview, etc etc?  There are plenty of them which you could try, though it would be good to know why eog is not working for you.

What is the output of ```
eog /home/abdilahrf/Documents/CTF/asis/survey.png
```
I note you were using those previous commands you showed in a root terminal; why was that?

---

