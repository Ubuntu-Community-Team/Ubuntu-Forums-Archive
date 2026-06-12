---
title: "How to uninstall Grub from the main hard drive?"
date: 2007-08-12
forum: General Help
---

### Post by Oligator on 2007-08-12
Hi,

I am a beginner on forums in general and I think I misplaced my questions...
I put it originally at the end of a thread:
SUCCESS - Dapper Drake loaded on external USB drive! [taken from DaBruGo Breezy post]
Sorry...

So, here are the original question and my further comments:

Hi,

I am running in a problem related to this thread I believe.
I have installed Ubuntu 7.04 on a usb-drive plugged to my laptop without realizing that the Grub would be installed on my main hard drive containing XP. Now, I cannot start XP without having my usb-drive connected which is kind of annoying.
Is anyone who could help me to relocate the Grub on my usb-drive?
Being new to linux, a pretty detailed procedure would be a great help.

Thanks to anyone replying.


ok, I think I can give more information.
I think my problem come from the bios... When my usb-drive with Ubuntu is not connected, I have the messages: Grub loading stage1.5
Grub loading, please wait
Error 21

This error is related to "21 : Selected disk does not exist
This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.". This info comes from [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Well I am still stuck with my problem...

I think I am getting more info.

I understand that the real problem is that the Grub is installed on the MBR of the internal hard drive. The only way to solve my problem would be to uninstall it from it and to put it on my usb drive...

Would anyone know how to do that?

Thanks


Sorry again and thanks for any reply

---

### Post by confused57 on 2007-08-12
Download a copy of the Super Grub Disk:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
there are several ways listed in the above link to restore your internal hard drive's mbr, but SGD is probably the easiest.

You can use the Ubuntu live cd(or SGD) to install grub's IPL to the external hd's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
you would need to "setup (hd1)", using the above guide

Then boot first to your external drive, if you get a grub boot menu, hghlight your Ubuntu entry, press "e" to edit, then highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot...x means leave this value as it is...this change is temporary, but you can make it permanent in your /boot/grub/menu.lst.

---

### Post by Oligator on 2007-08-13
Thanks a lot for the quick reply!
As soon as I have time to take care of it, I will let you know if I managed to make it work.

---

### Post by Oligator on 2007-08-13
ok, I solved the problem. I used a copy of Super Grub Disk on CD and rebbooted my computer with it without my ubuntu drive connected. I repaired the MBR with windows option. After I restarted my laptop without any problem.
Same thing with my usb drive. Very easy.

Thanks again

---

### Post by confused57 on 2007-08-13
Glad you were able to get your system repaired...yes, Super Grub Disk is pretty amazing.

---

