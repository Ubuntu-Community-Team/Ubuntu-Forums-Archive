---
title: "how to copy xorg.conf from live cd to hd and is it wise ?"
date: 2007-10-09
forum: General Help
---

### Post by doron387 on 2007-10-09
booting from live cd works well
booting from hd freezes
my conclusion (being a noob) : xorg.conf in the installation should be changed to the one which works .

question 1 : i am not deeo enough into all the details in the xorg.conf, are there some settings that are using the live cd in it and if i boot the installation w/ this xorg.conf it might get stuck again, this time for other reason ?
question 2 : how to : check _where_ is my installed xorg.conf (sda5 or sda6)
                  how to : copy xorg.conf _from live cd_ over the installed one ?
i will understand what the commands say but i can not yet build up all the syntax.

pllllease help, for the last 4 days i havn't seen the ubuntu screen even once as it freezes all the times.
thanks a lot

---

### Post by fjgaude on 2007-10-09
Just do it... and let us know what happens.

I can't see anything wrong with do it, shouldn't hurt anything, but do make a backup of the xorg.conf that is on the hard drive.

The file is in /etc/X11/xorg.conf. You can find it using file manager (Nautilus) on the liveCD. I think the live CD will mount the drive and partitions in /media off your home directory using "file system".

---

### Post by doron387 on 2007-10-09
would love to do it if i knew how to :

i am currently on live cd session,
i typed in terminal : 
ubuntu@ubuntu:~$ locate xorg.conf
locate: warning: database /var/lib/slocate/slocate.db' is more than 8 days old
/var/lib/x11/xorg.conf.md5sum
/var/lib/x11/xorg.conf.roster
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/xresprobe/xorg.conf
/etc/X11/xorg.conf

all these files are in the cd, right ?

