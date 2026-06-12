---
title: "Somebody help a n00bbiee please"
date: 2006-12-17
forum: General Help
---

### Post by badgaz1 on 2006-12-17
Right well I installed Ubuntu today (Dual Booted with XP) and I'm just trying to get the hang of it. I've managed to get NTFS working which I'm quite proud of myself for but now I seem to have messed it up and I need YOUR (yes you) help.

I installed some crazy program called Automatix and told it a load of programs I wanted it to install for me and the massive majority of them failed because of an "apt-based error" and no matter how many times I tried it kept saying this, then I just closed it and carried on exploring Ubuntu. 

Then I tried to install a program using the normal "Add/remove..." tool and I got an error saying "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. " which didn't happen before I decided to mess around with Automatic  because I installed some stuff using it not long beforehand.

So then I made a journey into the terminal and ran 'dpkg --configure -a' and it said I couldn't do it because I wasn't a superuser blah blah so I went and tried it in the root account and tried it and when I did it says “Setting up java-common (0.25ubuntu1) ...” and nothing else seems to happen nor does it fix the problem.

Any help from you nice, friendly, sexy people?

---

### Post by taurus on 2006-12-17
You need to run that command with the sudo so from a terminal, type

```
sudo dpkg --configure -a
(use the same password that you log in with...)
```

Now, which version of Ubuntu do you have (Dapper or Edgy) and are you sure you installed the right version of automatix2 for the right release?  Paste the output of this command here from a terminal?

```
cat /etc/apt/sources.list
```

---

### Post by badgaz1 on 2006-12-17
> **taurus said:**
> You need to run that command with the sudo so from a terminal, type

```
sudo dpkg --configure -a
(use the same password that you log in with...)
```

Now, which version of Ubuntu do you have (Dapper or Edgy) and are you sure you installed the right version of automatix2 for the right release?  Paste the output of this command here from a terminal?

```
cat /etc/apt/sources.list
```


Ooohh the first bit of code fixed it! Thanks a lot for the quick reply, here have a smiley star... :KS

---

### Post by badgaz1 on 2006-12-17
Right I have another brain buster for you. I just tried to install the new version of aMSN and I got this error...

