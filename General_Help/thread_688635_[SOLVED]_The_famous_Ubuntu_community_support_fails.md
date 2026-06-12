---
title: "[SOLVED] The famous Ubuntu community support fails: Automount broken, nobody can help"
date: 2008-02-05
forum: General Help
---

### Post by tbraun on 2008-02-05
Hello!

I have had so many wonderful experiences with the support and help from the Ubuntu community on these forums. I understand that everyone here helps voluntarily, and this is all greatly appreciated.

Occasionally, though, it seems as if there are some problems for which there just is no solution known. Case in point: Automount breaks, and nobody knows how to get it back.

There are multiple threads about this...

[INDENT][COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=686842]("http://ubuntuforums.org/showthread.php?t=686842")[/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=685694]("http://ubuntuforums.org/showthread.php?t=685694")[/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=536715]("http://ubuntuforums.org/showthread.php?t=536715")[/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=683753]("http://ubuntuforums.org/showthread.php?t=683753")[/COLOR][/INDENT]

... but not a single one arrives at a solution.

So now I am wondering: What are the next steps that can be taken? I have had this in the past, where the forums just couldn't help with specific problems. Where do you go from there?

Tom

---

### Post by jaytek13 on 2008-02-05
Nevermind... Maybe you could try the linux forums? There is linuxforums.org and linuxquestions.org.

---

### Post by seventhc on 2008-02-05
you could look under System>Preferences>Sessions and make sure 'Volume Manager' has a check next to it. No it isn't for sound, it's for removable media and drives.
> ....Where do you go from there?more google or paid support ;)

---

### Post by bodhi.zazen on 2008-02-05
> **tbraun said:**
> Hello!

I have had so many wonderful experiences with the support and help from the Ubuntu community on these forums. I understand that everyone here helps voluntarily, and this is all greatly appreciated.

Occasionally, though, it seems as if there are some problems for which there just is no solution known. Case in point: Automount breaks, and nobody knows how to get it back.

There are multiple threads about this...

[INDENT][COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=686842]("http://ubuntuforums.org/showthread.php?t=686842")[/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=685694]("http://ubuntuforums.org/showthread.php?t=685694")[/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=536715]("http://ubuntuforums.org/showthread.php?t=536715")[/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=683753]("http://ubuntuforums.org/showthread.php?t=683753")[/COLOR][/INDENT]

... but not a single one arrives at a solution.

So now I am wondering: What are the next steps that can be taken? I have had this in the past, where the forums just couldn't help with specific problems. Where do you go from there?

Tom

If you find a problem with no solution, next step is to file a bug report (otherwise how do the developers know about it ?).

