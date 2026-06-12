---
title: "NTFS change permission problem while copying"
date: 2007-12-08
forum: General Help
---

### Post by true_friend on 2007-12-08
I am on dual boot XP + Kubuntu 7.10. I've converted my all partitions to NTFS after installation of kubuntu latest. Now when I try to copy any file from linux root to c, d or e (windows volumes) I get this message. 
Cannot change permissions for xxx
Some time transferring a large amount of data annoys me as i have to press enter for almost equal to the number of files being copied.
Any ideas to solve it?
Regards

---

### Post by patty mac on 2007-12-08
There's an NTFS write driver that may or may not come installed, the fact that you're able to write at all indicates that you have it.  Other than that, try:

$sudo chmod +w name-of-ntfs-formatted-directory

I believe that they are defaulted to mount read only in most Linux distrobutions.  If you want to change that, open up /etc/fstab with a text editor with sudo priviledges, it'll look something like this:

/dev/hda2  	 /  	                ext2  	defaults  	                1 1
/dev/hdb1 	 /home 	           ext2     defaults 	                   1 2
/dev/cdrom 	/media/cdrom   auto 	ro,noauto,user,exec 	0 0

Change ro to rw for the NTFS partitions you want to be able to write to, and they should trouble you no longer.

---

### Post by true_friend on 2007-12-08
This is the entry of a Windows partition.
/dev/sda8  /media/sda8     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
I basically converted these partitoins from FAT32 to NTFS from within windows by a convert command. Then I have changed the lines in /etc/fstab to ntfs rw support. NTFS is being read and write fine. Only this copying is creating these annoying messages...

---