how do i check where xorg.conf in the hard disk (i know it should be in partition #5 or #6,
how to check it, how to get to it, what is the line that i should type to make thae backup and to make the copy, i am complete noob

---

### Post by fjgaude on 2007-10-09
Wait, I'll have to run a liveCD and see how to mount the hard drive partitions. I can't recall from memory.

---

### Post by fjgaude on 2007-10-09
Well, it seems the partitions are auto mounted in Nautilus file manager, shows them on the left side of the window.

From the menu, click on Places... oh God, you are using KDE and not Gnome.

I can't help you, really, if the liveCD doesn't auto mount the partitions. Sorry.

Okay, I am trusting you are using Gnome. Click Places and then Home Folder. From there click on a Volume on the left side of the window. Then an icon shows on the desktop; click on both Volumes, one after the other. You should have two disk icons on the desktop now. Click on one and then on /etc and then go down the icons and find X11. There you will see xorg.conf.

Use gedit to copy the xorg.conf from the liveCD /etc/X11/xorg.conf to the hard drive xorg.conf overwriting the latter. Make a backup of it before overwriting it. Can you do all this?

---

### Post by doron387 on 2007-10-09
first of all thanks for your efforts,
second, gnome and kde are not that different from this point of view, it should be basic.
the problem is that i havn't figure yet what mount / unmount mean so it makes my life more difficult but i am sure that there is a command to check the in the partitions in the hard drive ehich files exist there.
and much easier should be copy a file from one place to the other, i just don't find the exact orders.
please think of it again.
thnx

---

### Post by fjgaude on 2007-10-09
Okay, you mount a device to a mount point.

A device is called /dev/sda[123456]. You have sda5 and sda6 of concern, eh? Yes.

So while in the liveCD at the command line from a terminal enter:

sudo mount /dev/sda5 /media
sudo mount /dev/sda6 /media

The mount point is /media.

I believe that should now permit you to use your file manger to find the xorg.conf file in X11. One of the two partitions will have it.

Using your file manger you can simply drag and drop the xorg file from the liveCD to the partition that has the xorg file there.

So much to learn when thing are not going right, eh?

---

### Post by doron387 on 2007-10-09
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media
ubuntu@ubuntu:~$ ls
Desktop
ubuntu@ubuntu:~$ sudo mount /dev/sda5
mount: /dev/sda5 already mounted or /media busy
mount: according to mtab, /dev/sda5 is already mounted on /media
ubuntu@ubuntu:~$ sudo cd  /dev/sda5
sudo: cd: command not found
ubuntu@ubuntu:~$  cd  /dev/sda5
bash: cd: /dev/sda5: Not a directory
ubuntu@ubuntu:~$ sudo cd  /dev/sda5/media
sudo: cd: command not found
ubuntu@ubuntu:~$

- how do i look for the file ? shouldn't ls give me a list of files ?
- what is the command that i should use ?
- i like to learn but since i installed kubuntu i havn't seen the desktop once (quit frusrating), but a command that i use will not be forgotten never.

waiting 4 rply

---

### Post by fjgaude on 2007-10-09
You have to move to where the partition is mounted. In Ubuntu it is usually in /media. So try:

```
cd /media/sda5
```

Your file manager should show all the partitions that are mounted and where.

---

### Post by PmDematagoda on 2007-10-09
Yes, but you are looking at the wrong command, you need to use something like:-
```

cd media/volume
```

But it would be easier for you if you used Nautilus for that. Just find the media folder in the root of the Linux volume and you will see every device connected to your computer, mounted or unmounted, from there I trust you know what to do?

---

### Post by doron387 on 2007-10-09
've been already tryin' some commands but yoq !!!
the is the I/O :

ubuntu@ubuntu:~$ cd /media/sda5
bash: cd: /media/sda5: No such file or directory
ubuntu@ubuntu:~$ cd /sdag/media
bash: cd: /sdag/media: No such file or directory
ubuntu@ubuntu:~$ cd /sda5/media
bash: cd: /sda5/media: No such file or directory
ubuntu@ubuntu:~$ sudo cd /sda5
sudo: cd: command not found
ubuntu@ubuntu:~$ sudo cd /sda5/media
sudo: cd: command not found
ubuntu@ubuntu:~$

what can it be done ? how should i find the right command/guide ? (i was already looking at some but i can't find

---

### Post by doron387 on 2007-10-09
hey, i found this part of a thread :

[B]2. Copy the /etc/X11/xorg.conf from the LiveCD to your harddrive, replacing the broken one.
 
Code:
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming /dev/hda1 is where Ubuntu, /, is located.)
sudo cp /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
sudo umount /mnt/ubuntu[/B]

can you figure out what i can use from these commands ?

---

### Post by PmDematagoda on 2007-10-09
So go through your file manager, either it's Nautilus, Konqueror or Thunar. It is easier that way.

---

### Post by fjgaude on 2007-10-09
> **doron387 said:**
> hey, i found this part of a thread :

[B]2. Copy the /etc/X11/xorg.conf from the LiveCD to your harddrive, replacing the broken one.
 
Code:
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming /dev/hda1 is where Ubuntu, /, is located.)
sudo cp /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
sudo umount /mnt/ubuntu[/B]

can you figure out what i can use from these commands ?

Look, the partitions are already mounted but we don't know where. So, can't you use your file manager to find where? The cp command can be used as shown above but we have to know where the partition is mounted.

---

### Post by doron387 on 2007-10-09
well, thanks i'll try another thread with more accurate questions

---

### Post by doron387 on 2007-10-09
ok,
now i read another thread that said to type : sudo fdisk -l
and this is the output : (i think it helps us)

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7369    59191461    7  HPFS/NTFS
/dev/sda2            8645        9598     7662973+   c  W95 FAT32 (LBA)
/dev/sda3            9599        9729     1052226   d7  Unknown
/dev/sda4            7370        8644    10241437+   5  Extended
/dev/sda5   *        7370        8584     9759456   83  Linux
/dev/sda6            8585        8644      481918+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

let's go on, please.

---

### Post by fjgaude on 2007-10-09
Okay we know the sda5 will be the one that has the xorg.conf file, but we still have to find where it is mounted.

Do you have a file manger active on the liveCD? Yes, and it is at Places/Home Folder. Can you tell us what happens?

Just thought, do simply mount at command line and it shows all devices and their mount points. Let us see the results.

---

### Post by doron387 on 2007-10-09
output ;

[B]ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /media type ext3 (rw)
ubuntu@ubuntu:~$ [/B]                 

i don't see what we are looking for in this output, do you ?
i don't know what a file manager should do.
if i change to ubuntu live cd will it be easier 4 you to guide me ? (should take 5 minutes)

---

### Post by fjgaude on 2007-10-09
We now know that /dev/sda5 is mounted on /media just where is should be.

Where are you now? On what system?

In order to copy the xorg.conf file from the liveCD to /etc/X11/xorg.conf on sda5 you will have to be on the Ubuntu liveCD, yes.

