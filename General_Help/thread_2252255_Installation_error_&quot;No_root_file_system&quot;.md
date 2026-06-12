---
title: "Installation error: &quot;No root file system&quot;"
date: 2014-11-10
forum: General Help
---

### Post by steve169 on 2014-11-10
I'm a newbie using a Dell Inspiron 660 PC with Windows 7.

I'm trying to install Lubuntu 14.10 onto a 32-GB USB thumb drive.

Working from a Lubuntu live DVD, I used Gparted to create two partitions on the thumb drive: one ext4 partition for Lubuntu (29 GB) and one Linux-swap partition (512MB).

Then when I clicked the install button on the Lubuntu desktop, I got this error message: "No root file system is defined. Please correct this from the partitioning menu."

How do I make this correction?

---

### Post by Rex Bouwense on 2014-11-10
That error message can mean that you skipped a small, but important step. You have not defined the mount point for the partition. It should be "root", indicated by a single forward slash "/".  Have you done that in Gparted?

---

### Post by oldfred on 2014-11-10
Not sure what Lubuntu installer looks like, but using Something Else you have to choose the partition you created for / (root) as root. You also choose format again if already formatted. If swap already created, you do not have to select it.
Also be sure to choose sdb or whatever is correct for your external drive for grub2's boot loader. Otherwise sda drive is the normal default.

Ubuntu installer looks like this & you select change button to choose an existing partition but use/reuse, format/reformat & mount it. Note my example still has the default sda as I have not changed it yet.

       Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by bapoumba on 2014-11-10
@oldfred, lubuntu installer looks the same (Hello :)).

---

### Post by steve169 on 2014-11-12
Dear Rex,

By following your advice I was able to install Lubuntu 14.10 onto my 32-GB USB stick. Many thanks.

However . . .

When Lubuntu is booting from the USB stick, it flashes an error message saying the "dev/mapper/cryptswap1" is "not ready yet or not present." Then it goes ahead and boots Lubuntu, which seems to work fine.

How do I correct whatever's wrong?

---

### Post by oldfred on 2014-11-12
It seems you have created an encrypted install. I do not know about them and that used LVM which is an advanced logical partition overlay.

run these:
 sudo blkid -c /dev/null -o list
sudo cat /etc/fstab

But I am not sure how fstab with the LVM mounts the encrypted swap.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

      
 LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by steve169 on 2014-11-13
I've decided to try reuinstalling Lubuntu without encryption.

---

