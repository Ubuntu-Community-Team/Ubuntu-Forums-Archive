---
title: "[SOLVED] Applications uninstallable"
date: 2008-06-30
forum: General Help
---

### Post by gettinoriginal on 2008-06-30
My ubuntu installation seems very slow, (not CPU or Ram problem).  I thought maybe if I uninstalled some uneeded applications that it might help.  But that is not my question, why is it that so many uneeded applications are tied to needed applications ??:confused:  I decided I didn't need a polish scientific calculator, but cannot uninstall it without uninstalling Ubuntu Desktop.  Sorry if this sounds dumb, but that's like saying I need a fishing pole to drive.](*,)](*,)

---

### Post by Elfy on 2008-06-30
Don't worry about uninstalling ubuntu-desktop - it's just a meta package.

---

### Post by forger on 2008-06-30
you could try clearing out your apt cache:
> sudo apt-get autoclean

---

### Post by nikgare on 2008-06-30
> not CPU or Ram problem

Are you sure - how do you know?

---

### Post by gettinoriginal on 2008-06-30
> **nikgare said:**
> Are you sure - how do you know?

I did an htop

Sorry, I do not know how to post a screenshot in the post.

---

### Post by nikgare on 2008-06-30
Can you post the specs of your machine and the output of these commands:

free
df -h
less /etc/hosts

---

### Post by gettinoriginal on 2008-06-30
I have 1G Ram and an AMD processor (not sure the model), 80G HD dual boot with XP.  CPU runs avg of 20% and memory running at about 240mb, 0 swap

Sorry, I do not know how to post a screenshot of the commands you asked for, but they were all within limits.

---

### Post by Elfy on 2008-06-30
You don't need to screenshot - you can just paste the outputs in a post, easier if you can select and then use the # to surround the text with code tags

For future reference - [screenshots]("http://ubuntuforums.org/showpost.php?p=4527031&postcount=4")

[Guide to Forum features]("http://ubuntuforums.org/showthread.php?t=726219")

---

### Post by gettinoriginal on 2008-06-30
hope this is what you want, and thanks for the help

          total       used       free     shared    buffers     cached
Mem:       1035372     670152     365220          0      28304     382104
-/+ buffers/cache:     259744     775628
Swap:      2048248          0    2048248

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              45G  4.3G   38G  11% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   48K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   38M  469M   8% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       45G  4.3G   38G  11% /home/gettin/.gvfs

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by forger on 2008-06-30
What ubuntu release is this anyway? Ubuntu hardy heron 8.04?

Post back the output of this command:
```
sudo fdisk -l
```
It shows the partitions, (maybe your swap is too small).

Also attach the file specs.txt after doing this command (which will create it on your Desktop):
```
sudo lshw > ~/Desktop/specs.txt
```

By the way, forestpixie in post #2 is right, the ubuntu-desktop is a meta-package, it's only necessary when you're upgrading from an older release to a newer one, shouldn't create problems if it's uninstalled :)

---

### Post by gettinoriginal on 2008-06-30
[ATTACH]75803[/ATTACH]

[ATTACH]75804[/ATTACH]

[ATTACH]75805[/ATTACH]

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80568056

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3871    31093776    7  HPFS/NTFS
/dev/sda2            3872        9964    48942022+   5  Extended
/dev/sda5            3872        9709    46893703+  83  Linux
/dev/sda6            9710        9964     2048256   82  Linux swap / Solaris
gettin@gettinscomputer:~$ sudo lshw > ~/Desktop/specs.txt
gettin@gettinscomputer:~$ sudo lshw > ~/Desktop/specs.txt
gettin@gettinscomputer:~$

---

### Post by Elfy on 2008-06-30
> By the way, forestpixie in post #2, the ubuntu-desktop is a meta-package, it's only necessary when you're upgrading from an older release to a newer one, shouldn't create problems if it's uninstalledYes I know :)

(> maybe your swap is too small)Doesn't appear to be - twice RAM, it could be that it's not on though.

---

### Post by Elfy on 2008-06-30
Your htop looks quite normal to me, have you turned off compiz to see what it's like then ?

---

### Post by forger on 2008-06-30
1) still haven't replied: **is it ubuntu hardy heron 8.04**? do this:
```
sudo lsb_release -a
```

2) you have an nvidia graphics card: NV34 [GeForce FX 5200]
Did you install the drivers using menu System > Administration > Hardware Drivers and check them to be "in use"? :)
Should look like the attachment

---

### Post by gettinoriginal on 2008-06-30
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04
Release:	8.04
Codename:	hardy

and yes, my graphics driver is in use.

what is meant by Ram may not be on :confused:

Thank you both for your assistance I am learning by the minute :)

---

### Post by gettinoriginal on 2008-06-30
Sorry, off to work, if there is anything else, I will be back on later tonight.  Thanks again.

---

### Post by forger on 2008-06-30
Well i'm out of ideas :\
Seems that if you want a faster ubuntu, you need to upgrade your hardware :P

What exactly do you mean when you say that it's slow?
- Slow at boot? Leave your desktop running for a 3-4 days, applications should be running faster when loaded from memory.
- Slow firefox? Firefox is slow on my dual core as well :P

---

### Post by Elfy on 2008-06-30
> what is meant by Ram may not be onI was talking about the swap - it would be slow I expect if you had no RAM :)

Load some programs, openoffice - all of them, just to see if you're swap is being used - check with free -m or top

If it isn't being used run the swapon command 

```
 sudo swapon
```

Turn off desktop effects, see if that makes any difference.

> My ubuntu installation seems very slow,This of course is quite subjective and hard to get to the bottom of as I'm sure you understand.

---

### Post by gettinoriginal on 2008-06-30
I turned on 11 programs, and CPU remains at 8 - 12 %, but swap shows 0/2000mb no matter what I do.  I did the swapon command, and got this:
usage: swapon [-hV]
       swapon -a [-e] [-v]
       swapon [-v] [-p priority] special|LABEL=volume_name ...
       swapon [-s]
But even after turning it on, it still reads 0/2000mb  :confused:

---

