---
title: "Can you partition twice?"
date: 2012-12-12
forum: General Help
---

### Post by BulgarianBoy on 2012-12-12
I am asking if I can increase the windows partition since it is to small right now it is 50gb and it is almost full. I have ubuntu installed and I want to make its partition smaller I will never be able to fill the hard drive.

---

### Post by haqking on 2012-12-12
> **BulgarianBoy said:**
> I am asking if I can increase the windows partition since it is to small right now it is 50gb and it is almost full. I have ubuntu installed and I want to make its partition smaller I will never be able to fill the hard drive.

You can make a partition smaller and expand another into the space you free up yes.

Gparted. [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) it is a boot CD/DVD/USB

However make sure you have a clone/backups as if you dont know what you are doing you wont be enjoying yourself for the next few weeks ;-)

Peace

---

### Post by BulgarianBoy on 2012-12-12
Thanks.

---

### Post by sandyd on 2012-12-12
if its a windows partition that windows 7 uses, you will probably want to use the Windows 7 Disk Management instead when resizing windows. Windows 7 gets a bit fussy sometimes, and does not like it when you mess with its partitions.

---

### Post by haqking on 2012-12-12
> **sandyd said:**
> if its a windows partition that windows 7 uses, you will probably want to use the Windows 7 Disk Management instead. Windows 7 gets a bit fussy sometimes, and does not like it when you mess with its partitions.

The Windows Disk management wont resize a Ext4 filestystem, it can only delete them.  It will only resize Windows supported filesystems.

The OP wants to resize a Ubuntu Partition smaller to free up space to then extend the Windows filesystem, but yes i agree when possible use the Windows tool for Windows filesystems, so to the OP when you want to resize the Windows filesystem use the Windows tools.

Peace

---

### Post by BulgarianBoy on 2012-12-12
I have problems. First problem was that I needed to boot from a live USB it worked I can resize the Linux partition, but I cannot add any to the ntfs partition which is my windows.

my partition are
 /dev/sda1     ntfs  (without sub menus)    50gb
/dev/sda2    extended (with two sub menus)   100gb  
  /dev/sda5      ext4   96gb
/dev/sda6    linux-swap 4gb

---

### Post by haqking on 2012-12-12
> **BulgarianBoy said:**
> I have problems. First problem was that I needed to boot from a live USB it worked I can resize the Linux partition, but I cannot add any to the ntfs partition which is my windows.

my partition are
 /dev/sda1     ntfs  (without sub menus)    50gb
/dev/sda2    extended (with two sub menus)   100gb  
  /dev/sda5      ext4   96gb
/dev/sda6    linux-swap 4gb

The free space and the one you want to increase has to be contiguous

---

### Post by Impavidus on 2012-12-12
So the trick is:
1: Shrink your /dev/sda5 from the left (or should I say shrink from the right and move to the right?).
2: Shrink your /dev/sda2 to put the unallocated space between /dev/sda1 and /dev/sda2.
3: Reboot into windows and enlarge your /dev/sda1, which will be called C by windows.

I hope this is understood by both the OP and the specialists. Am I correct?

Best is to do it one step at a time and make backups of your most important files. You shouldn't need them, but you might click the wrong button.

---

### Post by BulgarianBoy on 2012-12-13
Yes but the sda2 has a key that is keeping it located unable to shrink :/

---

### Post by plucky on 2012-12-13
> **BulgarianBoy said:**
> Yes but the sda2 has a key that is keeping it located unable to shrink :/

Right click on the swap partition and turn swap off.

The Live CD/USB mounts the swap partition.

Good Luck

---

