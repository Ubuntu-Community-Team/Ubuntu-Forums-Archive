---
title: "Second Hard Drive"
date: 2007-01-13
forum: General Help
---

### Post by El Viejo Lobo on 2007-01-13
I just installed Edgy eft on my desktop leaving no Windows XP -I love it- but I do have a problem with my second hard driver, as I am, new to Linux and Ubuntu I left the second HDD of my PC disconnected while installing Ubuntu  6.10 in the first HDD.
Now I need to join the second HDD where all my data (from XP time) is stored to the system. I plug to the PC it and reboot but I do not see it going to "Places/Computer where I do see the CD RW drive and filesystem. What I have to do to get the two hard drivers work together?](*,)

---

### Post by souki on 2007-01-13
hello,

I suppose you are talking about ide drives ?
if so, they will not be mounted automatically, you have to do this manually

first, check if the drive is properly connected, in a terminal, with this command :

> sudo fdisk -lthis should list all disks and partitions available
then, check which partitions are already mounted :

> df -hpost the results here, and you'll probably get an answer

---

### Post by El Viejo Lobo on 2007-01-13
I hope that it will be OK

yigal@ubuntux2:~$ sudo fdisk -l 
Password:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4810    38636293+  83  Linux
/dev/hda2            4811        4998     1510110    5  Extended
/dev/hda5            4811        4998     1510078+  82  Linux swap / Solaris
yigal@ubuntux2:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              37G  3.4G   32G  10% /
varrun                252M  140K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  144K  9.9M   2% /proc/bus/usb
udev                   10M  144K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   8% /lib/modules/2.6.17-10-386/volatile

---

### Post by taurus on 2007-01-13
Are you sure you have connected and plugged in your second harddrive because it's not on the list, no /dev/hdb?  See if the BIOS even sees your second harddrive.

---

### Post by El Viejo Lobo on 2007-01-19
what I am missing here? I have it but can not use it.
If I go to:  Places/Computer  I do not see my second hard drive which is my old data from windows age.
When I go to System/Administration/Device manager  I can see two hard disks - one is the Ubuntu installation and the other is my old windows data bank named DATOS  
-IDE  device (slave) 
     -Maxtor 4D080H-4       Device :
        - Volume                          Vendor : Unknown
        - Volume (swap)                Device: Unknown
        - DATOS                            Status: Status
                                             Device type: storage
                                            Capabilites: storage,block  
Terminal: 
yigal@ubuntux2:~$ sudo fdisk -l
Password:

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4810    38636293+  83  Linux
/dev/hda2            4811        4998     1510110    5  Extended
/dev/hda5            4811        4998     1510078+  82  Linux swap / Solaris

Disk /dev/hdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        9872    79296808+   7  HPFS/NTFS
/dev/hdd2            9873        9964      738990    f  W95 Ext'd (LBA)
/dev/hdd5            9873        9964      738958+  82  Linux swap / Solaris
yigal@ubuntux2:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              37G  4.8G   30G  14% /
varrun                252M  172K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  160K  9.9M   2% /proc/bus/usb
udev                   10M  160K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   18M  235M   8% /lib/modules/2.6.17-10-386/volatile
/dev/hdc              608M  608M     0 100% /media/cdrom0
yigal@ubuntux2:~$ 

What is the magic word?

---

### Post by taurus on 2007-01-19
Okay, so you want to mount /dev/hdd1 (ntfs).  Open a terminal and edit your /etc/fstab.

```
gksudo gedit /etc/fstab
```
Scroll to the end and add this line to it.

```
/dev/hdd1   /media/hdd1   ntfs   nls=utf8,umask=0222  0   0
```
Save it.  Then, create a new mount point for it and mount it.

```
sudo mkdir /media/hdd1
sudo mount -a 
df -h
```

p.s.  And there is no magic word at all.

---

### Post by El Viejo Lobo on 2007-01-20
The "no magic" worked, thanks a lot to Taurus and the others.
 I am 61 years old "farm boy" new to linux/ubuntu that had to learn how survive with Windows/crash/virus/spy/ads and more.  Ubuntu is a kind of MAGIC for me.):P

---

### Post by pecos.wil on 2007-01-21
Help, I have tried to get Ubuntu to recognize my XP Hard drive,  What is did was install a 15 gig hd and then installed Ubuntu on that.  I have a dual boot effectively & i would like access to the XP hd [which has a name also]. i have tried to follow the steps but on the last step i run into this problem:
[INDENT]pecoswil@pecoswil-desktop:/$ sudo gedit /etc/fstab
pecoswil@pecoswil-desktop:/$ sudo mkdir /media/hda1
pecoswil@pecoswil-desktop:/$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/INDENT]

What am I doing wrong?

---

### Post by El Viejo Lobo on 2007-01-26
In my case, it is Ubuntu with no Windows at all. I had a second hdd as a store in my Windows system before Ubuntu was installed as the only OS and I needed to be able to read the data that was saved on at my Windows time. I am too newbie to answer your question, the info that was showed here is for a different problem then your. I am sure that the good people  that helped me will help you too. You may have a better and quicker answer if you will put your problem in a new post or thread.   keep smiling:guitar:

---

