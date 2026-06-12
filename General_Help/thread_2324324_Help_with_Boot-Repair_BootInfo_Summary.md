---
title: "Help with Boot-Repair BootInfo Summary"
date: 2016-05-12
forum: General Help
---

### Post by Novash on 2016-05-12
Hello,

I am trying to help my parents fix their computer. It is not booting, and after the BIOS runs it comes to a prompt that says:

> mbr
mbr 123:

I cannot type at this prompt. After googling, I ran Boot-Repair through a Ubuntu Live CD, and the option for "Recommended Repair" was not available, only BootInfo Summary.

I uploaded it to pastebin as suggested, and would like some help.

[http://paste.ubuntu.com/16383341/](http://paste.ubuntu.com/16383341/)

I appreciate any insight anyone can give. 

Much thanks!

Nick

---

### Post by yancek on 2016-05-12
The boot repair link doesn't show much.  In fact more than half the information usually shown is not available.   No boot files show on the windows partition.  It just shows one windows partition on a 1TB hard drive so which windows are you using and is it UEFI/GPT or an MBR install and what happened just before this problem occurred?  The boot repair doesn't usually fix windows boot problems.

---

### Post by LostFarmer on 2016-05-12
Did you run 'testdisk' ?  testdisk was incorrectly used and put its MBR boot code in the MBR and also in the Windows partition VBR .  That will not work.  What Windows version is installed ?  You might be able to rerun 'testdisk' and recover the NTFS partition.

1st window) create log 
2nd           ) select sda (only one displayed)
3rd           ) select  Intel  
4th           ) select Advanced
5th          ) select  the NTFS partition (only one displayed)  at bottom select "BOOT" with arrow keys and press enter
6th         )  if and only if it says " boot sector -BAD  and backup boot sector -GOOD"  at bottom select "Backup BS"  You will need to verify with yes (Y) several times. quit and reboot.  If backup boot sector is also BAD select quit and post back .

see if it will boot if able to select "Backup BS" above.

some help sites with photos on use:
[https://www.maketecheasier.com/recover-data-and-partitions-for-free-with-testdisk/](https://www.maketecheasier.com/recover-data-and-partitions-for-free-with-testdisk/)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#Current_partition_table_status)

---

### Post by Novash on 2016-05-13
Hello, thanks for the input. 

**Yancek:** I called my parents to ask for the story, and it went something like: 

"There were two separate hard disks, one with Windows XP on it and another with Ubuntu on it. GRUB for some reason or another wasn't working correctly anymore, so my dad used Rescatux to fix it. Everything was pretty much working when he saw an option that asked if he would like to rewrite/overwrite the MBR. He said he clicked no, but it overwrote it anyway, and since then he has not been able to boot into Windows." 

Since I sat down at the computer, only the XP partition was plugged in. 

**LostFarmer:** I just found out about 'testdisk' in some forum, and I'm currently using it to backup all the files on the hard drive. When that finishes I will go back and do the steps that you listed.

Thank you both for the input! I really appreciate it.

Nick

---

### Post by Bucky Ball on 2016-05-13
*Thread moved to **General Help**.*

Not related to ***Installations and Upgrades***.

---

### Post by Novash on 2016-05-13
LostFarmer,

It worked!

It was as you said, the boot-sector was bad and the boot-sector backup was 'OK'. I selected the option you recommended, and am now able to boot into windows.

The mouse and keyboard do not work (but did with the live cd), but unless that is related, I'm on to the next problem.

Many many thanks!!

---

### Post by LostFarmer on 2016-05-13
You should replace the non Windows MBR boot code with that for XP.  That is not a must, but the non standard boot code might cause a problem later.

Please mark the problem solved , I think one does it on the ' thread tools" found top right on first post.

Thanks for the feed back and it might help some one else.

---

