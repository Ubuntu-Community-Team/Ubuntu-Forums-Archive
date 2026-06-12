---
title: "How To Determine If 2nd Mount Worked"
date: 2023-07-03
forum: General Help
---

### Post by Old Jimma on 2023-07-03
Hello Ubuntuers:

With the help of people in the forum (TheFu), I was able to add a 2nd m.3 SSD. See: [HTML]https://ubuntuforums.org/showthread.php?t=2488332[/HTML]

My question in this thread is: "How can I verify if the 2nd mount really worked? When I write to what I think that 2nd m.2 SSD is, am I really writing to it, did the mount fail and am I writing on the other m.2 SSD where the operating system is and where my home directory is?"

I sure would like to learn how to do this verification. I've written over more that my share of operating systems! I want tto be very, very sure that I'm not doing that, please!

Many thanks!

Old Jimma

---

### Post by ixeous on 2023-07-04
The mount command will show stuff like blow.  In this case it shows the lvm volumes.  You can use lvdisplay and pvdisplay to track it back to specific devices.

```
[FONT=monospace][COLOR=#000000]
dev/mapper/VGsys-LVdata1 on /data1 type xfs (rw,relatime,seclabel,attr2,inode64,logbufs=8,logbsize=32k,noquota) [/COLOR]
/dev/mapper/VGsys-LVtmp on /tmp type xfs (rw,relatime,seclabel,attr2,inode64,logbufs=8,logbsize=32k,noquota) 
/dev/mapper/VGsys-LVhome on /home type xfs (rw,relatime,seclabel,attr2,inode64,logbufs=8,logbsize=32k,noquota) 
/dev/md0 on /boot type xfs (rw,relatime,seclabel,attr2,inode64,logbufs=8,logbsize=32k,noquota) 
/dev/mapper/VGsys-LVvar on /var type xfs (rw,relatime,seclabel,attr2,inode64,logbufs=8,logbsize=32k,noquota) 
/dev/mapper/VG3tdata-LV3tdata on /3tdata type xfs (rw,relatime,seclabel,attr2,inode64,logbufs=8,logbsize=32k,noquota)

[/FONT]
```

You can also use lsblk to show you that info.  For example, in the below output you can see the device (sda, sdb, etc),  the partition (sda1, sdb2, etc), other info.  But you can also see the mount point that it is attached to.  You can deduce from that which physical drive you are using for your mount.


