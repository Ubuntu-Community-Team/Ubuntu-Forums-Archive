---
title: "BTRFS sadness: impossible to reuse BTRFS-formatted /home partition for Lubuntu?"
date: 2018-02-18
forum: General Help
---

### Post by RoestVrijStaal on 2018-02-18
I've dusted of my little workforce laptop and replaced the EOL  Manjaro with a Lubuntu 17.10 install. I was smart enough to put /home at  a separate partition to make distro switching easier. During install I  told the installer to use the partition as /home mountpoint and NOT  format it. 


  So far so good. But I discovered that the installer didn't pick my  existent home profile folder. Somehow my data at separate /home  partition has become invisible despite  -a-blackbox-package-about-filesystems- reports that the partition is  used for about the same amount as it was before the installation. So for  me it seems the data is somewhere. 


  It looks like BTRFS is the curpit. But after doing btrfs subvolume list /home, only one entry returned. Which placed me on doubt if my data still exists. I tried to change subvol=@home to subvol=@ but that resulted in Emergency mode. 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=nopenope-nope-nope-nope-nopenopenope /               btrfs   defaults,subvol=@ 0       1
# /boot was on /dev/sda1 during installation
UUID=nopenope-nope-nope-nope-nopenopenope /boot           ext4    defaults        0       2
# /home was on /dev/sda4 during installation
UUID=nopenope-nope-nope-nope-nopenopenope /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sda6 during installation
UUID=nopenope-nope-nope-nope-nopenopenope none            swap    sw              0       0
```

I'm out of ideas. Did I lost my data or is there a way to restore it?

---

### Post by mastablasta on 2018-02-19
was the home data encrypted?

if the /home wasn't supposed to be formated, then it would not be formatted or erased. wheather the parittion is BTRFS or EXT4 - it shouldn't matter IMO.

also a couple of guys over at Kubuntu forums really know a lot about BTRFS. just a tip.

---

### Post by Impavidus on 2018-02-19
I don't know Manjaro. Does it give the first user UID 1000 like Ubuntu? Did you use the same user name? If not, the files may be somewhere else than where you expect them. Check```
ls -l /home
```

---

### Post by The Cog on 2018-02-19
Firstly I would mount the btrfs volume at root - assuming the partition is /dev/sda9 (which it probably isn't) then do:
```
sudo mkdir /mnt/btrfsroot
sudo mount /dev/sda9 /mnt/btrfsroot
```
and now you can explore the whole partition. You could start by listing the subvolumes
```
sudo btrfs subvolume list
```
and you should be able to see them looking like directories with a file manager. If you feel the need you can rename subvolumes by renaming them in the enclosing volume just as though they are ordinary directories. You will probably just find @ and @home subvolumes in the top level of the volume.

---

### Post by RoestVrijStaal on 2018-03-01
First thank you all for your quick response. It became quicker than I expected. And due problems at my end I'm able to answer the things now.

> **mastablasta said:**
> was the home data encrypted?
Nope, it's not (due performance issues).
> **mastablasta said:**
> 
if the /home wasn't supposed to be formated, then it would not be  formatted or erased. wheather the parittion is BTRFS or EXT4 - it  shouldn't matter IMO.
My thoughts then.
> **mastablasta said:**
> also a couple of guys over at Kubuntu forums really know a lot about BTRFS. just a tip. I tried Kubuntu as well before installing Lubuntu. Despite the Kubuntu LiveUSB didn't ran that fluent because KDE is more resourcehungry than LXDE. I regret for not installing Kubuntu, because Lubuntu doesn't even support hotswapping UsbSticks in 2018 and Kubuntu has more a go-go-go factor because it installs things out-of-the-box. May I find it weird that a flavor of Ubuntu has more skilled people than the generic Ubuntu?

> **Impavidus said:**
> I don't know Manjaro. Does it give the first  user UID 1000 like Ubuntu? Did you use the same user name? If not, the  files may be somewhere else than where you expect them. Check```
ls -l  /home
```If i recall, my user UID was 1000 as well. At least I used the same user name as my previous (Manjaro) install. 

The result of the command is: ```
total 0
drwxr-xr-x 1 roestvrijstaal roestvrijstaal 620 mrt  1 11:24 roestvrijstaal

