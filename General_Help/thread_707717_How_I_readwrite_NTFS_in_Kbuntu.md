---
title: "How I read/write NTFS in Kbuntu?"
date: 2008-02-25
forum: General Help
---

### Post by the lemming on 2008-02-25
Trying to get my head around Kbuntu but I find it completely different to anything else I have tried in Linux land.

Could somebody please tell me how to be able to read/write to NTFS partitions?

Cheers

---

### Post by Arwen on 2008-02-25
You can do it with ntfs-3g([here]("http://ubuntuforums.org/showthread.php?t=217009"))

---

### Post by logos34 on 2008-02-25
gutsy comes with read/write support (-->ntfs-3g driver), but you need to configure it for your windows partitions.  In a terminal type:

sudo apt-get install ntfs-config

sudo ntfs-config

>enable write support internal or external drives

---

### Post by the lemming on 2008-02-25
> **logos34 said:**
> gutsy comes with read/write support (-->ntfs-3g driver), but you need to configure it for your windows partitions.  In a terminal type:

sudo apt-get install ntfs-config

sudo ntfs-config

>enable write support internal or external drives

I tried your advice and got the following




frank@frank-laptop:~$ sudo apt-get install ntfs-config
[sudo] password for frank:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ntfs-config
frank@frank-laptop:~$ sudo ntfs-config
sudo: ntfs-config: command not found
frank@frank-laptop:~$



Have I done something wrong?

Cheers

---

### Post by logos34 on 2008-02-25
make sure **universe** repository is enabled in synaptic
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)

---

### Post by the lemming on 2008-02-26
> **logos34 said:**
> make sure **universe** repository is enabled in synaptic
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971)


That's just my problem.  I have no idea where the synaptic package manager is with kubuntu 7.10.

Could somedody please direct me to it?

---

### Post by forestpixie on 2008-02-26
kubuntu uses adept - doon't know how to use it

alternatively use th terminal to open sources.list in kate

kdesu kate /etc/apt/sources.list

then 

sudo apt-get update
and try again

---

### Post by logos34 on 2008-02-26
oops...meant adept.

---

### Post by the lemming on 2008-02-26
Learning curve continues.

I have learnt how to use the package manager and have installed loads of NTFS packages.

I tried to use the NTFS config tool in the System tab but nothing happened so I did a "cut and paste" of some advice into the terminal.  Doing this got the NTFS config too to start.  However I was only ablr to select to be able to read external hard drives.  The internal partitions, which were NTFS, just stayed grayed out and as yet I don't know how to enable this feature.

Anybody got any ideas how I can mount and read internal partitions?

I've managed to configure the external drives but that is all so far and I haven't yet tried to read an external drive to see if it is actual working yet.

Cheers

---

### Post by logos34 on 2008-02-26
You never did say what ubuntu version you're using.  Gutsy? Feisty?

You might want to post your **fdisk -l** so we can see how everything is showing up.

Take a look [at this]("http://www.psychocats.net/ubuntu/mountwindows").  

You could try manually adding ntfs read/write entries to fstab.  E.g.:
> 
/dev/hda1 /media/hda1 ntfs-3g defaults,locale=en_US.UTF-8 0 0

---

### Post by the lemming on 2008-02-27
> **logos34 said:**
> You never did say what ubuntu version you're using.  Gutsy? Feisty?

You might want to post your **fdisk -l** so we can see how everything is showing up.
g.:



Hello, I'm using Kubuntu 17.10

and here is the info you asked for


frank@frank-laptop:~$ fdisk -l
frank@frank-laptop:~$ sudo fdisk -l
[sudo] password for frank:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3bba3bb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1             547        5884    42877485    7  HPFS/NTFS
/dev/sda2               1         546     4385713+  12  Compaq diagnostics
/dev/sda3   *        5885        9565    29567632+  83  Linux
/dev/sda4            9566        9729     1317330    5  Extended
/dev/sda5            9566        9729     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order
frank@frank-laptop:~$



Hope this helps

Cheers

---

### Post by Yellow Pasque on 2008-02-27
Ok, open up /etc/fstab with gedit  (sudo gedit /etc/fstab in Terminal) and add this line (or modify the current line for /dev/sda1 if it exists)

```
/dev/sda1  <directory you want to mount to>  ntfs-3g  rw,auto,exec,user,uid=1000  0  0
```

Make sure that the dir you want to write to exists and is empty. You can make a dir in /media if you don't know what directory to mount to.
```
cd /media
sudo mkdir win_disk
sudo chmod 777 win_disk
```
Then, your fstab line would look just like above, but would start with:
```
/dev/sda1  /media/win_disk .... 
```

---

