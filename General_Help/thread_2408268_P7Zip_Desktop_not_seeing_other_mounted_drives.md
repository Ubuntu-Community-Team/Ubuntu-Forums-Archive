---
title: "P7Zip Desktop not seeing other mounted drives"
date: 2018-12-16
forum: General Help
---

### Post by whooty-mcwhooface on 2018-12-16
I am trying to perform some archiving in .7z format using P7Zip Desktop.  The program was installed using apt and had no errors (p7zip p7zip-full p7zip-rar packages).

I am running Ubuntu Budgie 64-bit 18.04.1 LTS under VMware® Workstation 15 Player Ver. 15.0.2 build-10952284.  I have also setup a VM using non-flavored Ubuntu 64-bit 18.04.1 LTS and it has the same issues.  No custom configurations (other than using a larger hard drive spec and partitioning the extra space for data storage mucking around).

I can see both the second partition on the VM machine mounted and also the USB flash Drive that I am using to store data in the File Manager.  I can also pop a terminal and see them via ***ls -l /media/username/*** and can **cd** to them as well.

The issue I am having is within the GUI Desktop program, I cannot see the mounted drives.  if I go to the root directory, I go to the /media directory and see nothing there listed.  Is this a rights issue??  How come the program cannot see the system partition or the flash drive?

I know it is possible to do it through the command line from the root directory using the command with the full path for the file and it compressed the file without any issue.  

What am I missing?


>  
***username@ubuntu*:  p7zip -k /media/username/Downloaded/Test-file.pdf **

7-Zip (a) [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,64 bits,1 CPU Intel(R) Core(TM) i5-3337U CPU @ 1.80GHz (306A9),ASM,AES-NI)

Scanning the drive:
1 file, 20941551 bytes (20 MiB)     

**Creating archive: /media/username/Downloaded/Test-file.pdf.7z**

Items to compress: 1

                    
Files read from disk: 1
Archive size: 13418288 bytes (13 MiB)
**Everything is Ok**


---

