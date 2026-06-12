---
title: "grub screen resolution"
date: 2007-09-30
forum: General Help
---

### Post by gubemton on 2007-09-30
Hi, I would like to know how can I change the screen resolution *of* grub. Currently when I'm in grub, I can see nothing (my monitor is a samsung syncmaster 941mp). With different monitors it work.

Thanks

---

### Post by kellemes on 2007-09-30
Look here for hints..

[http://ubuntuforums.org/showthread.php?t=258484&highlight=grub+resolution]("http://ubuntuforums.org/showthread.php?t=258484&highlight=grub+resolution")

---

### Post by gubemton on 2007-09-30
I've not found the solution... I should have to install the graphical version of grub....  this is just too dangerous.

---

### Post by kellemes on 2007-09-30
This is about the Grub bootmenu itself right? Not the console?
Well, I've searched a bit and to be honest.. I can't find anything useful.. did you check your BIOS? Often you can set some sort of default resolution, maybe you need to change it to get this monitor going..

---

### Post by gubemton on 2007-09-30
In fact it is the resolution of grub itself, I also searched a lot in google.... I didn't find a thing.

I had so much entusiasm about linux... The last time I used it was 3 years ago... Now still it seems not to be ready yet.

Another thing that I miss, and without it it is impossible to work, is ULTRAEDIT!!! In linux there is no such thing as ultraedit, for example no column mode (exept for gedit, which has not got the column mode I need, and gvim, which is far too much complicated).

I heard that Russia is adopting open source in the schools, I hope that they will be able to spread the linux adoption.

---

### Post by kellemes on 2007-09-30
> **gubemton said:**
> In fact it is the resolution of grub itself, I also searched a lot in google.... I didn't find a thing.

I had so much entusiasm about linux... The last time I used it was 3 years ago... Now still it seems not to be ready yet.

Another thing that I miss, and without it it is impossible to work, is ULTRAEDIT!!! In linux there is no such thing as ultraedit, for example no column mode (exept for gedit, which has not got the column mode I need, and gvim, which is far too much complicated).

I heard that Russia is adopting open source in the schools, I hope that they will be able to spread the linux adoption.

You can always use one of the many other bootloaders, like LILO.
There are a gazillion editors for GNU/Linux and for me vim is the best.. but I understand it's difficult for others.
You can also look at gedit, kate, cream (vi the easy way), slickedit (not free), emacs, pico, mousepad, scribes. I would especially look at Kate and Gedit (part of Ubuntu).

---

### Post by Izobalax on 2007-09-30
I believe this is a program called Start-up Manager, in either gnome-apps.org or kde-apps.org. It allows you to select your GRUB graphic as well as the resolution, provided the GRUB graphic you select supports that resolution. 

Google it and check it out. 

/izo

---

### Post by kellemes on 2007-09-30
Well, that's a fine tip.
Didn't know this existed.

---

### Post by Izobalax on 2007-09-30
> **kellemes said:**
> Well, that's a fine tip.
Didn't know this existed.
Heh, no worries. Do be warned though, for SOME people it has affected how their system boots up. 

In other words, use at your own risk. 

/izo

---

### Post by BUGabundo on 2007-10-01
install hwinfo:
#sudo apt-get install hwinfo

then run it :
#sudo hwinfo --framebuffer

see the resolution you want, and it vga code.

edit grub menu:
#sudo gedit /boot/grub/menu.lst 

look for:
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=verbose splash

and add the code, to the end of the line:
# defoptions=verbose splash vga=0x0360


the run:
#sudo update-grub

good luck

---

### Post by gubemton on 2007-10-03
Thank you everybody to have spent time to resolve my grub problem.

Have a nice day! :)

---

