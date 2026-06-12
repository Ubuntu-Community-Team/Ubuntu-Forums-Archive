---
title: "&quot;System Problem Detected&quot; when booting"
date: 2016-06-26
forum: General Help
---

### Post by Richard_Alexander on 2016-06-26
Good morning.  I am a fairly new user to Ubuntu but, love it.  I have it loaded on three separate laptops in my household.  Thanks for all the support postings that I have read so far.

My problem as my title states is that I have get an error when booting.  I know that the error is associated in some sort with mounting.  I created an automount to a network location.  I modified the /etc/fstab file to include the mount specifics.  The error when booting prohibits the mount from completing however, if I issue a "sudo mount -a" command in a terminal window it completes without issue.  Could someone please assist me with getting this figured out?  Could it be permissions on the /etc/fstab file?  Thanks in advance.

---

### Post by deadflowr on 2016-06-26
Post the fstab, please.

---

### Post by yancek on 2016-06-26
In addition to the fstab file, is this mount point another system with a Linux filesystem and do you have nfs installed?

---

### Post by Richard_Alexander on 2016-06-28
Sorry for the delay.  Late hours.  Here is a snippit of the fstab file for the mount.  This is mounting to a BlackArmor NAS.  

\\192.168.1.102\public /mnt/NAS cifs credentials=/home/rich/mnt_creds,iocharset=utf8,sec=ntlm,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0
\\192.168.1.102\public /mnt/Public cifs credentials=/home/rich/mnt_creds,iocharset=utf8,sec=ntlm,gid=1000,uid=1000,file_mode=0777,dir_mode=0777 0 0

---

### Post by Richard_Alexander on 2016-07-01
Bump

---

### Post by Richard_Alexander on 2016-07-07
Could I get some assistance with this mount issue?  It seems that this could be a permissions error since it will mount with the sudo mount command and not on boot.  Is there someplace that the error that I get on boot in reference to the mount is logged that I can look at to help determine my issue?

---

