---
title: "&quot;doesn't contain a valid partition table&quot; but it works and has worked for ages ?"
date: 2014-04-09
forum: General Help
---

### Post by southof40 on 2014-04-09
Server Ubuntu 12.04 running within VirtualBox.

I wanted to add some more disk for use by the VM. I'm using [this page]("https://muffinresearch.co.uk/adding-more-disk-space-to-a-linux-virtual-machine/") as guidance.

I created the disk via VirtualBox and booted the VM. I did a `fdisk -l` and it reported that a drive I had been using for months "doesn't contain a valid partition table". It reported the same thing for the new drive which I expected but I thought I had better find out what was going on before I went any further. I've put the output of the `fdisk` below.

Before I did anything I had cloned the VM so I booted the clone and did a `fdisk` in there and sure enough it too reported that the months old partition "doesn't contain a valid partition table".

Is this OK ? Can I continue to partition the new drive ? Should I do something about the old drive ?

The `fdisk` output looks like this :


```
~ $ sudo fdisk -l
[sudo] password for foodoo:

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004ce84

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758    16775167     8136705    5  Extended
/dev/sda5          501760    16775167     8136704   8e  Linux LVM

Disk /dev/sdb: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777216 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/ubserver1-root: 7763 MB, 7763656704 bytes
255 heads, 63 sectors/track, 943 cylinders, total 15163392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubserver1-root doesn't contain a valid partition table

Disk /dev/mapper/ubserver1-swap_1: 532 MB, 532676608 bytes
255 heads, 63 sectors/track, 64 cylinders, total 1040384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubserver1-swap_1 doesn't contain a valid partition table
~ $

```



Thanks

---

### Post by oldfred on 2014-04-09
LVM is logical partitions. Fdisk is only showing the physical partitions underneath the logical.

You need to use LVM tools to edit LVM partitions.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by southof40 on 2014-04-09
Thanks oldfred.

I see what you mean about the lvm.

I don't much care whether it's lvm or not but the page at [https://muffinresearch.co.uk/adding-more-disk-space-to-a-linux-virtual-machine/](https://muffinresearch.co.uk/adding-more-disk-space-to-a-linux-virtual-machine/) assumes it's not (hence their use there of fdisk) so if you or anyone else knows how to persuade VirtualBox to create a new disk outside of lvm I would appreciate it .

---

### Post by southof40 on 2014-04-09
Sorry I meant to say ... I appreciated your list of links about lvm, just for your future reference one of  them is broken :  [http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html) .

Thanks again.

---

### Post by oldfred on 2014-04-09
I do not know LVM, but it is a logical partition on top of physical partitions. 
So you use fdisk to create just one partition on a drive and then with LVM tools add that to your logical volume(s).

I tend towards wanting reliability. As I understand it one of the disadvantages of LVM is if one drive fails, you lose all data. Or really good backups are vital. 
But I would rather just mount partitions and use them, I still have to back up my data, but both drives should not fail at same time so I have less chance of loss with any one failure. But then I have to manage partitions and have to go to more work to resize them.

---

