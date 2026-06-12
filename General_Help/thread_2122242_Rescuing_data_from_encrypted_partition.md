---
title: "Rescuing data from encrypted partition"
date: 2013-03-04
forum: General Help
---

### Post by zesterer on 2013-03-04
Hi there,

Sorry to be rushed. I have a very important piece of work on my linux partition that I NEED access to veyr soon, and I can't get to it. I have posted this in general help because its not just one problem.

Ok, yesterday I managed to f*** up Ubuntu. I tried to uninstall lightdm and install slim. Something didnt work, and now I cant access Ubuntu because whenever I press Ctrl+Alt+F2 on startup screen (the one with the 5 dots that go from white to orange), it almost instantly switches back to the startup screen. If I could access the command "startx", I would.

My question is this: Can I access this stuff from Windows? With time short, I switched back to my Windows partition to 'get the job done'. I am having withdraw symptoms already.

Another way to get my work would be to access my home folder from Windows. I installed Ext2Msg or whatever its called, and can access my linux partition. HOWEVER. And this is the big HOWEVER. I chose to encrypt my linux partition when I install Ubuntu, and obviously the data I can get from Windows is useless. I do know the password for the encrypted partiton however. Are there any ways/tools that will gain me access to it that work on Windows?

I you can solve or help me solve either or these problems, I would be immensely grateful!

Thanks,

Barry Smith (Zesterer)

---

### Post by cbraxton on 2013-03-04
You can boot off of a Linux live CD (or flash drive) to access the files on your system.  To do so from Windows would require you to install a program that can read your Linux partition, such as ext2read which can read ext2/3/4 filesystems:

  [http://sourceforge.net/projects/ext2read/files/](http://sourceforge.net/projects/ext2read/files/)

---

### Post by zesterer on 2013-03-04
So this would allow me to read an encrypted partiton?

Thanks so much for they help, you guys are life savers!

Barry Smith

---

### Post by cbraxton on 2013-03-04
Not from Windows, I'm not sure if there's anything for Windows that can read a Linux encrypted partition. But you should be OK with a recent Linux Live CD, you can use the Disk Utility to unlock the partition and mount it, same as you would do with an encrypted removable drive.

---

### Post by zesterer on 2013-03-04
Grrr... This problem is very persistant. Can anyone help with actually fixing Ubuntu? It seems like it doesnt like Slim... Can I install lightdm again from windows by editing system files or something?
[SIZE=5][B]
Please help, this is really urgent![/B][/SIZE]

---

### Post by oldfred on 2013-03-04
When a system is broken you can often chroot into it. But with encryption you may have to mount partitions differently.

[http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/](http://www.cyberciti.biz/faq/ubuntu-mounting-your-encrypted-home-from-livecd/)

 To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
drs305 chroot to reinstall kernel
[http://ubuntuforums.org/showthread.php?t=1641599](http://ubuntuforums.org/showthread.php?t=1641599)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Then from inside chroot you can reinstall or repair just about anything.
      
 #Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a

   # reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by zesterer on 2013-03-05
Hey, thanks for the reply. Luckily I managed to find a lower-grade backup on one of my cloud drives, but its still annoying. However, I am getting a new computer soon so I will just copy the encrypted data across, use the same username and password as I did with Ubuntu the first time, and hope it decrypts properly.

Btw: Does this working with Linux mint too? I am planning to switch to linux mint, but staying fairly close to Ubuntu...

Thanks,

Barry Smith

---

### Post by black veils on 2013-03-06
your whole access problem was just that you installed slim display manager?

1. boot the computer, pressing and holding the Shift key to enter the grub boot loader and choose recovery option

2. then in the following menu choose network to mount the drive with write permissions. then choose drop to root shell from menu again.

3. ```
sudo dpkg-reconfigure lightdm
``` and follow instructions to choose lightdm as the display manager again, or whatever you had before slim.

if there is no option, then you need to ```
sudo apt-get install lightdm
```instead, and hope that fixes it.

4. exit to the menu, i think by pressing Esc key, then choose boot as usual from menu.

you should now be able to login as you would normally.

you can get your data from a live disc regardless of this though. i dont know if you have an lvm encryption or just encrypted home, the methods for data retrieval are different.

---