```
[FONT=monospace][COLOR=#000000]
NAME                                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT [/COLOR]
sda                                               8:0    0 465.8G  0 disk   
&#9500;&#9472;sda1                                            8:1    0   9.5M  0 part   
&#9500;&#9472;sda2                                            8:2    0   967M  0 part   
&#9474; &#9492;&#9472;md0                                           9:0    0   966M  0 raid1 /boot 
&#9492;&#9472;sda3                                            8:3    0 418.1G  0 part   
  &#9492;&#9472;md1                                           9:1    0   418G  0 raid1  
    &#9492;&#9472;luks-b28b2a46-7264-4a5b-9d5a-aed6530800ec 253:0    0   418G  0 crypt  
      &#9500;&#9472;VGsys-LVroot                            253:1    0     4G  0 lvm   / 
      &#9500;&#9472;VGsys-LVswap                            253:2    0     8G  0 lvm   [SWAP] 
      &#9500;&#9472;VGsys-LVusr                             253:3    0    60G  0 lvm   /usr 
      &#9500;&#9472;VGsys-LVvar                             253:4    0     8G  0 lvm   /var 
      &#9500;&#9472;VGsys-LVhome                            253:5    0     8G  0 lvm   /home 
      &#9500;&#9472;VGsys-LVtmp                             253:6    0     4G  0 lvm   /tmp 
      &#9492;&#9472;VGsys-LVdata1                           253:7    0   200G  0 lvm   /data1 
sdb                                               8:16   0 465.8G  0 disk   
&#9500;&#9472;sdb1                                            8:17   0   9.5M  0 part   
&#9500;&#9472;sdb2                                            8:18   0   967M  0 part   
&#9474; &#9492;&#9472;md0                                           9:0    0   966M  0 raid1 /boot 
&#9492;&#9472;sdb3                                            8:19   0 418.1G  0 part   
  &#9492;&#9472;md1                                           9:1    0   418G  0 raid1  
    &#9492;&#9472;luks-b28b2a46-7264-4a5b-9d5a-aed6530800ec 253:0    0   418G  0 crypt  
      &#9500;&#9472;VGsys-LVroot                            253:1    0     4G  0 lvm   / 
      &#9500;&#9472;VGsys-LVswap                            253:2    0     8G  0 lvm   [SWAP] 
      &#9500;&#9472;VGsys-LVusr                             253:3    0    60G  0 lvm   /usr 
      &#9500;&#9472;VGsys-LVvar                             253:4    0     8G  0 lvm   /var 
      &#9500;&#9472;VGsys-LVhome                            253:5    0     8G  0 lvm   /home 
      &#9500;&#9472;VGsys-LVtmp                             253:6    0     4G  0 lvm   /tmp 
      &#9492;&#9472;VGsys-LVdata1                           253:7    0   200G  0 lvm   /data1 
sdc                                               8:32   0   2.7T  0 disk   
&#9492;&#9472;sdc1                                            8:33   0   2.7T  0 part   
  &#9492;&#9472;md126                                         9:126  0   2.7T  0 raid1  
    &#9492;&#9472;luks-c7d78ab2-73d7-4213-ba3e-b6f419cc523a 253:8    0   2.7T  0 crypt  
      &#9492;&#9472;VG3tdata-LV3tdata                       253:9    0   2.6T  0 lvm   /3tdata 
sdd                                               8:48   0   2.7T  0 disk   
&#9492;&#9472;sdd1                                            8:49   0   2.7T  0 part   
  &#9492;&#9472;md126                                         9:126  0   2.7T  0 raid1  
    &#9492;&#9472;luks-c7d78ab2-73d7-4213-ba3e-b6f419cc523a 253:8    0   2.7T  0 crypt  
      &#9492;&#9472;VG3tdata-LV3tdata                       253:9    0   2.6T  0 lvm   /3tdata
[/FONT]
```

---

### Post by Old Jimma on 2023-07-04
Thanks, ixeous:

Here is my blkid:
> 
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0     4K  1 loop /snap/bare/5
loop1         7:1    0  63.3M  1 loop /snap/core20/1822
loop2         7:2    0  63.4M  1 loop /snap/core20/1950
loop3         7:3    0  73.9M  1 loop /snap/core22/766
loop4         7:4    0 346.3M  1 loop /snap/gnome-3-38-2004/119
loop5         7:5    0 349.7M  1 loop /snap/gnome-3-38-2004/140
loop6         7:6    0 466.5M  1 loop /snap/gnome-42-2204/111
loop7         7:7    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop8         7:8    0  45.9M  1 loop /snap/snap-store/638
loop9         7:9    0  12.3M  1 loop /snap/snap-store/959
loop10        7:10   0  49.8M  1 loop /snap/snapd/18357
loop11        7:11   0  53.3M  1 loop /snap/snapd/19457
loop12        7:12   0   304K  1 loop /snap/snapd-desktop-integration/49
loop13        7:13   0   452K  1 loop /snap/snapd-desktop-integration/83
nvme1n1     259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme1n1p1 259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme1n1p2 259:2    0   931G  0 part /
nvme0n1     259:3    0 931.5G  0 disk 
&#9492;&#9472;nvme0n1p1 259:4    0 931.5G  0 part /media/camillesmith/WD1



I have 2 m.2 SSD's



