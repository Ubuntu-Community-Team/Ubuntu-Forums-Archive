---
title: "Have swap partition, but not being used?"
date: 2008-05-21
forum: General Help
---

### Post by sippyCUP on 2008-05-21
Ubuntu 8.04, upgraded from Gusty Gibbon where I had the same problem. I have one gig of ram and a 1 gig swap partition at the end of my disk.

The weird thing is that I can never catch the system actually using my swap, even though I have had some severe (1 minute +) freezes in GIMP when manipulating (resizing or just loading) 50+ meg images. Sometimes it happens when I just have a lot of applications open (I think I have had the same effect when Brasero is checking mp3s for audio cd burning).


Here is the result of the command swapon -s:
sippy@sippy:~$ swapon -s
Filename				Type		Size	Used	Priority

Nothing, nada. Also, GParted has an option to turn on my swap, but I don't want to go in there every time I boot. Where is the swap activation set upon boot so I can solve this problem?

Thanks for your time,
Eric

---

### Post by sippyCUP on 2008-05-21
I'm thinking... /etc/fstab? My swap line is in there, mount point "none," type "swap," options "sw" dump "0" pass "0".

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=137cc1dc-9164-4b97-8c78-94beaefd0be3 /               ext3    defaults,errors=remount-ro 0       1
# windowsxp
UUID=BECC835ECC830FB7 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=6d6d3128-dd3f-42c1-8984-3dc6aa6b49bc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec     0       0
UUID=dc85c059-9011-4704-984f-5239695ae4e5 /media/300 ext3 0 1

---

### Post by logos34 on 2008-05-21
another command to try 

cat /proc/swaps

one possibility is that swap is listed in fstab but the uuid has changed so it's not automounting (something that's happened to me often).  compare with 

ls -l /dev/disk/by-uuid

---

### Post by cdtech on 2008-05-21
Check your block id with "blkid" and be sure it matches the one in the /etc/fstab file, if not change it. This could cause your swap not to turn on at boot. If you run "free" on a command line this should tell you if your swap is on and how much is being used.

Hope this helps.....

---

### Post by sippyCUP on 2008-05-21
Yup, the UUID had changed! Works perfectly now. Thanks so much guys!

---

### Post by cdtech on 2008-05-21
Yu welcome...

---

### Post by pneukamp on 2008-10-30
I need to know howto configure the live cd so that it does not use SWAP! Is a Forensic Live CD

Please help me!

---

### Post by cdtech on 2008-10-31
If you mean installing, the Live CD has an option dontuse when assigning the SWAP manually.

---

### Post by mempman on 2008-10-31
> **pneukamp said:**
> I need to know howto configure the live cd so that it does not use SWAP! Is a Forensic Live CD

Please help me!


You can turn swap space on/off via the swapon and swapoff command.

---

### Post by pneukamp on 2008-10-31
OK! I understand, but which pass this parameter? Press F6 on the first screen of the Live CD and passing the "swapoff"?
"LABEL live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz splash [COLOR="Red"]**swapoff**[/COLOR] --"

---

