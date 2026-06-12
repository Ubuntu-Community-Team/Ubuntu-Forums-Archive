---
title: "Hide unmounted drives from Nautilus side panel"
date: 2013-10-24
forum: General Help
---

### Post by adi06 on 2013-10-24
Hi all,

i have a NTFS drive showing in side panel of nautilus, which i dont want to be available as it is my **/dev/sda2 **C drive, installation of Windows 7 dual booted with Ubuntu
It is not mounted, nor it is in fstab. Not even in /mnt/ nor in /media/ abviously if not mounted. ^_^
How can i remove this from side panel, as this have no purpose for me to use, and is a critical drive to be messed with by anyone.

A thing was bugging me why would Nautilus show that drive and not my system recovery partition which is also ntfs.
And i read that GVFS is the reason that nautilus show drives inside side-panel.

I tried this solution but it didn't do anything.
[http://askubuntu.com/questions/236315/hide-boot-drive-from-nautilus](http://askubuntu.com/questions/236315/hide-boot-drive-from-nautilus)

My system:
Ubuntu 13.10 Unity

---

### Post by xiccarph on 2013-10-25
This is alot easier than it use to be.  There is a 'hint' which is used by Nautilus to determine whether or not to make a partition visible.
Use the Disks app in Ubuntu.
Find the partition you want to remain invisible.
If I am remembering correctly, there is an option under the Settings for the partition/drive that allows you to have the partition not be visible.
I'm not in front of my Ubuntu machines right now...when I am I will update my post with some more specific information about where to find that option

---

### Post by oldfred on 2013-10-25
Hide mount - examples with UUID or device using noauto

 sudo mkdir /mnt/SysRes
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0


 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list

 sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

If you want read only:

 Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

---

### Post by adi06 on 2013-10-25
@xiccarph
OMG =D> u are awesome. Really its never been this easy hehe, i'm so happy 
Thanks for the help, i got it. usng this method, i can easily mount my drives at anyplave with GUI and no rough comand :guitar:
@oldfred, u are as alwasy helpful in ndeed. thanks man. :)

[IMG]http://img842.imageshack.us/img842/7004/37cd.png[/IMG]

---

### Post by xiccarph on 2013-10-26
Hey [COLOR=#000000]adi06, glad you got it...I knew it was there but didn't remember exactly.
And thanks for putting in a screenshot so other users know what to do.

Finally the whole udisks thing is coming to fruition.

[/COLOR]

---

### Post by Dominicus on 2013-12-28
I'm attempting the very same thing, yet can't seem to get to the "Mount Options" screen shown.

I'm running Ubuntu 12.04.3 from a USB drive created with the Ubuntu startup disk creator, with persistence.  So called LiveUSB.

I'm able to run the Disk Utility 3.0.2, which shows similar output to the screenshot shown, but I fail to find any way to show Mount Options.  My goal is same as the OP, hide the Win7 boot drive altogether from Nautilus.

---

### Post by oldfred on 2013-12-28
If you have the older Disk Utility with 12.04 then you do not have the newer Disks that has improvements. You can do it the manual way as in post #3.

---

### Post by PopsTheSailor on 2014-01-01
I'm trying to do the same thing but in Mint 16 with Nemo. Will this work with Nemo? The drives still show up. They are not mounted but I want to eliminate them from showing up to remove some clutter. I have a bunch of logical drives but most are not associated with Mint and don't want them listed.

I tried using both the Disks utility and the manual method. Neither of them removed them fromt he view in Nemo.

---

