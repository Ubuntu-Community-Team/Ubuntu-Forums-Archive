---
title: "Black screen"
date: 2014-09-28
forum: General Help
---

### Post by dkreisst on 2014-09-28
I've just installed 14.04 Trusty Tahr.  I downloaded and installed it from the older version.  It did fine until it tried to shut down and restart at the end.  It showed the system 76 page, ran some text, then went black.  Please help.

---

### Post by mörgæs on 2014-09-29
Please begin with a complete hardware description, especially the graphics processor.

---

### Post by dkreisst on 2014-09-29
The computer I have is a lemur ultrathin from System 76.  I bought it around 2010.  I'm not sure of the graphics processor.  I've looked at the System 76 page, and they no longer sell the computer.  Their only information refers to a wiki page: [http://knowledge76.com/index.php/Category:Lemur](http://knowledge76.com/index.php/Category:Lemur), which has no information about graphics processors.  I can give the product code, if that helps.

---

### Post by Dana_Carter on 2014-09-29
I ran into a similar issue when I upgraded.
With me it was a resolution issue.  The system was booting but not giving me a screen.  I was able to ssh in and mess around with the Grub settings, which proved to be the culprit.
If you can't ssh, you can hit the shift key during boot to get to the grub menu and choose recovery mode. then 
```
mount -rw -o remount /
```
then you can edit grub.
```
sudo nano /etc/default/grub
```
Then edit the following lines to read as follows:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset grub_gfxmode=1280x1024x24 video=795"
GRUB_GFXMODE=1280x1024x24
GRUB_GFXPAYLOAD_LINUX=keep
```
You can change the line:
```
GRUB_GFXPAYLOAD_LINUX=keep
```
to
```
GRUB_GFXPAYLOAD_LINUX=text
```
If you want to disable graphical boot and do a textual boot.
Then run
```
sudo update-grub
```

I'm not saying that this will definitely work for your situation, but seeing as how it seems to be what I ran into......

---

### Post by dkreisst on 2014-09-29
Thank you.  I don't know what the Grub settings are.  I did try hitting shift while loading.  It flashed a few lines containing the word "error" and then went to the black screen, so I'm not sure how to get to the shell.  I also noticed that there was a note on the first screen to hit f2 to get to system utilities.  This works, but I don't know what to do from there.

I'm not sure the system is loading at all, as the black screen comes very quickly.  After that there are no sounds from the computer that would equate to loading the system.

---

### Post by Dana_Carter on 2014-09-29
The F2 is probably for your bios settings.
Try holding the shift key immediately after you start the computer and see if this brings up the grub menu.

---

### Post by dkreisst on 2014-09-29
It flashes "GRUB Loading", then four or five "error file not found", then goes to a black screen.  It happens very quickly.  If I don't hold down shift it just flashes the error messages.

---

### Post by Dana_Carter on 2014-09-29
Well if you can't get to grub to go to recovery mode, and you can't ssh in you could always try the boot repair disk
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

good luck

---

### Post by dkreisst on 2014-09-29
Thank you.  I put the 64bit download on a usb and rebooted the computer with usb in.  It does the same thing while pressing shift and not pressing shift.  Any other ideas?  Did I do the reboot wrong?

---

### Post by Dana_Carter on 2014-09-29
there's more to it than that.
firstly to boot from the usb, you have to set the bios to choose it first in the boot order, but I digress.
you should be able to start the computer and immediately hold down the shift key and keep it pressed, eventually the grub menu should show up.
If you can't get that far your options are
1) use the boot repair boot disk I referred to earlier
2) boot to an install disk and use recovery mode
3) reinstall

I wish I could be of more help to you.
but I will keep checking in.

---

### Post by dkreisst on 2014-09-30
Thank you so much for all the information.  I'll work on it.

---

### Post by dkreisst on 2014-10-05
Holding the shift key down does nothing different, except state "GRUB Loading" before the error:file not found messages appear and the computer goes blank.

I finally found a cd and burned the 64 bit download onto it.  I shut down my computer and restarted it with the disc in the drive and the same thing happened.  Do I have to change the bios to get the computer to recognize the disc in the beginning?  If so, what parts do I change?

Thank you for any help.

---

### Post by dkreisst on 2014-10-15
I booted with the recovery disc and it was able to boot ubuntu 14.04.  It was not able to connect to wi-fi, and, later, was not able to find any wi-fi.  Is there a way to check if this can be solved?

---

### Post by dkreisst on 2014-10-15
Nevermind, it found it after shutting down and starting again.

---

