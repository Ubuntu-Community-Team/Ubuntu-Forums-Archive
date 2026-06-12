---
title: "Offline File Manager Recommendations"
date: 2012-10-29
forum: General Help
---

### Post by Greg Roberts on 2012-10-29
Hi
 
I suspect this is a common question but my search did not find it. I have a x64 Ubuntu v9.1 machine.
 
>> I after recommendation of a bootable ISO (like gparted, clonezilla) which has a file manager to allow files to be copied and edited, WITHOUT the OS running ?
 
In this way i can adjust mount drives which are locked by processes.
 
NB: I found [http://www.techrepublic.com/blog/10things/10-linux-rescue-tools-for-recovering-linux-windows-or-mac-machines/1458](http://www.techrepublic.com/blog/10things/10-linux-rescue-tools-for-recovering-linux-windows-or-mac-machines/1458) abd tried Ubuntu-Rescue-Remix but when it boots it does not show any of the underlying drives ?
 
I tried serveral ISos, the ADRIANE_KNOPPIX_V7.0.4CD-2012-08-20-EN would complain about a lvm2 error when trying to mount the root /dev/sda1 drive
ubuntu-9.10-desktop-amd64 comes close which in the Palimpset Disk Utiltiy shows all the drives , however it will not let me mount or have access to the /dev/sda1 drive (LVM2, Ext4), it will allow file access to the 255MB Firesystem partition (Ext2)
 
So as i can't get to the underlying /etc/fstab file, i am snookered.
 
Interesting, it is happy to mount the new LVM Ext4 drive on /dev/sdc1  but not the LVM2 (ext4) on /dev/sda1, sdb1
 
Thanks

---