```Which isn't a surprise. 

> **The Cog said:**
> Some helpful instructions Ok, I discovered something weird.

After mounting my sda4 (not sure if I could mount it again because a part of it was already mounted via fstab). I discovered there are two directories in /mnt/btrfsroot/

```
# ls -lr /mnt/btrfsroot
total 0
drwx------ 1 roestvrijstaal roestvrijstaal 3084 jan 23 20:18 roestvrijstaal
drwxr-xr-x 1 root root    8 jan 29 02:40 @home

```So the first directory bears all my files of my previous install. Phew!

But how do it manage to make that folder my /home/folder and get rid of the @home subvolume with my current unneeded home folder?

---

### Post by RoestVrijStaal on 2018-03-12
Bump, I got the feeling I'm close to goal but just need a few hints for the right direction.

---

### Post by RoestVrijStaal on 2018-04-04
Ok, it turns out ideas for a solution is beyond the knowledge of anyone in these forums?

---

### Post by HermanAB on 2018-04-05
Well, basically, you have to edit /etc/fstab to mount the correct partition in the correct place.

You cannot have two directories with the same name, so if there already is a directory called /home which was created during the install process, then you need to rename it to something else, make a new empty directory called /home as a mount point and then mount your old btrfs partition onto that mount point.

In order to change the mountings, the partitions need to be unmounted and not in use.  So the easiest way to change things is to log in as root into single user mode, then fix things and reboot.

---

### Post by RoestVrijStaal on 2018-04-08
> **HermanAB said:**
> Well, basically, you have to edit /etc/fstab to mount the correct partition in the correct place.

You cannot have two directories with the same name, so if there already is a directory called /home which was created during the install process, then you need to rename it to something else, make a new empty directory called /home as a mount point and then mount your old btrfs partition onto that mount point.

In order to change the mountings, the partitions need to be unmounted and not in use.  So the easiest way to change things is to log in as root into single user mode, then fix things and reboot.Unfortunately it isn't that simple. I'm dealing with subvolumes here, not partitions. (Yay BTRFS).

An additional problem is the @home-subvolume Lubuntu created has the path '/home/myhomedir'. But the subvolume myusername Manjaro created begins directly at '/myusername' without the additional home-folder. 

I tried renaming the current home (volume/directory/whatever) to a different name, make a new directory bearing the same name and moved my old directory to there. No luck.

Well it seems my only way out of BTRFS-subvolume-hell is the same how I let my files escape out NTFS-hell: Booting SystemRescueCD and shrink the current BTRFS-parttion, make a new Ext4-partition, copy files over to new partition, shrink BTRFS-partition, copy files over the new Ext4-partition and repeat the process till files are safely out the BTRFS-hell. 

Seems BTRFS is too powerful or distro-installers differ to much to detect and handle previous installations of linux.

---

### Post by sisco311 on 2018-04-08
It looks to me like the installer created a home@ subvolume for your home directory. And on your old installation the top level subvolume was used to hold your files.

Can't you simply mount the top level subvolume via fstab?
```
# /home was on /dev/sda4 during installation
UUID=nopenope-nope-nope-nope-nopenopenope /home           btrfs   defaults,**subvol=@** 0       2

```

If that works then you can delete the unneeded subvolume.

---

### Post by RoestVrijStaal on 2018-04-18
> **sisco311 said:**
> It looks to me like the installer created a home@ subvolume for your home directory. And on your old installation the top level subvolume was used to hold your files.

Can't you simply mount the top level subvolume via fstab?
```
# /home was on /dev/sda4 during installation
UUID=nopenope-nope-nope-nope-nopenopenope /home           btrfs   defaults,**subvol=@** 0       2

```

If that works then you can delete the unneeded subvolume.Hehehe Unfortunately it wasn't, because I already tried to change the subvol to @ before I started this topic.

Anyway, I solved the problem with the hard way as I described earlier. Unfortunately the installation of Kubuntu didn't went easy on me but that's a different subject (and topic).

Thanks to you all for the help anyway! :thumbsup:

---

### Post by stereoplegic2 on 2019-03-25
> **sisco311 said:**
> It looks to me like the installer created a home@ subvolume for your home directory. And on your old installation the top level subvolume was used to hold your files.

Can't you simply mount the top level subvolume via fstab?
```
# /home was on /dev/sda4 during installation
UUID=nopenope-nope-nope-nope-nopenopenope /home           btrfs   defaults,**subvol=@** 0       2

```

If that works then you can delete the unneeded subvolume.

This was the key for me, coming from a Parrot Security OS 4.4 install (BTRFS by default) to Ubuntu and variants (Ext4 by default) with a dedicated /home partition mount.

---

