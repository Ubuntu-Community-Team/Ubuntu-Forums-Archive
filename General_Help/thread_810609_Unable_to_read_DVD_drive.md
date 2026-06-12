---
title: "Unable to read DVD drive"
date: 2008-05-28
forum: General Help
---

### Post by srihari_ravi on 2008-05-28
Hi

when I go to Places -> Computer and try opening "CD-RW/DVD±RW Drive", I get the message "Unable to mount location, can't mount file" error (after I insert a disc into drive and open).

Can you help me what I can do to read my DVD?

Thanks
Ravi.

---

### Post by unutbu on 2008-05-28
Please post the output of

```
cat /etc/fstab
```

---

### Post by theophiles on 2008-05-30
Well, I hate to hijack this thread for my own problems, but it was 2 days ago . . .

i am having a similar problem. Oddly enough DVD's mount, but CD's do not from the same device. 

Here is my cat /etc/fstab output
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fc8d0803-2eb8-454a-a3f3-3ef496ca3e53 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=8ff96ad7-2bbb-4e1b-b4de-6da61611d264 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by srihari_ravi on 2008-05-30
Here is the output for *cat /etc/fstab*:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=c31f8ddb-9a98-43e1-aac8-2f266e53b81e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=bc8baf90-ee85-43b8-9b36-20d671925213 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by unutbu on 2008-05-30
theophiles, what happens when you stick a CD in the drive and type

```
mount /media/cdrom0
```

srihari_ravi, please post

```
ls -l /media
```

---

### Post by theophiles on 2008-05-30
> **unutbu said:**
> theophiles, what happens when you stick a CD in the drive and type

```
mount /media/cdrom0
```


```

bcline@BenjiDesktop:~$ mount /media/cdrom0
mount: No medium found

```

---

### Post by srihari_ravi on 2008-05-31
Hi unutbu, here is the output of ls -l /media:

lrwxrwxrwx 1 root  999    6 2008-05-28 02:23 cdrom -> cdrom0
drwxr-xr-x 2 root  999 4096 2008-05-28 02:23 cdrom0
lrwxrwxrwx 1 root  999    7 2008-05-28 02:23 floppy -> floppy0
drwxr-xr-x 2 root  999 4096 2008-05-28 02:23 floppy0

---

### Post by unutbu on 2008-05-31
theophiles and srihari_ravi, I do not see anything wrong with your fstabs or setups in general. I do not know what is causing the problem.

Here are a few things you could try, but they are all desperation plays:

(1) Run
```
gnome-volume-properties
```
Make sure the "Mount removeable media when inserted" option is enabled.

(2) Create a temporary user account. Login as the new user. See if the problem persists. If so, you know the problem is system-wide... maybe a driver or config file. If the problem is not apparent for the new user, then you can conclude that the problem is in one of the config files in your home directory.

(3) Stick a cd in the drive and type in a terminal

```
sudo cat /dev/scd0
```

You should get garbage back. Press Ctrl-C to halt the command. This is a low-level way to access your drive without using the mount command. If you can do this, at least you know the kernel can read the drive. You could then conclude the problem is somewhere higher up the chain of events, though I'm at a loss to say where.

(4) Remove the gnome-volume-manager package and then reinstall it. This [fixed the "No medium found" problem]("http://ubuntuforums.org/showthread.php?t=42075") for rajaiskandarshah.

(5 for theophiles) Do you get the same error for both audio CDs and data CDs?

---

### Post by theophiles on 2008-05-31
> **unutbu said:**
> theophiles and srihari_ravi, I do not see anything wrong with your fstabs or setups in general. I do not know what is causing the problem.

Here are a few things you could try, but they are all desperation plays:
I am up for anything
> **unutbu said:**
> 
(1) Run
```
gnome-volume-properties
```
Make sure the "Mount removeable media when inserted" option is enabled.

I had options for cameras, PDA's, Printers and scanners and input devices, but not CD's
> **unutbu said:**
> 
(2) Create a temporary user account. Login as the new user. See if the problem persists. If so, you know the problem is system-wide... maybe a driver or config file. If the problem is not apparent for the new user, then you can conclude that the problem is in one of the config files in your home directory.

I tried that right away and probably should have mentioned it earlier. 
> **unutbu said:**
> 

(3) Stick a cd in the drive and type in a terminal

```
sudo cat /dev/scd0
```

You should get garbage back. Press Ctrl-C to halt the command. This is a low-level way to access your drive without using the mount command. If you can do this, at least you know the kernel can read the drive. You could then conclude the problem is somewhere higher up the chain of events, though I'm at a loss to say where.