Bug reports:

	How to : [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

	[https://bugs.launchpad.net/distros/ubuntu/+bugs](https://bugs.launchpad.net/distros/ubuntu/+bugs)

Holds true for any distro.

---

### Post by Bloch on 2008-02-05
Automount has not worked on my FAT32 external usb hard drive for both Feisty and Gutsy. It worked on Dapper Drake.
I've wasted a lot of time trying to fix it. I never entered a bug report, in part because I didn't feel qualified enough, in part because I thought there might be something wrong with the hard drive. (Though it mounts perfectly from the command line)

Now I just use pmount. I have a little script to mount with pmount and launch nautilus - sounds like a neat trick. Except sometimes the hard drive appears as dev/sda1 (on fdisk -l) and sometimes as dev/sdb1
So generally I mount it by hand i.e the command line.

I'll follow this thread with interest.

---

### Post by tbraun on 2008-02-05
Volume manager is checked, so that's not the problem.

---

### Post by bodhi.zazen on 2008-02-05
If you would like help please post additional information.

I just now reviewed the threads you posted, and I am not sure how they apply to you.

One of the threads is marked as solved.

1. What are you trying to mount ?

2. What is the mount point ?

3. Plug in your device / cd and post the output of :

```
sudo fdisk -l

dmesg | tail

mount
```

We also need to look at /etc/fstab . Does the mount point exist ?

@Bloch : I understand what you are saying, +1 pmount ftw.

My point is only that if one would like to see bugs squashed, one needs to start with bug reports.

---

### Post by tbraun on 2008-02-05
Hello!

> **bodhi.zazen said:**
> 
1. What are you trying to mount ?


A CD in my CD drive. It's a laptop, and the CD drive is permanently mounted. The device shows up in Places-->Computer, no matter if I have a CD inserted or not. I can still manually mount the CD from there, if I right click on the CD device and select 'Mount Volume', but no more automounting (appearance of the icon on the desktop and all that).

It used to work perfectly on Feisty. I then upgraded to Gutsy, and now it seems to be broken. Automount of USB devices still works perfectly, and the autofs4 kernel module is loaded.

> **bodhi.zazen said:**
> 
2. What is the mount point ?


It's /media/cdrom0, and the device itself is /dev/scd0

> **bodhi.zazen said:**
> 
3. Plug in your device / cd and post the output of :

```
sudo fdisk -l

dmesg | tail

mount
```


```

backpack:~> sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        2619    20972857+  83  Linux
/dev/sda3            2620        3835     9767520   83  Linux
/dev/sda4            3836       12161    66878595    5  Extended
/dev/sda5            3836        4078     1951866   82  Linux swap / Solaris
/dev/sda6            4079       12161    64926666   83  Linux
backpack:~> dmesg | tail
[  147.940000] eth1: no IPv6 routers present
[  196.896000] UDF-fs: No VRS found
[  196.932000] ISO 9660 Extensions: Microsoft Joliet Level 3
[  196.960000] ISO 9660 Extensions: RRIP_1991A
[  568.896000] loop: module loaded
[  568.960000] device-mapper: ioctl: 4.11.0-ioctl (2006-10-12) initialised: dm-devel@redhat.com
[  569.212000] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[ 1460.008000] UDF-fs: No VRS found
[ 1460.044000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1460.068000] ISO 9660 Extensions: RRIP_1991A
backpack:~> mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda2 on /SHARED type ext3 (rw,user_xattr)
/dev/sda1 on /SHARED_VFAT type vfat (rw,utf8,umask=007,gid=46)
/dev/sda6 on /home type ext3 (rw,user_xattr)
none on /proc/bus/usb type usbfs (rw,devgid=1001,devmode=666)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/mapper/truecrypt0 on /home/jbrendel/SECURE type ext2 (rw,sync,user_xattr)

```

Note that the output of dmesg is a bit older. Nothing new is being printed when I insert a CD.

> **bodhi.zazen said:**
> 
We also need to look at /etc/fstab . Does the mount point exist ?


My fstab is as follows:

```

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=c2d8a779-204c-4034-941e-fceaf9192975 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda7 :
defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda2 :
UUID=dad9dd60-f707-43ed-a991-a30ccb9cb777 /SHARED ext3 defaults,user_xattr 0 2
# Entry for /dev/sda1 :
UUID=07D7-0510 /SHARED_VFAT vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sda6 :
UUID=b528f816-3b2e-410e-ae9f-467f061e9551 /home ext3 defaults,user_xattr 0 2
# Entry for /dev/sda5 :
UUID=c848cfc2-ae09-43e2-b239-dd4696f80ff8 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

none /proc/bus/usb usbfs devgid=1001,devmode=666 0 0

```

I hope this all helps...

---

### Post by bodhi.zazen on 2008-02-05
Not sure if it will help, but try commenting out the line for your CD on fstab (place a # in the front)

> #/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

Then unmount and remove the CD

Then delete the mount point :

```
sudo rm -f /media/cdrom0
```

Then try putting the CD back into the drive.

Also, may I ask, what is on the CD ? Is it a data cd or a music cd ?

---

### Post by tbraun on 2008-02-05
Hello!

Thank you for trying to help me here...

> **bodhi.zazen said:**
> Not sure if it will help, but try commenting out the line for your CD on fstab (place a # in the front)

Then unmount and remove the CD

Then delete the mount point:

```
sudo rm -f /media/cdrom0
```

Then try putting the CD back into the drive.

I did all of that, and it didn't help. In fact, it made things a little bit worse, because now I can't even manually mount the CD anymore (Places-->Computer). I now get a pop-up stating something about illegal characters in the mount point name (which is not even present). Anyway, I re-created the mount points and uncommented the line in fstab again and now at least the manual mount works again.


> **bodhi.zazen said:**
> 
Also, may I ask, what is on the CD ? Is it a data cd or a music cd ?

It's a data CD. In fact, it's a Ubuntu boot CD. But I have tried other CDs with the same (non-)result.

---

### Post by bodhi.zazen on 2008-02-05
Not sure it will help, but try leaving the mount point but commenting out the line in fstab. Sometimes automount fails if there is an entry in fstab.

If that fails we will have to wait for a guru or you can try filing a bug report.

---

### Post by shaggy999 on 2008-02-05
> **tbraun said:**
> Hello!

I have had so many wonderful experiences with the support and help from the Ubuntu community on these forums. I understand that everyone here helps voluntarily, and this is all greatly appreciated.

Occasionally, though, it seems as if there are some problems for which there just is no solution known. Case in point: Automount breaks, and nobody knows how to get it back.

There are multiple threads about this...

[INDENT][COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=686842]("http://ubuntuforums.org/showthread.php?t=686842")[/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=685694]("http://ubuntuforums.org/showthread.php?t=685694")[/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=536715]("http://ubuntuforums.org/showthread.php?t=536715")[/COLOR]
[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=683753]("http://ubuntuforums.org/showthread.php?t=683753")[/COLOR][/INDENT]

... but not a single one arrives at a solution.

So now I am wondering: What are the next steps that can be taken? I have had this in the past, where the forums just couldn't help with specific problems. Where do you go from there?

Tom

You mention that none of those topics comes to a solution. One of those is mine. I solved it and posted the solution. Clearly, you didn't read the whole thread.

---

### Post by seventhc on 2008-02-05
> **shaggy999 said:**
> You mention that none of those topics comes to a solution. One of those is mine. I solved it and posted the solution. Clearly, you didn't read the whole thread.
It isn't marked as solved, so he/she may have possibly not read it all the way through.
I'll post the link here so it isn't hidden by the others. :)
[http://ubuntuforums.org/showthread.php?t=685694](http://ubuntuforums.org/showthread.php?t=685694)

---

### Post by geirha on 2008-02-05
I haven't looked at the threads you linked to yet, but to me it sounds like it's a problem with hal (hardware abstraction layer). Since you can mount your cd manually, there's probably nothing wrong with the cdrom-drive, but hal is the application responsible for telling gnome to mount it. What does this command give? ```
ps -ef | grep hald
``` On my gutsy system it gives several lines, including this:```
108       4681  4489  0 02:08 ?        00:00:00 hald-addon-storage: polling /dev/hdb (every 2 sec)
``` with /dev/hdb being a dvd-drive in my case. I've seen some cases on these forums where people have had troubles with hal after an upgrade from a previous ubuntu release.

---

### Post by seventhc on 2008-02-05
I'm not sure if this might help but if you look in *System>Preferences>Removable Drives and Media* (the storage tab) and see whats checked off. On mine, the first 3 are checked which all somehow relate to auto mounting.

---

### Post by tbraun on 2008-02-05
> **seventhc said:**
> I'm not sure if this might help but if you look in *System>Preferences>Removable Drives and Media* (the storage tab) and see whats checked off. On mine, the first 3 are checked which all somehow relate to auto mounting.

They are all checked...

---

### Post by tbraun on 2008-02-05
> **geirha said:**
> I haven't looked at the threads you linked to yet, but to me it sounds like it's a problem with hal (hardware abstraction layer). Since you can mount your cd manually, there's probably nothing wrong with the cdrom-drive, but hal is the application responsible for telling gnome to mount it. What does this command give? ```
ps -ef | grep hald
``` On my gutsy system it gives several lines, including this:```
108       4681  4489  0 02:08 ?        00:00:00 hald-addon-storage: polling /dev/hdb (every 2 sec)
``` with /dev/hdb being a dvd-drive in my case. I've seen some cases on these forums where people have had troubles with hal after an upgrade from a previous ubuntu release.

Whoa!

Now THAT is interesting: I have a bunch of HAL related lines, but that one (about the addon-storage) is missing! How do I get it back? This really looks like that could be it.

HAL, eh? Funny, just yesterday they had "2001: A space odyssey" on TV here...

---

### Post by seventhc on 2008-02-05
> [**HAL**]("http://www.imdb.com/title/tt0062622/"): I'm sorry Dave, I'm afraid I can't do that.sorry, couldn't resist. :D

---

### Post by false_cognate on 2008-02-05
I am having a similar problem to this with my USB external HDD.

Running Gutsy.

Since I updated the linux headers today, the disk in question has ceased automounting. In fact, Ubuntu can't even see it! I've tried unplugging and replugging, turning off and on, and nothing get Ubuntu to see the drive. Can someone help me?

EDIT: Here's my HAL data:
```
107       4560     1  0 21:41 ?        00:00:00 /usr/sbin/hald
root      4561  4560  0 21:41 ?        00:00:00 hald-runner
107       4602  4561  0 21:41 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event1
107       4603  4561  0 21:41 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event5
107       4604  4561  0 21:41 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event6
107       4605  4561  0 21:41 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event7
107       4611  4561  0 21:41 ?        00:00:00 hald-addon-acpi: listening on acpid socket /var/run/acpid.socket
107       4613  4561  0 21:41 ?        00:00:00 hald-addon-keyboard: listening on /dev/input/event8
107       4633  4561  0 21:41 ?        00:00:00 hald-addon-storage: polling /dev/scd0 (every 2 sec)
tony      6225  6201  0 22:47 pts/0    00:00:00 grep hald
```

---

### Post by wawarren on 2008-02-05
Thanks for this thread.  My link is in the group you posted.  I also tried the solution in the "solved" post, but that doesn't work for me. However, I think my issue is identical to the poster of this thread. 

When I insert any type of data CD, movie DVD, blank media,.. regardless.  I get this error:

```
unable to mount the volume "NEW"
```
expanding the "Details" drop-down
```
mount: must be superuser to use mount
```

I know what I did that caused this, so maybe that can help. 

I plugged in my external USB 120GB IDE hardrive, and as it sometimes happens I got an error regarding an "unsafe removal" since I must have shut down my computer from windows the last time I used it.  

Ubuntu gives you 2 options in this scenario.  1. go back to windows and safely remove it with the "remove hardware" icon in the tray.  2. mount it from the terminal with "-o force"

I opted for the 2nd option, and I used "sudo" to do it.  Ever since I forced my external disk to mount my CDROM doesn't automount.  I don't mean to confuse the 2, cause by all means my external drive works fine now.  

my hal stuff - non CDROM stuff omitted 

```
$ ps -ef | grep hald
107       5447  5379  0 19:43 ?        00:00:00 hald-addon-storage: polling /dev/hda (every 2 sec)
alan      6400  6290  0 21:26 pts/1    00:00:00 grep hald

```

---

### Post by geirha on 2008-02-06
I don't know much about HAL, but I found this bug-report which seems to be about the same problem: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/161044](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/161044)

The last post suggests that doing ```
sudo aptitude reinstall hal
``` should fix things.

---

### Post by tbraun on 2008-02-06
Hello!

Thank you for trying to help...

> **geirha said:**
> I don't know much about HAL, but I found this bug-report which seems to be about the same problem: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/161044](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/161044)

The last post suggests that doing ```
sudo aptitude reinstall hal
``` should fix things.

Sadly, this doesn't fix the problem. After doing this, the relevant HAL module (the one for storage related things) still is not running.

However, DURING the re-installation and subsequent setup of HAL, apparently it does start to work briefly, because if a CD is inserted in the drive during this operation, it does get mounted, and the nautilus window for it pops open.

But that happens only that one time, during the installation, Eject and re-insert the CD and you'll find it still doesn't work.

---

### Post by danwood76 on 2008-02-06
It sounds like it was working for the moment when the HAL was disabled during the re install.
So still a hal issue.

I have no idea where to start with HAL, sorry

---

### Post by tbraun on 2008-02-06
Solved!

For some reason, polling was disabled for HAL. You can use the 'hal-disable-polling' command to enable polling again. That's about as logical as using the 'start' button on Windows to shut down the computer, though... :-)

Anyway, here is what I typed and what I got back as output:

```

backpack:/>  sudo hal-disable-polling --enable-polling --device /dev/scd0
Polling for drive /dev/scd0 have been enabled. The fdi file deleted was

  /etc/hal/fdi/information/media-check-disable-storage_model_CDRWDVD_CRX880A.fdi

```

So, I guess it would have been sufficient to just remove this 'lock' file of sorts. If I would have known about that file ahead of time, I would have taken a look to see what's actually inside the file.

Googling around a bit for that filename, I came across a discussion thread related to powertop (to be found here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456598](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456598)). Maybe powertop wrote that file there? I remember playing around a bit with powertop shortly after I upgraded to Gutsy. Did I inadvertently tell powertop to disable the polling for me? That would suck, because then it would all be my fault to start with. :-(

Since other people are reporting similar problems after a distro upgrade, they may check out the hal-disable-polling command anyway. Maybe that's what happened in their case?

Thank you everyone for your help...

Tom

---

### Post by bodhi.zazen on 2008-02-06
Famous Ubuntu Community Support : 1 :twisted:
Automount : 0

:lolflag:

Please mark as solved.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by danwood76 on 2008-02-06
> **tbraun said:**
> 
That's about as logical as using the 'start' button on Windows to shut down the computer.

Completely off topic -

Never really thought about it like that, hehehe.
Windows is stupid! lol. :D:D

---

### Post by wawarren on 2008-02-07
> **bodhi.zazen said:**
> If you would like help please post additional information.

I just now reviewed the threads you posted, and I am not sure how they apply to you.

One of the threads is marked as solved.

1. What are you trying to mount ?

2. What is the mount point ?

3. Plug in your device / cd and post the output of :

```
sudo fdisk -l

dmesg | tail

mount
```

We also need to look at /etc/fstab . Does the mount point exist ?

@Bloch : I understand what you are saying, +1 pmount ftw.

My point is only that if one would like to see bugs squashed, one needs to start with bug reports.

Hey, I may have found something interesting with your suggestions.  If you don't mind taking a look here's my output. 

dmesg | tail
```
[   56.855210] No dock devices found.
[   56.891030] input: Power Button (FF) as /class/input/input6
[   56.891053] ACPI: Power Button (FF) [PWRF]
[   56.891139] input: Power Button (CM) as /class/input/input7
[   56.891156] ACPI: Power Button (CM) [PWRB]
[   58.073167] Capability LSM initialized
[   61.982565] NET: Registered protocol family 10
[   61.982695] lo: Disabled Privacy Extensions
[   72.620569] eth0: no IPv6 routers present
[17203.759262] slpp[12288]: segfault at 0000000000000000 rip 0000000000401b77 rsp 00007ffff013f020 error 4

```

segfault??

also sudo fdisk -l
```
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3381f162

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       17629   122069902+  83  Linux
/dev/sda3           17630       18241     4915890   82  Linux swap / Solaris

```

I use an SATA drive, so my cdrom is called /dev/hda.  I don't see it above, but i'm not sure if i'm supposed to. Suppose thats my problem though.. . it won't automout. 

My fstab line was posted earlier in this thread if that helps. 

I tried the solution that worked for tbraun, but all I get is a message that says.
" --device /dev/hda
Polling is already enabled on the given drive." 

Thanks, I can move this back to my thread if necessary, but this one seems to have got much better attention.

---

### Post by geirha on 2008-02-08
Since your problem seems to be a bit different, wawarren, I posted a reply to your two posts here in your thread. [http://ubuntuforums.org/showthread.php?t=686842](http://ubuntuforums.org/showthread.php?t=686842)

---

