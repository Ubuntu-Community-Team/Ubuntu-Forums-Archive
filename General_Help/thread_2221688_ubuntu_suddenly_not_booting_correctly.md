---
title: "ubuntu suddenly not booting correctly"
date: 2014-05-03
forum: General Help
---

### Post by linuxgrrl on 2014-05-03
Help!!
My ubuntu box (12.04 LTS) is suddenly not booting correctly. While the normal text bootup messages are scrolling by, it stops/freezes ... the last message to display is that apache server is loading (but I don't think Apache is the problem, it's just the last message).
If I jump to another terminal, I can log in and do normal commands like df and top, so I think (?) the system is booting to some point, but never makes it to the graphical login screen.

dmesg had nothing that looked helpful. I ran "startx" from a terminal and checked the X log file ... nothing obvious seemed to be happening, although at the end of the file it unloaded the modules and had a "giveup" shut-down message but did not say why.

Just prior to this, my system became unresponsive and I was forced to do a hard-reset.  This is my first attempt to boot since the hard re-set. I hope I did not kill my system.

Thanks!!!

---

### Post by ajgreeny on 2014-05-03
Maybe a system check with fsck will sort out the problem; it is worth trying anyway, so from your command line login run command ```
sudo touch /forcefsck
``` and reboot, which will force a file system check as it boots up.

You could also use a live system to run fsck on your root partition; just boot to live system, DVD or USB, and run command ```
sudo e2fsck /dev/sdx#
``` where **sdx#** is your root partition, eg probably **sda1** if only ubuntu is on the disk.

---

### Post by linuxgrrl on 2014-05-03
thanks. I ran an apt-get update, then tried running gdm manually and it actually worked! Next time the keyboard does not respond, i will try to remember to SSH in from elsewhere to fix.

---

### Post by oldfred on 2014-05-03
Do not force shutdown without remembering the Elephants.

 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by linuxgrrl on 2014-05-03
sweet. 
I wonder if it works with my RFID keyboard. 
Hopefully i won't need it again for awhile, but now I know!

---