Still at a loss:
```
bcline@BenjiDesktop:~$ sudo cat /dev/scd0
[sudo] password for bcline: 
cat: /dev/scd0: No medium found
```
> **unutbu said:**
> 
(4) Remove the gnome-volume-manager package and then reinstall it. This [fixed the "No medium found" problem]("http://ubuntuforums.org/showthread.php?t=42075") for rajaiskandarshah.

I had a feeling that this would work. But I was wrong.
> **unutbu said:**
> 
(5 for theophiles) Do you get the same error for both audio CDs and data CDs?
Yes, it is the same error, but neither data nor movie DVD's are have an error.

---

### Post by theophiles on 2008-06-01
Thank you for your help, unutbu, I have come to the conclusion that this is a hardware problem and I will soon be learning about Dell's warranty system.

---

### Post by unutbu on 2008-06-01
Type 
```

ls -l /dev/*
```

In particular, look for /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw. These should be links to /dev/scd0 or something. 

I suggest look at everything in /dev/* just in case there is some other device name I'm not aware of.

Is there any difference between /dev/dvd and /dev/cdrom for example? Do they point to different devices? Do you have a /dev/scd0?

---

### Post by Alfred_McGee on 2008-06-08
I seem to be in the same boat as Theophiles, except that CDs mount and DVDs don't. Though it seems that I will soon be learning about Acer's shoestring warranty policy, I post here my   cat /etc/fstab   output, just to see if anyone can help me.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=777ae1e6-c2e9-4712-8636-f3370a511c05 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=98f4bc2c-9bdc-4982-80c4-909af43fce36 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


EDIT: My DVD drive was broken. Just to be fair to the tech support people at Acer: Both times I called them, they answered immediately and were very helpful. Though I did have to pay for one-way shipping, they repaired and quickly mailed my machine back to me, still under warranty. And the fact that I had removed Windows was not a problem.

---

### Post by mc4man on 2008-06-08
Run ```
sudo lshw -C disk
``` could prove informative

---

### Post by Alfred_McGee on 2008-06-08
mc4man: Below is the cdrom result of running **sudo lshw -C disk** 
 
  *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-850S
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.61
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open

The same result comes back whether or not there is a DVD (data or video) in the drive. System-> Preferences-> Removable Drives and Media indicates no optical drive of any sort, even if it's playing a James Brown CD- as it is right now.

I first noticed this DVD problem after using gparted to set up a bootable usb drive. Oh well, I don't know if it helps, but here's what comes back when I enter **sudo lshw -C disk** with a CD in the drive.

*-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ-850S
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.61
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

---

### Post by mc4man on 2008-06-09
@ alfred 
as our discussion here is similar issue, look thru maybe something will stick, odds are the drive should be replaced
[http://ge.ubuntuforums.com/showthread.php?t=645470](http://ge.ubuntuforums.com/showthread.php?t=645470)

---

### Post by Alfred_McGee on 2008-06-10
@mc4man:

Thanks. Read most of that thread. Learned that CDs and DVDs are not read by the same laser. That would explain a lot. Following some of your instructions on that post I tried the following, though it doesn't seem too informative:

$ ls -l /dev | grep dvd*
lrwxrwxrwx  1 root   root           4 2008-06-08 10:06 dvd -> scd0
lrwxrwxrwx  1 root   root           4 2008-06-08 10:06 dvdrw -> scd0

As for the question of tired DVD players lasting a little longer in Windows, I did try booting from a Windows Vista recovery DVD, and that didn't work, either.

---

### Post by ejizzel on 2008-09-26
Im having the same problem as others in which I cannot read any CD's or DVD's. I know my drive is ok because I can use it for other VM's im running

> **unutbu said:**
> theophiles, what happens when you stick a CD in the drive and type

```
mount /media/cdrom0
```

Heres my output

```
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by ejizzel on 2008-10-03
Any help would definitely be appreciated.

---

### Post by mc4man on 2008-10-03
@ ejizzel
If you were running that mount  ... command with an audio cd in the drive then you'd get an error (they don't 'mount' per se and the location is actually home -> .gvfs/ cdda mount on scdx

Try putting a cd and or dvd in the drive with a known compatible filesystem (any data cd/dvd except those made with vista's 'live system' or a movie dvd 
and run 
```
sudo lshw -C disk
```

---

### Post by voltav on 2009-05-02
* (4) Remove the gnome-volume-manager package and then reinstall it. This [fixed the "No medium found" problem]("http://ubuntuforums.org/showthread.php?t=42075") for rajaiskandarshah.*

I had the same problem and fix with this step. I removed genome-volumen-manager and gnome-mount <<complete removal>> (one pack use ubuntu-desktop pack so it will remove too), restart the pc, install the 3 packages and WHUALA! (works), now i put the cds and they mount automatic, very nice. 

That is I did, i dont know if can be more simple, i want just share my experience.

---

