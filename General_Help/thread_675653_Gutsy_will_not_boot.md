---
title: "Gutsy will not boot"
date: 2008-01-22
forum: General Help
---

### Post by CaptainTux on 2008-01-22
Hi, 

This is not my machine, but a machine of one of my students that is currently sitting on my kitchen table (the machine, not the student).  
It is a Compaq Presario V3000, AMD Turion 64, nVidia graphics.

I installed Gutsy on it for her about 3 months ago and everything has been going swimmingly.

I do not know how often she was doing upgrades or what she has added through synaptic.  

Here is what it is currently doing.

I boot, it goes to grub, then gives the splash screen for a moment, then goes blank and comes up with the following.

> BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built in commands.
(initramfs)

When it goes to grub, if I choose escape it gives me the following options...
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+

I have googled about for some solutions and it has been suggested I can edit one of these lines to get into the system, but it was not made clear what to edit...either through poor communication or my ignorance.

Please advise or ask further diagnostic questions as needed.

Cheers

PS Installed 32 bit version of Gutsy, not 64 bit.

---

### Post by rosegarden78 on 2008-01-22
How'd that happen?  Sound like fresh install is needed.

---

### Post by CaptainTux on 2008-01-22
> **rosegarden78 said:**
> How'd that happen? 
Wish I knew.  The last thing she installed was Amarok and the last thing she was doing was copying files to a thumb drive.  She's a sweet kid and I am really hoping to avoid doing a fresh install.

---

### Post by CaptainTux on 2008-01-23
Based on some advice I received on a mail list to better identify the issue, I removed the "quiet splash" from  /boot/grub/menu.lst making it look like this:


/boot/vmlinuz-2.6.22-14-generic root=/dev/uuid ro

I am not really sure what to look for, but these were some lines of potential concern I found towards the end.

[6.552000] EXT3-fs error (device sda1) ext3_check_descriptors: Block bitmap for group 384 not in group (block 33188 )!
[6.552000] EXT3-fs: group descriptors corrupted!
mount:   Mounting /dev/disk/by-uuid/8754c3d3-a451-4609-8dcf-0d2f1ae097a6 on /root
failed: Invalid argument

a few lines down I get
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount:  Mounting /sys on /root/sys failed: No such file or directory
mount:  Mounting  /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Thoughts?

---

