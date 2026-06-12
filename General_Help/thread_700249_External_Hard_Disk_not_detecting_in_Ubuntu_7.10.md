---
title: "External Hard Disk not detecting in Ubuntu 7.10"
date: 2008-02-18
forum: General Help
---

### Post by Mohamed Fahim on 2008-02-18
Hi Friends,
  I have two hard disk one is 160 gb which is internal one sata in that i have 4 partition in one i have winxp and in other partition i have Ubuntu 7.10 now i have an external hard disk which is 120gb my external disk is detected clearly in winxp but not in Ubuntu 7.10 when i type lsusb in terminal it shows the following
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0c45:627b Microdia 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 015: ID 067b:2507 Prolific Technology, Inc. - **[COLOR="Red"]this shows up when my external attached through usb device [/COLOR]**
Bus 001 Device 001: ID 0000:0000

---

### Post by buntu_Geek on 2008-02-18
what is the file system used in your external hard disk??

if it is NTFS means... there would be mounting problems...

for solving it u can follow any wiki's on NTFS partition mounting problems.....

---

### Post by intel on 2008-02-20
check the output of command
#dmesg
once before you plugin the external USB drive
then run
#dmesg again after pluggin it in..

and post the new lines that show up in the command output

---

