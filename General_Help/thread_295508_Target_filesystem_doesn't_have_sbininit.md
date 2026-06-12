---
title: "Target filesystem doesn't have sbin/init"
date: 2006-11-08
forum: General Help
---

### Post by AdamWarlock on 2006-11-08
Hey all,

I just finished a clean install of Kubuntu Dapper 6.06 LTS and upgraded to Edgy 6.10. I set up all my programs and settings and rebooted the system.

This is what appeared on the screen:

[B][I]Target filesystem doesn't have sbin/init

BusyBox v.1.1.3

/bin/sh: can't access tty; job control turned off

(initramfs)[/I][/B]

As a relatively new Kubuntu user, could someone offer me some help in fixing this issue? Any help would be appreciated.

Thanks!

---

### Post by AdamWarlock on 2006-11-08
Quick BUMP. My comp is unusable in this situation.

---

### Post by Ramses de Norre on 2006-11-08
Boot a live cd, mount your / at for example /media/root, then do
```
sudo chroot /media/root
sudo aptitude reinstall ubuntu-minimal
```
Show us what that says.

---

### Post by AdamWarlock on 2006-11-08
I SO appreciate the help! 

Can I get some quick instructions on how to mount root in a different location?

---

### Post by qalimas on 2006-11-08
```
mkdir ~/Desktop/harddrive
sudo mount -rw /dev/hda1 ~/Desktop/harddrive
sudo chroot ~/Desktop/harddrive
sudo aptitude reinstall ubuntu-minimal
```

Assuming, of course, /dev/hda1 is the root of your hard drive.  To unmount and try different numebrs in case that doesnt work, teh command is:```
umount /dev/hda1
```and so on.

Hope this helps :)

---

### Post by glyphobet on 2006-11-10
I encountered a similar program after the official upgrade process crashed mid-upgrade on an unmodified 6.06 installation. 

Booting from an old Ubunutu Live CD (4.04), I was able to mount my root partition, chroot to it, and then this fixed the problem:

aptitute reinstall ubuntu-minimal 

It appears that the official upgrade process hadn't gotten around to installing upstart.

Thanks for the tip.

It should also be noted that a forum reporting a similar problem suggested that you check /boot/grub/menu.lst points to the correct boot partition -- on my system the  upgrade process had overwritten /dev/hda1 with a big long string of garbage.

---

### Post by rubberglove on 2006-11-24
Thanks for that - I woke up this morning to the same problem (quite a nasty surprise before my coffee!), and that fixed it. 

I'm not sure what caused it for me, as I haven't recently updated anything special, but I did notice that the power went out for a few minutes last night...

---

### Post by Eman64 on 2006-12-05
Hey guys,
I've done everything up to the sudo chroot ~/Desktop/root(that's what I named the folder) because whenever I try to use the code it says
```
sudo chroot ~/Desktop/root
chroot: cannot run command '/bin/bash': No such file or directory
```
So can anyone tell me what I did wrong? Everything worked fine up until just this command...

---

### Post by Yuzem on 2006-12-18
Hello, i followed the instructions but i can't access internet to install ubuntu-minimal.
What can i do?
Can i download it from somewhere?
I am dual booting and i can access my Linux partition from XP.

---

### Post by QOLIM on 2006-12-21
I got the same promlem as Eman

and when I mount my hd and open it in nautilus
then all i can see is files form 0bytes without extentions.
even all the folders are files like that, like bin, but when i seect the mounted folder and see the properties it says siwe 70 used:24 like it sould
but when i select all these files and properties it says 0 bytes.

so when i try chroot it returns: cannot run command `/bin/bash': Permission denied

Can anyone help me with this please, i dont want to lose all my data

---

### Post by QOLIM on 2006-12-21
update: i can see everything fine when i run 'gksudo nautilus'

so what file do i need to edit  to change the permissions, so i can startup normal again

---

### Post by Yuzem on 2006-12-21
> **Yuzem said:**
> Hello, i followed the instructions but i can't access internet to install ubuntu-minimal.
What can i do?
Can i download it from somewhere?
I am dual booting and i can access my Linux partition from XP.

I have found the answer and now my problem is solved:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by SanHolo on 2007-01-11
For chroot to work, you need to specify a shell, too. So, it should look like this:

```
sudo chroot ~/Desktop/root /bin/bash
```

I'm stuck with no internet-connection, too (damn proxy), shouldn't it be possible to do the ubuntu-minimal install from CD?

---

### Post by larsv on 2007-02-15
Just a short notice: If your *root file system* is **anything other than hda1**, please check your menu.lst in /boot/grub/ after updates, especially updates to the kernel. An update to our system changed all references from hda3 to hda1 and then the box of course refused to boot properly after that (dapper).

---

### Post by Ramses de Norre on 2007-02-15
> **SanHolo said:**
> For chroot to work, you need to specify a shell, too. So, it should look like this:

```
sudo chroot ~/Desktop/root /bin/bash
```

I'm stuck with no internet-connection, too (damn proxy), shouldn't it be possible to do the ubuntu-minimal install from CD?

Works from cd too, use apt-cdrom add to add it to your sources if you removed it.

---

### Post by reillyse on 2007-03-28
aptitude reinstall kubuntu-minimal 
worked for me on Kubuntu 
something to do with sysvinit be uninstalled or something.. that was one annoying bug

---

### Post by Eladon on 2007-03-29
I have the same issue after a fresh install of Edgy Server.  I tried doing the reinstall of ubuntu-minimal, but it didn't seem to actually reinstall anything.  Is there something different I should be using for the server edition?

---

### Post by punong_bisyonaryo on 2007-04-17
When I run reinstall ubuntu-minimal, I get this error message:
```
debconf: Perl may be unconfigured (Can't locate strict.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at (eval 1) line 2.
BEGIN failed--compilation aborted at (eval 1) line 2.
) -- aborting
```

What does it all mean and how do I solve it?

---

### Post by soundwave on 2007-05-04
don't work =( 

```

