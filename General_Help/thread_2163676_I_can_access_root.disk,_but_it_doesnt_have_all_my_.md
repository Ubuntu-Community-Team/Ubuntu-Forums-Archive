---
title: "I can access root.disk, but it doesnt have all my files [+Damaged]"
date: 2013-07-19
forum: General Help
---

### Post by rehcarlos on 2013-07-19
Hello everyone,

I have a notebook with Wubi running on Windows 7.

Everything was working fine, until yesterday when I was trying to install Doxygen in Ubuntu 12.10, the pc kinda of stuck in the installation, so I turned it off abruptely.

Now, I can't access Ubuntu because it gets stuck in the puple loading screen. When I try recovery mode it says a bunch of erros and stucks in (initramfs).

I already tried chdsk /f /r in Windows, but still nothing.

So, I download Ext2Read and opened my root.disk file to get my files, and that worked partially, because there are some important folders missing :/

I think that after my abrupt shutdown a lot of the Ubuntu files are missing. Is there any way to recover them? 

I really would appreciate some help,
rehcarlos.

---

### Post by oldfred on 2013-07-19
Never force shutdown as that almost always corrupts something. 
I do not know nor use wubi, but have some links. 
You probably also need fsck on root.disk which is like chkdsk except for Linux formatted partitions.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You will need to have a live flash drive or DVD version of Ubuntu. Probably best if same version as you have installed.

 [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

      
 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

