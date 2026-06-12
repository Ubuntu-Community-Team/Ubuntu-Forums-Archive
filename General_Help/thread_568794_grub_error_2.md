---
title: "grub error 2"
date: 2007-10-06
forum: General Help
---

### Post by eyeleica on 2007-10-06
Last night after burning an iso cd on my edgy eft system, the system froze.  Nothing I could do to get it working or to shut it down properly worked.  Finally, I had to power the machine off by holding down the on/off button for 10 seconds.
Upon trying to start the system, I get a Grub 2 error.

Any suggestions on fixing the grub error so the system will boot and run?

Thanks,
eyeleica

---

### Post by SpiritIsReality on 2007-10-06
howdy pard
see error 2 here
[http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage2-errors)
what I'd recommend is try to reinstall grub with the live cd here
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
If that works, great. If not I'd try fsck ing the ubuntu partition again with the use of the live cd, so that the ubuntu partition is not mounted when you run fsck. the partition being fsck 'd is not supposed to be mounted.then reinstall grub to mbr with the live cd
I can go thru it step by step if you like, I mean we can try what I said and see if it gets you BackInTheSaddle again.I mean YouAreInTheSaddle already, aren't you.
post back 
buds

---

### Post by eyeleica on 2007-10-06
I tried both suggestions, plus super grub iso.  When I tried using the live cd and attempting
to find grub, the response was no file found.
When I attempted to fsck the hard drive, I was completely unsuccessful.  I kept getting the message that the partition had errors in it and I needed to go back and fix the errors before proceeding, but I was not able to go back and fix errors.  

If you have the time, I'd appreciate any direction in trying to install grub.  I'm sure the power shut down corrupted many files.

thanks

eyeleica

---

### Post by SpiritIsReality on 2007-10-06
howdy
well if the files are corrupted, then there's only the fsck that'll fix them that I know of. There's lots better around this forum than me, and if you want to repost to get their attention at any time please do.
in order to install grub, we have to
so do you want to try to install grub? I've never used the super grub but I've run grub from a hard drive partition, it's too bad you don't have more than one linux installed, cause then you can run fsck from one partition, like debian or small or
puppylinux or kubuntu, and make sure they're not all mounted at boot, or the power failure would corrupt the whole dang lot.
there's a emergency shutdown attempt page around somewhere too. for the next time, but I've run into times when with my limited knowledge, I couldn't get to a virtual terminal, ctrl-alt-F2 or anything. to get it to reboot properly. 

ok so grub 2 error. maybe nothing got installed? or you need to run dpkg-reconfigure xserver-xorg to fix your video so you can see the screen?

maybe the reason grub is complaining is that your install didn't finish?

---

### Post by SpiritIsReality on 2007-10-06
OK
if you weren't able to install with the live cd, first thing to do is see if you can install with a alternate cd.[http://releases.ubuntu.com/7.04/](http://releases.ubuntu.com/7.04/) It won't have the trouble of finding your video card like the live cd does. 

for trying the live cd once more,
Pumalite recommended to someone a few days ago, I saw, but I can't quote him,  
when booting with the live cd, try to boot with a vesa driver and a refresh rate you know your monitor can handle. or try 600x800.
I'm not real good at pickin the F#'s but I can find out if you have to.
buds

---

### Post by SpiritIsReality on 2007-10-06
ok you burnt an iso. were you going to install 7.10? or ?
is it ok to go ahead with that plan now? we can use knoppix to copy files off the hd to a disk if you want to save some things before reformatting?
sorry about my lack of skill.
buds

---

### Post by SpiritIsReality on 2007-10-06
> **eyeleica said:**
> I tried both suggestions, plus super grub iso.  When I tried using the live cd and attempting
to find grub, the response was no file found.
When I attempted to fsck the hard drive, I was completely unsuccessful.  I kept getting the message that the partition had errors in it and I needed to go back and fix the errors before proceeding, but I was not able to go back and fix errors.  

If you have the time, I'd appreciate any direction in trying to install grub.  I'm sure the power shut down corrupted many files.

thanks

eyeleicawhatever you figure we should do, we'll try to do. amen

---

### Post by SpiritIsReality on 2007-10-07
howdy
in P235 signature, is/was this link on how to reboot only if all else fails
[http://ubuntuforums.org/showthread.php?t=315404](http://ubuntuforums.org/showthread.php?t=315404)

buds

---

### Post by eyeleica on 2007-10-08
I tried installing grub again as suggested above with no success.  I downloaded Knoppix live cd and tried it.  my hard disk shows up but I'm unable to mount it to transfer files to a flash drive or write to a cd.  The message I get when trying to mount is a bad superblock, wrong fs, bad option on /dev/hda1, missing codepage or other error.  
Lesson learned:   don't power off the machine by holding down on/off button for 10 seconds........results might be terminal.

thanks for all the help

---

### Post by SpiritIsReality on 2007-10-10
This message won't show up till the administrators check it out and make sure I'm not ... ? but here goes anyway.
run live cd
log in
terminal
sudo fdisk -fp /dev/partition your ubuntu is on.
repeat until no error messages.
the ubuntu partition should not b mounted when you run fsck on it, and if you just log in with the live cd, it won't be mounted, so you are safe.

see aboutdebian.com installing etch. click on find in this page, in box at bottom, type in fsck, click next if have to. talks about fsck -fp ...and also fixing badblocks.:guitar::-({|=:lolflag:

---

### Post by SpiritIsReality on 2007-10-11
howdy
sorry I didn't get back to you sooner. was in Jail.
I've had this rig lose power a number of times due to lightning strikes, power pole collisions, and also have hard shutdown the linux os, when it freezes up , ... sometimes an fsck is needed, sometimes not, and other times ... well it's reinstall time for me, others may know how to get around it. 
trails
buds

---

