---
title: "Screenshot Pre-set"
date: 2012-12-20
forum: General Help
---

### Post by oaxacamatt1 on 2012-12-20
Hi all,
I find that I am constantly taking screenshots and then cropping them with GIMP, etc.  How can I change the default program which Screenshot 'goes' to when I open up a screenshot.  

In other words I would like to have this pull down menu be selected to GIMP by default. 

I tried looking in /user/ and /usr but too much junk.  
Any suggestions,
M

PS I have looked over the XFCE website and find nothing yet...

---

### Post by Merrattic on 2012-12-20
Look for: file:///usr/share/xfce4/doc/C/xfce4-screenshooter.html

It shows you the command line options (as a minimum you need "-o" with "-w" or "-f"), you can then edit the keybindings so it works as you want when you press PRTSC

I learnt something too :)

so
```
xfce4-screenshooter -f -o gimp
``` in the keyboard shortcut opens gimp with the screenshot without any need for interaction with the screenshot dialog.

Even better might be ```
xfce4-screenshooter -r -o gimp
``` which allows you select a region to grab before opening up directly in gimp

I guess a backup shortcut is needed for those occasions when you don't want to do this (CTRL+PRTSC will do it) ;)

---

### Post by oaxacamatt1 on 2012-12-20
Very nice, 
Thanks I like it.  BTW, Admittedly I didnt do an exhustive serach but how did you find that info.
Cheers

---

### Post by Merrattic on 2012-12-21
IIRC I simply did a search on the /usr directory for "xfce4-shooter", and found the html file :). Sometimes the program name is not what you might expect it to be.....

---

