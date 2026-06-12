---
title: "GRUB re-installation method doesn't seem to work..."
date: 2007-06-23
forum: General Help
---

### Post by Miki01 on 2007-06-23
Hey everyone, its been a while since I've posted on the forums.

I've recently upgraded from 6.06 to 7.04.

The installation went fine until the Ubuntu installer messed with my Windows partition and somehow deleted the .dll file that Windows uses to communicate with my computer's hardware (that's not good ;)). At the time, GRUB was working fine, can boot into Fiesty with no problems, but WinXP just had the no-boot issue. So taking what I've learnt from cooperative-ed at a computer store, I stick my WinXP disc in the drive and repair it with chkdsk. All is well with XP.

But I noticed something when booting into Windows XP... GRUB isn't showing up! I noticed that when I went looking for Ubuntu on the boot menu!

So I boot up Fiesty's live CD and go on google (since I'd have to reboot if I just googled while in XP).

I've found the "sudo -i, find /boot/grub/stage1, root (hd0,x), setup (hd0)" method.

I've read on Ubuntu's resident wiki that it's better to run "setup (hd0,x)" instead of "setup (hd0)", since it installs GRUB in Ubuntu's partition, rather than the master boot record.

I tried it both ways and NONE have worked...

Here's what I got for each:

"setup (hd0,x)"

> ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0,5)
setup (hd0,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 12: Invalid device requested
grub> quit
quit

and running "setup (hd0)"

> ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 12: Invalid device requested
grub> quit
quit

What seems to be the problem? My Ubuntu partition is taking up quite a bit of space on this small 80GB HDD I'm using, so I'd like to be able to make use of it.

Would anyone know how to fix this?

Thanks in advance for your replies, it is greatly appreciated!

---

### Post by angryhomer17 on 2007-06-23
I had a similar problem: [http://ubuntuforums.org/showthread.php?t=415344](http://ubuntuforums.org/showthread.php?t=415344)

I needed to use my computer right away so I just had to reinstall ubuntu, but later on someone suggested that I couldn't boot to grub because it wasn't located within the first 1024k of the disk. (I think that has something to do with "base" memory and "extended" memory from the DOS era. Assuming you are using the bios supplied with the mobo.) 

If you can't get grub to work and you still want to keep windows, I would suggest backing up all your ubuntu files, removing the ubuntu partiton (gparted), and reinstalling. I think that would do they same things as installing windows and then installing ubuntu (though you'll have windows already installed)

---

