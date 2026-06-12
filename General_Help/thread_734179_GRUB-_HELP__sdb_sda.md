---
title: "GRUB- HELP  sdb sda"
date: 2008-03-24
forum: General Help
---

### Post by oligray on 2008-03-24
Ok. heres my situation, im 16 i live in a house where i have a laptop ( wont booot live cds :(... ) and the family has a desktop. So i install gutsy gibbon to an external harddrive from the desktop pc. was excited as i now had ubuntu. However i did have a few errors in the install and a fair few when i ran it.

I unplugged my ext hdd and when i rebooted the computer it tired to load GRUB and failed so windows cant load any more ( did i mention linux would be my preffered choice but my dad refuses anything but windows and that is why im sitting here typing this) I can still load windows if i have the hdd plugged in but otherwise i cant.

Is Grub saved somewhere on the internal drive and can i move it to my external so grub is only there when my external is plugged in.

GRUB is my primary problem so could you answer that question more urgently than the fact live cds fail to boot on my laptop, they kinda get half way and freeze

HOW DO I SOLVE THIS GRUB PROBLEM

1) GRUB PROBLEM
2) BOOTING LIVE CD WITH MY LAPTOP
3)WHY DO I GET SOO MANY ERRORS ( possibly something to do with dpfg-- or simmilar file name)

---

### Post by oligray on 2008-03-24
please help im fed up with computers for the day.... and will go off now please can someone leave some sort of response by the morning

---

### Post by fsmithred on 2008-03-24
It sounds like the problem is that grub is installed in the MBR of the internal drive, but the grub config file is on the external drive. Without the external drive, grub doesn't know what to do. I can think of at least a couple of solutions.

1. Teach your dad how to use the grub command line, and he can boot manually each time. This is the least desirable solution.

2. Make a small boot partition on the internal drive to hold your linux kernel and grub files. Lots of steps involved in this with a chance of hosing the windows installation.

3. Make a grub boot floppy ('grub-install /dev/fd0' will do it when you're running linux)
    and restore the mbr on the internal drive (boot windows cd, go to recovery console, and run 'fixmbr')  If you don't have a floppy drive, it's possible to make a grub boot cd.

4. Restore the mbr and edit the windows bootloader to give you the choice to boot linux. 
[http://ubuntuforums.org/showthread.php?t=732173&highlight=grub+usb+external+drive](http://ubuntuforums.org/showthread.php?t=732173&highlight=grub+usb+external+drive)

5.Install grub to the mbr of the external drive (grub-install /dev/sdb), restore windows to the mbr of the internal drive, and follow the directions for adding usb support to initrd, then set the bios to boot from usb before internal drive, and it'll boot linux when your external drive is plugged in.
[http://ubuntuforums.org/showthread.php?t=678146&highlight=grub+usb+external+drive](http://ubuntuforums.org/showthread.php?t=678146&highlight=grub+usb+external+drive)
(This is probably the best solution.)

---

### Post by oligray on 2008-03-24
i will do the 5th option tomorrow

that sounds like the best option. in basic terms is all im doing is removing the grub from internal to external

---

### Post by oligray on 2008-03-24
ok i read the option 5 bit.. and might reinstall and follow those instructions at another time.. however on the grub removal bit. it says for xp and has a link i could not find the link there for this. and his does not include how to put it onto the external..

sorry tht im a bit of a n00b and if im making stuff hard for you

. im actually really interested in linux and this bad experiecne has not put me off one bit. and in a few years i want to be able to contribute to ubuntu or another distro in my spare time. 

and as for the laptop situation after doing more searching i found a thread that said to someone else who sounded like they had same problem ... to try out fedora. so that is solved and my final problem i think will just be solved. when i update gutsy to hardy heron.

---

### Post by oligray on 2008-03-25
thanks i did that and saved the desktop.

now i think i will use my laptop only for linux distros

---

### Post by fsmithred on 2008-03-25
For option 5, putting grub on the external drive, if you can boot into linux on the external drive, you can start with step 9 or 10 (use sudo if you don't use su). You don't need to re-install. I don't know if you'll need to do step 13, changing (hd1,0) and (hd0,1). And you may need to set the bios to boot from usb first. That should be all. (Note: I've never done this myself, but I'd bet a dollar that it works.)

---

### Post by oligray on 2008-03-25
doesnt matter now i took it off.lol

i want to get a linux that works on my laptop and so far the only live cd that works is fedora 8 KDE and i want GNOME and the wireless wont work.. 

if you can help me with this theres a thread here..  [http://ubuntuforums.org/showthread.php?t=734896]("http://ubuntuforums.org/showthread.php?t=734896")

---

