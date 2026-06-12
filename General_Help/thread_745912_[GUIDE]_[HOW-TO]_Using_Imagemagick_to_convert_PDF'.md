---
title: "[GUIDE] [HOW-TO] Using Imagemagick to convert PDF's to JPEG's (succesfully done!!!)"
date: 2008-04-05
forum: General Help
---

### Post by s3a on 2008-04-05
Using Imagemagick to convert PDF's to JPEG's (succesfully done!!!)

1) Type "sudo apt-get install imagemagick" in the terminal
2) Create a folder called "temp" on the desktop
3) Place the pdf you want to convert in the temp folder
4) Type "cd ~/Desktop/temp/" in the terminal
5) Type "convert -units PixelsPerInch -density 150x150 **J5**.pdf **J5**.jpg"

1st		**J5**=name of PDF file
2nd		**J5**=name of the JPEG file
(all of this done in a folder called "**temp**" on the desktop)



I have been going through hell trying to get this to work. I don't know if I am stupid or whatever may be the reason, here is what I wrote for others having such a problem. If the PDF file has multiple pages, each page will be automatically saved as a different JPEG file! You will need an internet connection in order to use the first terminal command. Do not actually type the quotes "". If you have any questions...ask! Some tried to help me on other threads I've made. And, many have attempted to help me on irc channels and therefore I don't have a reputable name of theirs to give, however, borris.morris (from Ubuntu's Forums) solved this for me and it is thanks to him that this guide exists. If I don't respond after a long period of time, private message me.

---