[http://img328.imageshack.us/img328/1213/screenshotdf3.png](http://img328.imageshack.us/img328/1213/screenshotdf3.png)

(I tried the other choice on the list box by the way)

Is it because I am using the x64 version or am I just being a n00b again? (or maybe a combination of the two?)

---

### Post by hikaricore on 2006-12-17
> **badgaz1 said:**
> Right I have another brain buster for you. I just tried to install the new version of aMSN and I got this error...

[http://img328.imageshack.us/img328/1213/screenshotdf3.png](http://img328.imageshack.us/img328/1213/screenshotdf3.png)

(I tried the other choice on the list box by the way)

Is it because I am using the x64 version or am I just being a n00b again? (or maybe a combination of the two?)


it's because you tried to open in installer package in gedit  (think of opening an EXE file in wordpad)  usually you need to open a terminal and do:

chmod +x packagename

./packagename

But some install packages are different than others.  Check for info where you downloaded it.

---

### Post by taurus on 2006-12-17
Isn't amsn in the repos???

---

### Post by hikaricore on 2006-12-17
Why yes it is, I've never used it.  So it slipped my mind.

Dude forget the package unless you have a special need for it.

Goto Applications, Accessories, Terminal

Then type:

```
sudo apt-get install amsn
```

---

### Post by badgaz1 on 2006-12-17
Oooh thanks for that too, that's another problem out of the way...


Right...another :S haha sorry about this

The way I have my system set up at the moment is one hardrive is split into 2 partitions (well 3 if you include the swap), one has Windows installed on it the other Ubuntu. I also have a secondary harddrive with all my files on (which is formatted as NTFS).

I installed NTFS-3g (by running 'sudo apt-get install ntfs-3g') and now it seems to detect my primary harddrives Windows partition but my secondary harddrive still isn't showing.

I went into Root and loaded up QTParted and the harddrive is detected (as hda5) can someone help me get it set up so it is useable?

---

### Post by taurus on 2006-12-17
Paste the output of these two commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat   /etc/fstab
```

---

### Post by badgaz1 on 2006-12-17
badgaz1@badgaz1-desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24222   194563183+   7  HPFS/NTFS
/dev/sda2           24223       30019    46564402+  83  Linux
/dev/sda3           30020       30401     3068415   82  Linux swap / Solaris

Disk /dev/hda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2       24321   195350400    f  W95 Ext'd (LBA)
/dev/hda5   *           2       24321   195350368+   7  HPFS/NTFS




badgaz1@badgaz1-desktop:~$ cat   /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1f1e9f4e-b221-4296-9f81-8d38d1015ca2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=5E44AE4F44AE29AB /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=adf993b4-535f-4b22-88dc-8c3b819e3c41 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by taurus on 2006-12-17
I thought you already installed ntfs-3g so you can write to your ntfs but your /etc/fstab is still using ntfs!!!  Therefore, remove the old entry for /de/sda1 and replace it with the new one, plus the one for /dev/sda5...

```

/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0    0
/dev/sda5   /media/sda5   ntfs-3g   defaults,locale=en_US.utf8   0    0

```
Now, create new mount point for /dev/sda5, unmount /dev/sda1, and mount both partitions again...

```
sudo  mkdir  /media/sda5
sudo  umount  /media/sda1
sudo  mount  -a
df  -h
```

---

### Post by badgaz1 on 2006-12-17
badgaz1@badgaz1-desktop:~$ /dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0    0
bash: /dev/sda1: Permission denied

badgaz1@badgaz1-desktop:~$ /dev/sda5   /media/sda5   ntfs-3g   defaults,locale=en_US.utf8   0    0
bash: /dev/sda5: No such file or directory


:(

---

### Post by taurus on 2006-12-17
You need to open a text editor before you can add those two lines in your /etc/fstab...

Applications -> Accesories -> Terminal
```
gksudo  gedit  /etc/fstab
```
Now, add those two lines at the end of it...

```

/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0    0
/dev/sda5   /media/sda5   ntfs-3g   defaults,locale=en_US.utf8   0    0

```
Don't forget to remove the old one as well.

```

# /dev/sda1
UUID=5E44AE4F44AE29AB /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

```
Save the changes and run

```

sudo  mkdir  /media/sda5
sudo  umount  /media/sda1
sudo  mount  -a
df  -h

```

---

### Post by badgaz1 on 2006-12-17
Right so now that text file looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=1f1e9f4e-b221-4296-9f81-8d38d1015ca2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=adf993b4-535f-4b22-88dc-8c3b819e3c41 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8   0    0
/dev/sda5   /media/sda5   ntfs-3g   defaults,locale=en_US.utf8   0    0





I entered

sudo  mkdir  /media/sda5
sudo  umount  /media/sda1

into the terminal nicely without any problems but

badgaz1@badgaz1-desktop:~$ sudo  mount  -a
Error opening partition device: No such file or directory
Failed to startup volume: No such file or directory
Failed to mount '/dev/sda5': No such file or directory

---

### Post by taurus on 2006-12-17
It should have been

```

/dev/hda5   /media/hda5   ntfs-3g   defaults,locale=en_US.utf8   0   0

```
Save it and create a new mount point.

```
sudo mkdir /media/hda5
sudo rmdir /media/sda5
sudo umount /dev/sda1
sudo mount -a
df -h
```

---

### Post by badgaz1 on 2006-12-17
It worked! You are incredible have 3 smiley stars :KS :KS :KS 

Thanks a ton.

---

### Post by taurus on 2006-12-17
> **badgaz1 said:**
> It worked! You are incredible have 3 smiley stars :KS :KS :KS 

Thanks a ton.

It was my fault for not looking at your "sudo fdisk -l" more careful before, mixing up /dev/hda5 with /dev/sda5, but will take them while I can!  :oops:

---

### Post by badgaz1 on 2006-12-17
Haha it isn't a problem but maybe you could help me with another one of my little issues :p 

Errrr I have an Audigy 4 soundcard and the sound has been working all the time but only through my front 2 speakers (I have 5.1)... Looking in device manager it only detects it as a "SB0400 Audigy2 Value" which is probably why...Any remedy to this that you know of?

---

