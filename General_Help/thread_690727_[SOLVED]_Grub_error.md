---
title: "[SOLVED] Grub error"
date: 2008-02-07
forum: General Help
---

### Post by upthelum on 2008-02-07
I get error 22 on boot, grub doesn't make it to step 1. Does anyone know how to repair this? I cant boot into windows either now. I set up xp pro and ubuntu. Please help....

---

### Post by overdrank on 2008-02-07
> **upthelum said:**
> I get error 22 on boot, grub doesn't make it to step 1. Does anyone know how to repair this? I cant boot into windows either now. I set up xp pro and ubuntu. Please help....

HI  you may try and install the grub again
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Supertof on 2008-02-07
Well you can, boot for the CD, and start the terminal, go to the grub folder of the hard drive and do a grub-install hd0

or this : [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Quintium on 2008-02-07
I also have issues after the latest updates.

I have Ubuntu 7.10 on an external USB drive and WinXP on my internal Hard drive. GRUB loads and display the boot options like it always have. If I select windows I'm able to boot just find. But for the Ubuntu option I get "Error 2: Bad file or Directory type".

If I do "find /boot/grub/stage1", "find /boot/grub/stage2", or "find /boot/grub/menu.lst"  it display (hd0,0)

But if I do "find /boot/grub/vmlinuz-2.6.22-14-generic" the floopy drive makes a noise and I get "Error 15: File not found?"

I tried to boot from Live CD but unable to start up since my new graphic card (which worked fine on my installed version before the update) just suddenly make loud beeping sounds and the Live CD never boots (even tho I did get the start Ubuntu loading graphic at the beginning)

But at one time during "safe graphic mode" from Live CD I was able to get to a command prompt and mount the HD (/dev/sda3) and look in the /boot folder. The file mentioned above does exist with a date of when I applied the update and a bck file of the old version.

Here is the GRUB boot option:

root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=310a1846-fdfb-4520-b329-57fc16e48ea5 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

(sorry for any typos and grammar - not native English :) )

---

### Post by upthelum on 2008-02-07
Thanks guys, i fixed it through winblows recovery console.

---

