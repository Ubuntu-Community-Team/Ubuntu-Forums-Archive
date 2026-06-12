---
title: "Grub rescue mode after upgrading to 14.04"
date: 2014-04-26
forum: General Help
---

### Post by lhalliwell on 2014-04-26
I upgraded to 14.04 and now grub goes into rescue mode, saying 'grub_term_highlight_color' not found.

The really bad thing is I get this error even with a live usb inserted or when trying to enter the BIOS settings menu.  So it seems like I am stuck trying to boot from rescue mode.

I followed the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

set prefix=(hd1,3)/boot/grub
set root=(hd1,3)
insmod linux
linux /vmlinuz root=/dev/sdb3 ro
initrd /initrd.img

And this last step fails with 'error: no such partition'.

At this point I'm unsure what to try next ...

---

### Post by oldfred on 2014-04-26
Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

You may have to chroot or use Supergrub to boot to get into install so you can run the fix.


 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by pa-card on 2014-04-29
Same here with Xubuntu and Windows 7. Other machines without W7 have had no such an issue. After reading a lot of stuff, I came to this very simple solution following these instructions to re-install grub from a live usb:

[https://sites.google.com/site/easylinuxtipsproject/grub](https://sites.google.com/site/easylinuxtipsproject/grub)

All the partitions are visible, including W7

---

### Post by MikeCyber on 2014-04-29
I've fixed something alike using:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by betterhands on 2014-05-01
> **pa-card said:**
> Same here with Xubuntu and Windows 7. Other machines without W7 have had no such an issue. After reading a lot of stuff, I came to this very simple solution following these instructions to re-install grub from a live usb:

[https://sites.google.com/site/easylinuxtipsproject/grub](https://sites.google.com/site/easylinuxtipsproject/grub)

All the partitions are visible, including W7

i had this problem as well.  thanks for the post.

---