You have to learn what a file manager is all about. The command line is one way but new users usually take to a file manager to get around. Try it from Places/Home Folder.

---

### Post by doron387 on 2007-10-09
now i am working with live cd of kubuntu.
is file manager a window that shows all the folders and their relations ? if so then i don't see in it the sda at all.

i do see ' / '
under it : been
              boot 
           + cdrom
           + dev
           + etc
           + home


and a lot more.
do you mean this ai the file manager ?

if the answer is YES then give me tthe possible route to look for.

---

### Post by PmDematagoda on 2007-10-09
Yes it is the file manager.

Now tell us what you see listed on the left hand side of that file manager.

---

### Post by fjgaude on 2007-10-09
Oh, boy! I don't know KDE, but you are close with the list you show. Try go-ng to home. But first, are you in something called Konqueror?

And now at the command line do another mount and show what you get.

---

### Post by forestpixie on 2007-10-09
yes this is the right place

in /etc/X11 should be the xorg.conf file which I assume the live cd is using to work

in that window under /media is where you should look for the partition which is your installed ubuntu - in that partition will be another /etc/X11/xorg.conf - this is the one you have problems with

does that make sense

PS don't start another thread for the same thing - everyone will get really confused

---

### Post by por100pre1 on 2007-10-09
Can you try this in Ubuntu install?

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and select vesa.

```
sudo reboot
```

---

### Post by doron387 on 2007-10-09
wow guys this is confusing.....(my response to all the files)

i see /etc/X11/xserver
 and the problem is that when i open ' media' it kind of recursive, i mean i see under media again /home and the rest....

any clue ? maybe run a search ? (i am trying it now while this message is on the way)

---

### Post by PmDematagoda on 2007-10-09
Ok, now tell us what flavour of Ubuntu you have, be it Ubuntu, Kubuntu or Xubuntu.

---

### Post by doron387 on 2007-10-09
> **por100pre1 said:**
> Can you try this in Ubuntu install?

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and select vesa.

```
sudo reboot
``` \


1. my installation is Kubuntu (but it should not matter regards these commands (as far as i understand).
2. the commands that u wrote mean to make backup of xorg.conf that is on the installation and then reconfigure it by changing the 'nv' to vesa. am i right untill here ?
when i had a glimpse into the live cd's xorg.conf (that works fine w/ my machine) the resolution was 1200X800 which suits my machine and in during the xserver configuration this option do not exist, so i am quite sure that there are other settings that will work better if i just copy the live cd version of xorg.conf - am i wrong ?
now, here are the files that i found with the help of the file manager :

file:///etc/X11/xorg.conf
file:///media/etc/X11/xorg.conf
file:///rofs/usr/share/xresprobe/xorg.conf
file:///usr/share/xresprobe/xorg.conf

well, it seems that we are close to the end ... what shall i do now ? (in terms of exact commands)

---

### Post by fjgaude on 2007-10-09
Well, when you changed to vesa then the option of 1280x1024 went away.

Just do it. Copy the liveCD xorg.conf to your sda5 partition.

```
sudo cp /etc/X11/xorg.conf /media/etc/X11/xorg.conf
```

Or open two file manager and drag the file from the liveCD to the /media/etc/X11 folder.

I'm still confused at where you were before you went to the liveCD? on what computer?

Gosh, this has been tough.

---

### Post by doron387 on 2007-10-09
hey you sweet people, i was working all this time from my laptop, booted from live cd, after this idea of copying the content of the file, i have just copied it, things are so easy when you know how to do it, isn't it ?
well, i am logging out and trying to boot from the installation, answer will come soon.

---

### Post by doron387 on 2007-10-09
i did learn how to copy / edit / browse but i still can't boot to my newly installed dualbooting kubuntu.
it boot perfectly from live cd
it freezes after the first progress bar.
if somebody knows something about this problem in hp pavilion dv 6102 please help is needed.

---

### Post by strabes on 2007-10-09
Why won't you simply hit CTRL+ALT+F1 when it freezes and run the commands that por100pre1 wrote? Once you get a working X server then you can worry about installing drivers.

---

### Post by fjgaude on 2007-10-09
At least we now know that the xorg.conf file from a liveCD will not work on a hard drive.

Surely we have a video board issue here and a way to start to fix it is to do as suggested by por100pre1, at a command prompt.

---