mkdir ~/Desktop/harddrive
sudo mount -rw /dev/hda1 ~/Desktop/harddrive
sudo chroot ~/Desktop/harddrive
sudo aptitude reinstall ubuntu-minimal
```

i reboot the machine and not happen nothing, and error follow there

---

### Post by sully311 on 2007-06-12
ran into this problem updating from 6.10 to 7.04, sorry to say this did not work for me as well. tried from 6.0.6 live disk then downloaded 7.04, everything seemed to install, but same results.

went ahead & installed from 7.04 disk, must say was really impressed with the new options while installing, in particular the abilty to access all other drives and partitions... fantastic!

since this fixed/corrected several problems, think i, will re-install all other PC's this way...:D

thanks to everyones efforts for making & taking open source software where it is. :KS

---

### Post by zarathustra on 2007-06-26
I am getting this exact same problem with the latest stable kernel I've tried compiling.

---

### Post by PA28 on 2007-07-04
I've joined the Ubuntu forums just to say a huge thank you for the above hints. I had problems with my "initscripts" package and tried to remove it and install it again. Dumb move. =(

Using the directions posted on the first page I was able to use the Ubuntu Feisty Live CD, mount my existing hard drive, and use apt-get to reinstall the ubuntu-minimal package (which also installed the "initscripts" package). Everything now works just the way it used to!

Again, a huge thanks to you guys.

PA28

---

### Post by flickerfly on 2007-07-29
What can I do if I can't boot off a CD or USB to correct this? Am I going to have to remove the HD and put it into another computer to reinstall init?

---

### Post by The-Wappy-One on 2007-09-01
Hi there i wonder if some one could help on this matter i've followed it to the letter and im getting different errors to most.

Here it is 

```

ubuntu@ubuntu:~$ mkdir ~/Desktop/harddrive
ubuntu@ubuntu:~$ sudo mount -rw /dev/sda1 ~/Desktop/harddrive
ubuntu@ubuntu:~$ sudo chroot ~/Desktop/harddrive
/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

ubuntu@ubuntu:~$ sudo chroot ~/Desktop/harddrive
/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

ubuntu@ubuntu:~$ sudo chroot ~/Desktop/harddrive /bin/bash
/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory


```

Could any one please help, It would be greatly appreciated?

Thanks

Wappy

---

### Post by The-Wappy-One on 2007-09-01
I've tried all i can and the past 3 hours searching the forum with no luck can ANY one please help?

i keep getting as above

/bin/bash: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

What am i doing wrong

i've booted from a ubuntu live cd and also a ubuntu ultimate 1.4 dvd all with the same effect!

Please help 

Wappy

---

### Post by allorder on 2007-09-13
I got same error when I want to execute regnum game; ./game: error while loading shared libraries: libncurses.so.5: cannot open shared object file: No such file or directory

I have installed every library with synaptic, what wrong ?  :confused: :(

allorder@ubuntu:~/Desktop/live$ ls -l /usr/lib/libncurse*
-rw-r--r-- 1 root root  694518 2007-03-05 16:13 /usr/lib/libncurses.a
-rw-r--r-- 1 root root  169898 2007-03-05 16:13 /usr/lib/libncurses++.a
-rw-r--r-- 1 root root 2992582 2007-03-05 16:12 /usr/lib/libncurses_g.a
-rw-r--r-- 1 root root  605706 2007-03-05 16:12 /usr/lib/libncurses++_g.a
lrwxrwxrwx 1 root root      20 2007-09-13 17:09 /usr/lib/libncurses.so -> /lib/libncurses.so.5
lrwxrwxrwx 1 root root      13 2007-09-13 17:48 /usr/lib/libncurses.so.5 -> libtermcap.so
-rw-r--r-- 1 root root  169898 2007-03-05 16:13 /usr/lib/libncurses++w.a
-rw-r--r-- 1 root root  785462 2007-03-05 16:13 /usr/lib/libncursesw.a
-rw-r--r-- 1 root root  605754 2007-03-05 16:12 /usr/lib/libncurses++w_g.a
-rw-r--r-- 1 root root 3402896 2007-03-05 16:12 /usr/lib/libncursesw_g.a
lrwxrwxrwx 1 root root      21 2007-09-13 17:09 /usr/lib/libncursesw.so -> /lib/libncursesw.so.5

---

### Post by AxAeo on 2008-02-25
You know I've had this problem and looking at the solutions in this thread, I've kind of run into some issues. Mostly the fact that Aptitude and Apt-get won't install the ubuntu-minimal package. Regardless of what I do, like entering "apt-cdrom add" it still attempts to download the packages from the internet, which I don't have access to while using the live cd. Any advice? I tried to download the packages, but it has a million dependancies that dpkg reports not having when I try.

---