From the output of blkid listed above, it seems that:
[LIST=1]
[*]one of the m.2 SSDs nvme1n1, and
[*]the second m.2 SSd nvme0n1
[*]
[/LIST]

What concerns me is:
[LIST]
[*]the mount point specified in my /etc/fstab for the 2nd m.2 SSD is /home/WD1, and
[*]I DON'T SEE THAT MOUNT POINT LISTED IN THE blkid output.
[*]
[/LIST]

Rather, the output of blkid seems to indicate that the mountpoint of the 2nd m.2 SSD is **/media/camillesmith/WD1**

To me, this is extremely worrisome and implies that when I write to what I think is the 2nd m.2 SSD, I'm actually writting on the first m.2.

If this is correct, then If I save alot of data one what I think is the 2nd m.2 SDD, I'll actualy be filling up the first m.2 SSD and will possibly write over the opperating system.

Ie, my attempt to mount the 2nd m.2 SSD failed for some reason, and is a harard to my system.

Is this correct?

Old Jimma

---

### Post by HermanAB on 2023-07-04
Here is a simple trick I use.  One mounts a disk on a directory called a mountpoint. When mounted, everything in it becomes invisible and instead shows the newly mounted disk contents.

Therefore my simple trick is to create a file in the mount point called notmounted or some such: 
# mkdir /mnt/ssd2
# touch /mnt/ssd2/notmounted

Then a simple ls /mnt/ssd2 will show the notmounted file if the mount process  failed.  That can then be used as a test, to prevent a backup script from going wild when the ssd is not mounted.

BTW, the drive space command df (diskfree) is very useful to see what is going on with your disks.  The output is much more clear and concise than the mount command.

---

### Post by Dennis N on 2023-07-04
It would help to see the output of this&#8595; because it is mounting like an external drive.

```
mount | grep nvme0n1p1
```

---

### Post by grahammechanical on 2023-07-04
> nvme1n1     259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme1n1p1 259:1    0   512M  0 part /boot/efi
&#9492;&#9472;nvme1n1p2 259:2    0   931G  0 part /
nvme0n1     259:3    0 931.5G  0 disk 
&#9492;&#9472;nvme0n1p1 259:4    0 931.5G  0 part /media/camillesmith/WD1

What you are calling the second nvme drive the system is calling it the first nvme drive. And what you are calling the first nvme drive the system is calling it the second nvme drive. I do not know why that is happening. I guess it depends on which slot each drive has been put.

nvme0 = 1st nvme drive. nvme1 = 2nd nvme drive. 

Your operating system [boot & root (including /home) ] is on nvme1. You can save stuff to either drive since both are mounted. Whatever application you are using at the time has to be directed to save stuff to a folder on nvme0. You most will likely have to search in the /media folder for cammillesmith/ to do what you want to do.

Downloads through the web browser will still go in /home/Downloads. Unless you change the setting of the browser to download into /media/camillesmith/[any folder name]. The second nvme drive is treated as if it is a folder/directory. Which to the OS it is. 

The same principles apply if we have only one SSD/nvme/hard drive and create another partition for data so as not to fill up /Home/Username. In my case (with one nvme) I have to search for /mnt/Data/whatever folder I want to put stuff in. I have to do the same thing when I want to open a document/file on the Data partition.

Regards




Regards

---

### Post by Old Jimma on 2023-07-04
Hello Dennis N:

Here is the output:
> 
/dev/nvme0n1p1 on /media/camillesmith/WD1 type ext4 (rw,nosuid,nodev,relatime,errors=remount-ro,uhelper=udisks2)


