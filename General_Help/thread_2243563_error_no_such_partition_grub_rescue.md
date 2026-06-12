---
title: "error: no such partition grub rescue"
date: 2014-09-09
forum: General Help
---

### Post by Jacqueline_Scarbor on 2014-09-09
I have a black screen, with the below message:
error: no such partition grub rescue

The screen won't allow me to do anything else, I'm not sure if I connected to the internet or anything. How can I reset to factory setting, or how can I just come out of this screen.  If I turn the netbook off, it starts up to the same error message.   Please help me.

---

### Post by oldfred on 2014-09-09
Is this a BIOS or UEFI install?

You may be able to manually boot or use Boot-Repair to reinstall grub or perhaps use Supergrub to boot.

       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)


 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
With Boot-Repair, it can run a detailed report of your install so we can review your configuration. Best to post link and have us review it. While Boot-Repair usually works occasionally it can make things more difficult.

If a BIOS install:

 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

OR if configfile does not work, again use partition you installed Ubuntu into:

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

      
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

