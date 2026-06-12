---
title: "fsck - what to choose for usb flash boot sector restoration of corrupted usb"
date: 2015-04-24
forum: General Help
---

### Post by kinnu on 2015-04-24
Greetings All,

My 1GB external usb flash keeps getting corrupted. (I am trying to put lubuntu 14.04 on it using (lubuntu 14.04) System Tools -> Startup Disk Creator). 

Corruption is, strange files in /media/user1/BC26-AE82/syslinux:

   total 2106680
   -rw-r--r--  1 user1 user1          0 Jan  1  1980             =??
   -rw-r--r--  1 user1 user1          0 Jan  1  1980             >>>>>???
   -rw-r--r--  1 user1 user1          0 Jan  1  1980             &#9488;&#9488;?
   drwx------  2 user1 user1      12288 Apr 10 16:07   .
   drwx------ 11 user1 user1       4096 Jan  1  1970     ..
   -rw-r--r--  1 user1 user1          0 Jan  1  1980              &#8319;  <<<&#8319;&#8319;&#8319;°
   -rw-r--r--  1 user1 user1          0 Jan  1  1980              &#8319;&#8319;°
   ...
   -rw-r--r--  1 user1 user1 2155905152 Feb 25  1908  ÇÇÇ    
   -rw-r--r--  1 user1 user1          0 Jan  1  1980    
   -r--r--r--  1 user1 user1          0 Jan  1  1980         

Not sure why the usb flash keeps getting corrupted. I use the Startup Disk Creator -> erase at the beginning and at the end it asks to umount/safely remove the usb flash. 
After erase, I wanted to check the contents, so in terminal I did  

$ ls -la /media/user7/BC26-AE82/
   total 8
   drwx------  2 user7 user7 4096 Jan  1  1970 .
   drwxr-x---+ 3 root  root  4096 Apr 10 15:58 ..

Is it reporting there are 8 files, but 6 are not showing? Is there a way to view/delete them? 

Anyway, to fix this corruption, I umount the usb flash and run 

$ sudo fsck.fat -vl /dev/sdb1

It reports:
   There are differences between boot sector and its backup.
   This is mostly harmless. Differences: (offset: Original/backup)
   3:53/6d, 4:59/6b, 5:53/66, 6:4c/73, 7:49/2e, 8:4e/66, 9:55/61, 10:58/74, 65:01/00, 90:fa/0e, 91:fc/1f, 92:31/be, 93:c9/77, 94:8e/7c, 95:d1/ac, 96:bc/22, 97:76/c0, 98:7b/74, 99:52/0b, 100:06/56, 101:57/b4, 102:1e/0e
   ...

   1) Copy original to backup
   2) Copy backup to original

I do not know which is the better choice: original or backup? 

If one could see the time_stamp of the original and the backup, it would make it easier. Is there a way to see the time_stamp on these? 
If I were to guess, I would think that 'original' refers to the factory settings and 'backup' to something before modification. Is that how it is? 
('boot information' 'boot loader' are written to the usb flash as part of the startup disk).

Suggestions? 
Thanks
kinnu

PS. Thank you robsoles, Bucky Ball, zombifier25, et. al. for your help with [http://ubuntuforums.org/showthread.php?t=2260436&p=13205756#post13205756](http://ubuntuforums.org/showthread.php?t=2260436&p=13205756#post13205756)
That thread was closed before I could thank you all, especially zombifier25.

---

### Post by kinnu on 2015-04-30
Hmm, five days, no response. 
Can someone please direct me to where I may try asking this?

Thanks
kinnu

---

### Post by kinnu on 2015-07-11
Can anyone even see this question?
Am I in /dev/null :-?

If you can see this, please post a line.
Thanks
kinnu

---

### Post by oldfred on 2015-07-11
After fsck are you emptying trash and showing hidden files?

Some flash drives have proprietary "stuff" (technical term) on them.

---

### Post by kinnu on 2015-07-16
Ok, thank you oldfred.

I was not explicitly emptying trash, but next time I will. The startup disk creator pauses after erase, waiting for the user to initiate the next step. In a seperate xterm, to check the contents of the usb flash drive after erase, I did  

$ ls -la /media/user7/BC26-AE82/
   total 8
   drwx------  2 user7 user7 4096 Jan  1  1970 .
   drwxr-x---+ 3 root  root  4096 Apr 10 15:58 ..

where BC26-AE82 is the label arbitrarily assigned to the flash drive after format.  

I think it is reporting there are 8 files and not showing any information on six. That made me think there are (six) hidden files. Dont understand why ' $ ls -la ' is not showing any info (if the hidden files dont have a name, they should have some size size even if it is 0 bytes).

I am sure there is ' proprietary "stuff" (technical term) ' :-) but ' $ ls -la ' should not notice it, for example first 1024 bytes of a HDD have information, but ' $ ls -la ' on a blank formatted HDD does not report it. 

Any thoughts?

---

### Post by oldfred on 2015-07-16
I do not not know, but 1970 as date seems strange, and if FAT32 formatted the default mount is always root as owner. Who is user7?

---

