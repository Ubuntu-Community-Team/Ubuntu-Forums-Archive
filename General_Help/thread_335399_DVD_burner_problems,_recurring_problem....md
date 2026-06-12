---
title: "DVD burner problems, recurring problem..."
date: 2007-01-10
forum: General Help
---

### Post by uberlinux on 2007-01-10
So this is a recurring problem that I've googled and researched extensively, and tried all the fixes to no avail.

[SIZE="2"][COLOR="Red"]The Problem[/COLOR][/SIZE]
When I burn the first ever DVD on a kubuntu installation, it works fine.  After that it no longer works.  No matter what.  This has been on multiple different computers and burners, and has happened since 5.10

[SIZE="2"][COLOR="Red"]The Error[/COLOR][/SIZE]
```
System
-----------------------
K3b Version: 0.12.17

KDE Version: 3.5.5
QT Version:  3.3.6
Kernel:      2.6.17-10-generic
Devices
-----------------------
_NEC DVD+-RW ND-3450A 102B (/dev/hda, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96R; RAW/R96R; Restricted Overwrite]

Used versions
-----------------------
growisofs: 6.1
mkisofs: 2.1.1a03-unofficial-iconv

growisofs
-----------------------
:-( unable to pread64(2) primary volume descriptor: Input/output error
    you most likely want to use -Z option.

growisofs command:
-----------------------
/usr/bin/X11/growisofs -M /dev/hda -use-the-force-luke=notray -use-the-force-luke=tty -dvd-compat -speed=8 -use-the-force-luke=bufsize:32m -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-ksf/k3bUanYic.tmp -rational-rock -hide-list /tmp/kde-ksf/k3bhHrrVb.tmp -joliet -hide-joliet-list /tmp/kde-ksf/k3bJL6Pec.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-ksf/k3bhQRZKb.tmp 


```

This happens with dvd+R and dvd-R.  Growisofs seems to be thinking that I'm trying to use RW's even though I'm not.  This has happened with many types of discs.

This has been a royal pain in my butt for a long time and I even RMA'ed a drive back to newegg over it before I knew what was up.  So thanks in advance for any help.

---

### Post by uberlinux on 2007-01-10
BUMP back to page one!
(Hope that's OK on these forums.)

---

### Post by kebes on 2007-01-10
> **uberlinux said:**
> When I burn the first ever DVD on a kubuntu installation, it works fine.  After that it no longer works.  No matter what.  This has been on multiple different computers and burners, and has happened since 5.10

Just to clarify: when you say that the first DVD "works fine" but then "it no longer works." Do you mean that you are to burn one disk, and then can't burn another disk until you reboot. Or do you mean that the after burning a single disk, the DVD writer never works again, no matter what. (Even after reboot, or putting it into another computer, etc...) ? (or do you mean something else entirely...)


I was about to suggest that you try an upgrade, but your versions are actually as new or newer than mine:
$ k3b --version
Qt: 3.3.6
KDE: 3.5.2
K3b: 0.12.17

$ growisofs --version
* growisofs by <appro@fy.chalmers.se>, version 5.21,
  front-ending to mkisofs: mkisofs 2.01-unofficial-iconv (i686-pc-linux-gnu)

I've never had the problem you describe when using k3b. What happens if you try to burn a disk purely with "growisofs" instead of using k3b as a frontend? Are you able to burn multiple disks in that case? I believe k3b lets you edit the flags that you pass along to growisofs, so you could play with that.

For instance the error messages suggest, at one point, adding the -Z option. The "-Z" option is what you use to start a new initial session on a disk. So doing:
growisofs -Z /dev/dvd /home/user/dirtoburn/

hould burn a single session to a completely blank DVD. If that works on the commandline then try passing it as a parameter in k3b.

---

### Post by uberlinux on 2007-01-10
> **kebes said:**
> Just to clarify: when you say that the first DVD "works fine" but then "it no longer works." Do you mean that you are to burn one disk, and then can't burn another disk until you reboot. Or do you mean that the after burning a single disk, the DVD writer never works again, no matter what. (Even after reboot, or putting it into another computer, etc...) ? (or do you mean something else entirely...)

The latter.  I can no longer burn DVD's from that point on without reinstalling Kubuntu.

> **kebes said:**
> 
I've never had the problem you describe when using k3b. What happens if you try to burn a disk purely with "growisofs" instead of using k3b as a frontend? Are you able to burn multiple disks in that case? I believe k3b lets you edit the flags that you pass along to growisofs, so you could play with that.

When I try to pass on the -Z flag to growisofs in the K3b program, it does not stick.  I do not know why.  I entered -Z in 'parameters'

> **kebes said:**
> 
For instance the error messages suggest, at one point, adding the -Z option. The "-Z" option is what you use to start a new initial session on a disk. So doing:
growisofs -Z /dev/dvd /home/user/dirtoburn/

hould burn a single session to a completely blank DVD. If that works on the commandline then try passing it as a parameter in k3b.
Would doing that command actually burn the DVD?
Thanks
Also I thought that the -Z had to do with dvd-rw's and multisession stuff where I don't need that cause I'm using DVD-R's

---

### Post by uberlinux on 2007-01-10
Also I have tried to set the multisession option to anything instead of auto, and then an error always comes back and says no dvd-rw media found.

---

### Post by uberlinux on 2007-01-10
```

ksf@pchs:/dev$ sudo growisofs -Z /dev/dvd /home/ksf/Desktop/Muzik/Rock/ClassicRock/ClassicRock2/
Executing 'mkisofs /home/ksf/Desktop/Muzik/Rock/ClassicRock/ClassicRock2/ | builtin_dd of=/dev/dvd obs=32k seek=0'
INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.

```
results in this error:
:-( /dev/dvd: 15872 blocks are free, 275280 to be written!
:-( write failed: No space left on device

---

### Post by kebes on 2007-01-10
By the way, you shouldn't have to use sudo to use "growisofs"... (If you can't access growisofs as a normal user, maybe that's a clue...)


Also, check how much free disk space you have. I'm not sure, but maybe growisofs needs to create a diskimage of the iso to be copied. Do:
df -h

Are any of the partitions running out of disk space?

---

### Post by uberlinux on 2007-01-10
Thanks for your reply.  I'm not sure if I needed to use sudo or not, I knew there were some things that needed it in K3b.
Here are the results of df -h, all good there:
dksf@pchs:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   30G   38G  44% /
varrun                505M   76K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                505M     0  505M   0% /dev/shm
lrm                   505M   18M  488M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sdb1             496M   54M  443M  11% /media/USB DISK
ksf@pchs:~$

---

### Post by kebes on 2007-01-10
You said that the burner will start working again (only once!) if you reinstall Kubuntu. What if you just reinstall the growisofs (and/or mkisofs) package?

sudo aptitude remove growisofs
sudo aptitude remove mkisofs

sudo aptitude install growisofs


Does it then work afterwards? (only once or does it keep working?)

---

### Post by uberlinux on 2007-01-10
Still didn't work.  hmmm

---

