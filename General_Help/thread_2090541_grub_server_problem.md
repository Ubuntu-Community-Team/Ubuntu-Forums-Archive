---
title: "grub server problem"
date: 2012-12-02
forum: General Help
---

### Post by l3ecl on 2012-12-02
I have 3 partitions on my computer.
1. Ubuntu Server 1
2. Windows XP 
3. Ubuntu Server 2

I deleted Ubuntu Server 1 and now when I boot up, there is no more grub2 menu. Instead I get a grub rescue.

I tried re installing grub on Ubuntu Server 2 using this tutorial:
[http://opensource-sidh.blogspot.com/2011/05/install-grub-in-ubuntu-from-server-cd.html](http://opensource-sidh.blogspot.com/2011/05/install-grub-in-ubuntu-from-server-cd.html)
I got to the last part when it generates a grub.cfg. I thought that solved the problem but when I reboot, I get back the grub rescue

How do I get my grub menu back and boot normally?

---

### Post by kc1di on 2012-12-02
you can download and run boot-repair it may fix the problem for you.
you can get it [here]("https://help.ubuntu.com/community/Boot-Repair") with instructions.

---

### Post by oldfred on 2012-12-03
I also suggest Boot-Repair as    	kc1di did.

Some others:
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
    
Sometimes you can just manually boot:
       Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

    
       Manual boot:
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command. If grub.cfg is good this just may work:
configfile (hd0,1)/boot/grub/grub.cfg


OR:

   set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

---