Thanks. I do not see a /home/WD2  ;-(

---

### Post by Old Jimma on 2023-07-04
Hi HermanAB:

I tried it and rebooted.

a file named "notmounted" appeared.

---

### Post by Old Jimma on 2023-07-04
I tried it and rebooted.

a file named "notmounted" appeared.

---

### Post by Dennis N on 2023-07-04
> **Old Jimma said:**
> Hello Dennis N:

Here is the output:
/dev/nvme0n1p1 on /media/camillesmith/WD1 type ext4 (rw,nosuid,nodev,relatime,errors=remount-ro,uhelper=udisks2) 
Thanks. I do not see a /home/WD2  ;-(

The output shows this device is being mounted with udisks2, which is used to mount external devices like a USB stick. It can't be mounted twice - using udisks2 and also with /etc/fstab. Is your drive an external or internal drive?

---

### Post by ixeous on 2023-07-04
It's very odd to me that it would mount the device that way.  /media tends to be used for removable media.  Things like usb as DennisN mentioned.  You could probably edit /etc/fstab to prevent that and have it mount in the same location every time.

adding an entry such as

```

/dev/nvme0n1p1 /path/to/mount  ext4  defaults 0 1

```

I would personally not use /home/WD1.  /home tends to be for user home folders and I like to have "system level storage" mounted differently.  That choice is entirely yours though.

Using UUID is the "modern" way of entering devices into fstab.  Use the blkid command to find the UUID of the device/partition.  Then your entry would look something like

```

[FONT=monospace][COLOR=#000000]/dev/disk/by-uuid/{big-long-string} /path/to/mount ext4 defaults 0 1[/COLOR]
[/FONT]
```

---

### Post by Old Jimma on 2023-07-05
Thanks, Dennis N.

Thanks to you, I've fixed that.

Sincerely,
Old Jimma

---

### Post by MAFoElffen on 2023-07-05
Things have been said, that hit on the edges of this, but have spun out. I agree with what has been said and will point out which of each I use, for myself, and my customers, and for the companies I used to work for...

I just realized that I now have been doing System Admin, System Engineer, Developer, Database Admin, Network Admin... for over 35 years. Dang. Back with UNIX in 1988. Through the years, I have had to follow IT policies, Best Practices, and Standards. I could say that a mount has to go in a certain location... But when it comes down to it, it really doesn't. You are free to put it anywhere. You don't have to follow anyones policies but your own.

I will point out that /media is meant for removable media devices, where the system, if there are system utilities that do filesystem automount of removable media, that it is going to use /media/$USER/<device_label_or_name>...

By 'Best Practices', folder /mnt is meant to do temporary mounts to do file recovery, chroots into an installed system to do repairs and such... Where we have to clean up what is there after an umount. 

For example, I contribute to the 'boot-repair' script. I am the Project Lead for the Ama-GI Project. Both those use folder /mnt to mount an installed system from a Live Environment using that folder, we create mountpoint tags under /mnt/ to do that. We try to use names for those that outguess what a User would do previous to that. We can assure that from a Live Environment, but those scripts are also installed on metal, so... we hope not to blow out someones hard work (other mounts under that folder).

See where that might be a risk or problem?

Next, I also use lsblk to confirm mountpoints (and other things), both in diagnostics, and in my scripts... lsblk is very flexible in what you can show and what you need to see. For verifying mountpoints and seeing if something is writing to where I want it to, I do something like this.
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e 7 -o name,label,size,fstype,model,type,mountpoint
NAME   LABEL       SIZE FSTYPE MODEL                   TYPE MOUNTPOINT
sda                1.8T        Samsung SSD 870 QVO 2TB disk 
&#9500;&#9472;sda1 {SYSTEM}    550M vfat                           part /boot/efi
&#9500;&#9472;sda2             128M                                part 
&#9500;&#9472;sda3 {Windows}   900G ntfs                           part 
&#9500;&#9472;sda4             983M                                part 
&#9500;&#9472;sda5              30G                                part 
&#9492;&#9472;sda6           931.4G ext4                           part /
sdb                1.8T        Samsung SSD 870 QVO 2TB disk 
&#9500;&#9472;sdb1           931.5G ntfs                           part 
&#9492;&#9472;sdb2           931.5G ext4                           part /home/mafoelffen/Disk2
sdc              931.5G        Dogfish SSD 1TB         disk 
&#9492;&#9472;sdc1 mSATA1    931.5G ext4                           part /home/mafoelffen/mSATA

```
For mountpoints, this is my personal laptop, with 3 SSD drives, of 5TB storage. I am the only User. I want to get to my data. I put the mount in my Home and make bookmarks in nautilus so they show up in the left panel of, so I can get to them quickly.

For shared User type computers, and servers, I put the folder off from root-- Shared data, network shares, database files, etc. To make that easier for users to get to, I will either create symlink to those in their User Home folders, or I will create .desktop files for them to get there and give them access to those.

But as I said, there are hundreds of ways in Linux to do the same thing. That makes my job of supporting and repairing people's systems challenging sometimes, trying to follow other people's logic, on guessing what they might do, or what they did in the past, if I can't see what that 'somehow' in front of me. If remotely, I'm not looking over their shoulder, seeing what they see through their eyes.

On unique disk identifiers, that has been discussed in other threads that were linked from the OP. I personally went over the various ways to do that, and in many alternate ways. As long as they point uniquely to the where it needs to be, and is persistent from boot to boot...

********************************************************************************************
Which this:
```

nvme0n1 259:3 0 931.5G 0 disk
&#9492;&#9472;nvme0n1p1 259:4 0 931.5G 0 part /media/camillesmith/WD1

```
Is a problem. You said your fstab file told it to mount at /home/$USER/WD1... That would mean your fstab mount is failing. But that would mean that udisk2 is doing a filesystem automount of that internal M.2 SSD(???) Why is it showing up as a removable storage type to udisk2? If the mount failed, it logically should not be mounted at all. Not be automounted at the system boot.

What is the current mount line in your /etc/fstab? 

---> What might be the query to track this down may be this:
```

grep -i '\-\-mount\|mounting \/' /var/log/syslog.1 | grep 'nvme0n1'

```
Then post the output it  to put within CODE Tags...

---

### Post by Old Jimma on 2023-07-05
I've found a simple way to confirm that a device is mounted.

It is easy to determine with gparted:

[LIST=1]
[*]starte gparted
[*]In the upper right corner, click on the pull down menu, and look for the device you want to evaluate
[*]a new gparted parge will list that device,
[*]right click on the device,
[*]select the "information" option,
[*]Under "Filesystem," look at "Status."
[*]Gparted will say either "Mounted" or "Not Mounted."
[*]
[/LIST]

I hope this helps.

Old JImma

---

### Post by Dennis N on 2023-07-05
There's no answer to post 10, so if the disk is an external drive, I would guess udisks2 is just mounting it before the fstab entry can. fstab can't mount something that's already mounted. They may be some priority of mounting operations?

Also I don't know what post 12 is referring to. Something I asked you to fix?

This thread is marked as solved, so I guess you are satisfied.

---

### Post by MAFoElffen on 2023-07-05
@Dennis N --- Agreed, I am confused also. In all 3 threads on this, I see the OP marking them as Solved before them actually are...

Very good observation. You have jogged my memory. It is mounting at /media instead of where they wanted it to mount, which is a concern to both of us. If the drive is external USB, then this
```

gsettings set org.gnome.desktop.media-handling automount false

```
would disable the default setting to automount USB devices at boot.

On my last post, I asked about what the current fstab line was, because I could not find it in this thread, though they referred to having it mount off from their Home. I found it in post #3 here: [https://ubuntuforums.org/showthread.php?t=2488332&p=14149154#post14149154](https://ubuntuforums.org/showthread.php?t=2488332&p=14149154#post14149154)
```

# new m.2 ssd
Label=WD1 /home/WD1 ext4 defaults,nofail,discard,nodev,nosuid,noexec,fsck 0 2

```
Man page fstab
```

discard/nodiscard
   Controls whether ext4 should issue discard/TRIM commands to the underlying block device 
   when blocks  are  freed. This  is  useful  for  SSD  devices  and  sparse/thinly
   -provisioned LUNs, but it is off by default until sufficient testing has been done.

```
Which is useful for removable flash storage, but for SSD's (RE:[https://unix.stackexchange.com/questions/366949/when-and-where-to-use-rw-nofail-noatime-discard-defaults](https://unix.stackexchange.com/questions/366949/when-and-where-to-use-rw-nofail-noatime-discard-defaults))
> 
As for today, you could achieve better performance and data health by [Periodic trimming]("https://wiki.archlinux.org/index.php/Solid_state_drive#Periodic_TRIM") instead of a continuous trimming on your fstab. There is even a [in-kernel device blacklist]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/drivers/ata/libata-core.c#n4557") for continuous trimming since it can cause data corruption due to non-queued operations.

Not sure which is 'more' true there... With SSD's beyond Gen 1, where in Gen 1 SSD's, there was actually proven valid concerns from that.

nodev & nosuid are usually special security for public facing systems, not usually for Users who reside on a private LAN network... But no harm there from using that.

IDK now. I am still concerned that this is not actually solved yet, until their drive mounts to /home/WD1 as directed in their fstab, instead of under /media.

---

### Post by Old Jimma on 2023-07-05
Hi MaFoEiffen:


You and Dennis N have articulated my concern accurately:

**You articulated the concern that I did not have the technical vocabulary to express.**

>  ...am still concerned ... drive mounts to /home/WD1 as directed in their fstab, instead of under /media. 

Exactly. If it mounts under /media and one doesn't know that and thinks it is someplace else on another device.... well, somebody is gonna have a bad, unhappy day because [B]you might run out of space and write over something. 
[/B]

That has been my concern... because that has been my experience.

**The important thing is to know that one has been successful in writting an fstab that correctly mounts your device successfully... at the mount point you've designated in the fstab.**
[B]
One can find out if that devices is successfully mounted using gparted;[/B]

[LIST]
[*]Open gparted,
[*]in the upper right corner choose the device that you are interested in,
[*]on the next gparted "page/screen" right click on the device of interest, and then...
[*]choose "information."
[*]
[/LIST]
The subsequent screen will provide information that says precisely:
[LIST]
[*]whether the device is mounted or not, and
[*]where it is mounted (hopefully on your mount point of choice).
[*]
[/LIST]


[B]
 You can then verify from gparted how much space is available and how much space is used immediately after it is mounted.

Then, if you add a big-ish to that device, and ask gparte how much space has been used and how much available.... the difference should be the size of that file.

If it is the same, you are proably in good shape and he device is successfully mounted.
[/B]

Isn't this enough to close the post and call it solved?

Old Grey Jimma

---

### Post by TheFu on 2023-07-05
Use the **mount** command without any options. That will show all the current mounts.
It is common to **grep** that output for the mount-point you hope is mounted and if the count returned is exactly 1, then it is mounted.  

_OR_

You could run a **df -Th** and look at the mounts.  Perhaps with **grep** again. 

_OR_

There are other methods, like placing an empty file under the mount point.  If that file can be seen, then the mount didn't happen.  If the mount worked, then that file won't be there because the mounted storage will hide it. This method would use less resources to test, but you'd have to pre-setup the empty file.   Say /d/D1/.notmounted is the empty file. Then 
```
if [ -f  /d/D1/.notmounted ] ;  then
  echo "SSD is _not_ mounted."
else
  echo "SSD is  mounted."
fi
```

Easy to test. This works regardless of file type, volume manager, whatever.

I'd never use **gparted** just to see if something were mounted.  That's beyond overkill and bloat.  It is like loading an OS onto a computer to see if the computer has AC power connected.

Ah - see that I've been ninja'd by a few people.

---

### Post by MAFoElffen on 2023-07-05
Also handy is this minor difference to the columns-shown options (-o) of 'lsblk':
```

   MOUNTPOINT  where the device is mounted
  MOUNTPOINTS  all locations where device is mounted

```
Those do show different output... Example
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e 7 -o name,size,label,mountpoint,mountpoints
NAME     SIZE LABEL     MOUNTPOINT             MOUNTPOINTS
sda      1.8T                                  
&#9500;&#9472;sda1   550M {SYSTEM}  /boot/efi              /boot/efi
&#9500;&#9472;sda2   128M                                  
&#9500;&#9472;sda3   900G {Windows}                        
&#9500;&#9472;sda4   983M                                  
&#9500;&#9472;sda5    30G                                  
&#9492;&#9472;sda6 931.4G           /                      /var/snap/firefox/common/host-hunspell
                                               /
sdb      1.8T                                  
&#9500;&#9472;sdb1 931.5G                                  
&#9492;&#9472;sdb2 931.5G           /home/mafoelffen/Disk2 /home/mafoelffen/Disk2
sdc    931.5G                                  
&#9492;&#9472;sdc1 931.5G mSATA1    /home/mafoelffen/mSATA /home/mafoelffen/mSATA

```
'mount' should show them. To make things easier to see quickly, I usually add this filter
```

mount | grep -v 'loop\|snap\|sys\|run\|proc\|tmp\|devpts\|hugetlbfs\|mqueue'

```

---

### Post by Old Jimma on 2023-07-06
I tested the method TheFu provides in code: 

> 
testfile="/mnt/WD1"
if [ -e "$testfile" ]
then
  echo "WD1 drive is mounted."
  date
fi



It works well. Very easy.

Also, I tested both methods  MAFoElffen  offered.

> 
lsblk -e 7 -o name,size,label,mountpoint,mountpoints

works very well.

Also, 

> 
mount | grep -v 'loop\|snap\|sys\|run\|proc\|tmp\|devpts\|hugetlbfs\|mqueue'



Some of Those methods presuppose that users know how to interpret output from the scripts... output that can be cryptic if you are just a casual Ubuntu user that know nothing about scripts or bash.

... and these days, there are companies that manufacture computers and laptops loaded with ubuntu... and they are bought by many people who don't know bash, and don't care. They just want to use the great free software they can get with Ubuntu: engineers: ocatve; statisticians: RStudio, musicians: musescore, audacity, Sudio... etc;  artists: gimp, kritta, inkscape, karbon; etc); molecular science, space science, national defense, etc.

If you are one of those people, why not use gparted? It is has a semi-friendly user interface and provides output in English language.  


[B]
What is wrong with that??? [/B]

I'd be grateful to know. I must be not understanding something thoroughly again.

Thanks again,
Old

---

### Post by Dennis N on 2023-07-06
This is like a detective game with not all yet revealed.

No one has suggested **lsusb** command. It might provide some great clues.  Try it and your WD drive might be there. Here is the result I get with an external HDD connected:

```
dmn@Kayleigh:~$ lsusb
Bus 002 Device 002: ID 2537:1066 **[COLOR="#FF0000"]Norelsys NS1066[/COLOR]**
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 003: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 001 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 005: ID 1462:7d45 Micro Star International MYSTIC LIGHT 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

And there I recognize my HDD: Norelsys NS1066

What do you see?

---

### Post by TheFu on 2023-07-06
> ```
testfile="/mnt/WD1"
if [ -e "$testfile" ]
then
echo "WD1 drive is mounted."
date
fi
```

This isn't correct.  You need to put a file inside the directory that disappears when the mount is working.  If you mount onto /mnt/WD1, that's a directory and testing that it exists is useless.  Of course it exists.  BTW, a directory is just a file, so it will pass the -e test. You need to use a regular file test, -f.

---

### Post by Old Jimma on 2023-07-06
thank you!!!!!!!!!

If you are in the neighborhood, stop in an have a cuppa.... _anytime_.

---

