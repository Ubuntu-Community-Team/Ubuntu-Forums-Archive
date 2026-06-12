---
title: "/bin/sh : can't acess tty/job control turned off || HELP !"
date: 2007-03-13
forum: General Help
---

### Post by Ephemeral on 2007-03-13
Hello !
I am runninb dual boot Windows XP - Kubuntu 6.10, but this morning on boot I got this error :
```
/bin/sh : can't access tty; job control turned off
(initramfs) _
```

And something about a BusyBox v1.3 Debian.

Can someone please help me fix this ?

---

### Post by T27M on 2007-03-13
I have the same problem with ubuntu, i cant get it installed because of this, ive looked at other threads and havent found a fix 

someone please help

---

### Post by raja on 2007-03-13
This problem (or a similar one) has been discussed a lot of these forums. Maybe you would get some idea from those. You can try [this]("http://www.ubuntuforums.org/showthread.php?t=292533&highlight=job+control+turned+off") for a start.

---

### Post by T27M on 2007-03-14
I've been looking for a while and what i make off it and in this case everyone seems to have ubuntu,kubutu whatever installed then make a hardware change or move things around then something goes wrong (this problem happens) but im still trying to install it from the live cd
maybe i've missed something, ill carry on looking

thanks



EDIT: I coudnt find much help on the forums so i had a play around my self, i disconnected one my dvd drive so i only had a cd-rw drive and that fixed the problem inalled fine

hope this helps

---

### Post by silvanoh722 on 2007-03-20
hi all, i had same problem.

the cause was probably an apt-get autoremove.

try to install the sysvinit package, entering on root disk system from a live cd. 
then mount /dev/sda1 (or where you have root filesystem) on /somedir

#sudo mount -rw /dev/sda1 /somedir
#sudo chroot /somedir

#sudo apt-get install sysvinit

---

### Post by Ephemeral on 2007-03-22
> **silvanoh722 said:**
> hi all, i had same problem.

the cause was probably an apt-get autoremove.

try to install the sysvinit package, entering on root disk system from a live cd. 
then mount /dev/sda1 (or where you have root filesystem) on /somedir

#sudo mount -rw /dev/sda1 /somedir
#sudo chroot /somedir

#sudo apt-get install sysvinit
I'll try it, but don't I need Internet access for that ? (I am on wireless and need to install a load of stuff for Internet to work :P )

---

### Post by silvanoh722 on 2007-03-22
#sudo apt-crom add

this add a cdrom repository at your sources.list then a internet connection is not necessary

---

### Post by Ephemeral on 2007-03-23
```
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# sudo apt-get install sysvinit
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdb4.2++c2 libdb3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  initscripts
The following NEW packages will be installed:
  initscripts sysvinit
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 150kB of archives.
After unpacking 635kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://fr.archive.ubuntu.com dapper/main initscripts 2.86.ds1-6ubuntu32
  Temporary failure resolving 'fr.archive.ubuntu.com'
Err http://fr.archive.ubuntu.com dapper/main sysvinit 2.86.ds1-6ubuntu32
  Temporary failure resolving 'fr.archive.ubuntu.com'
Failed to fetch http://fr.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.86.ds1-6ubuntu32_i386.deb  Temporary failure resolving 'fr.archive.ubuntu.com'
Failed to fetch http://fr.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysvinit_2.86.ds1-6ubuntu32_i386.deb  Temporary failure resolving 'fr.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

This is what I got, but when I tried :
sudo apt-crom add
It said to insert a disc when there was already one.
Is there a way yo manually add the dcrom repositorie ?

---

### Post by Ephemeral on 2007-03-23
Still get the same thing, but it seems I can't really mount the cdrom, because it is already mounted : it is being used to acctually boot

---

### Post by Ephemeral on 2007-03-23
I download the sysvinit pack from the actual package site
How can I install it on the partition : /dev/sda3 instead of on the live CD ?

---

### Post by silas_irl on 2007-03-23
> **Ephemeral said:**
> I download the sysvinit pack from the actual package site
How can I install it on the partition : /dev/sda3 instead of on the live CD ?When your in Ubuntu in the LiveCD go into a terminal and mount /dev/sda3:
> sudo mkdir /mnt/sda3
sudo mount /dev/sda3 /mnt/sda3

You can then cd to /mnt/sda3 and install it.  You may need to execute chroot to tell the system that /mnt/sda3 is the new temporary /.

> #
sudo chroot /mnt/sda3 /bin/bash
# / now points to /mnt/sda3, install the package, and when you are finished press CTRL+D to
# go backto the old / location

cd /
sudo umount /dev/sda3

Have you fully tried all the grub related fixes?  If not, I'd recommend you try them first.

---

### Post by Ephemeral on 2007-03-23
bumpzzzzzz

---

### Post by Ephemeral on 2007-03-23
How do I run the .deb ? (For example, I put it in /dev/sda3)

---

### Post by Ephemeral on 2007-03-24
Bump
********

---

### Post by Ephemeral on 2007-03-24
Bump (a doo da bop...)

---

### Post by nitsthenazgul on 2007-03-25
> **silvanoh722 said:**
> hi all, i had same problem.

the cause was probably an apt-get autoremove.

try to install the sysvinit package, entering on root disk system from a live cd. 
then mount /dev/sda1 (or where you have root filesystem) on /somedir

#sudo mount -rw /dev/sda1 /somedir
#sudo chroot /somedir

#sudo apt-get install sysvinit


please i am newbie 
i am not able to understand wht u said
i am facing the same problem

---

### Post by wgw on 2007-03-25
Thanks for the tip: worked like a charm for me. I had indeed removed sysvinit etc. So I was really stuck. Now up and running again.

---

### Post by wpshooter on 2007-03-25
I do NOT believe that the **root** cause of the error (subject of this post) has anything to do with all of the information given in all of the replies BECAUSE I have received this error message when installing Ubuntu on a hard drive which I had JUST completely **WIPED** clean (i.e. there was ZERO, absolutlely nothing on the drive) and I got this error when booting to the Ubuntu installation CD.

This is something that someone in the development of this O/S needs to look at.  I have reported this as a bug.  I hope they can get to the **ROOT cause** of this problem.

Thanks.

---

