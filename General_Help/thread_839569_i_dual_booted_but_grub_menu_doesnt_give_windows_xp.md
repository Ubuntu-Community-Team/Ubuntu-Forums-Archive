---
title: "i dual booted but grub menu doesnt give windows xp?"
date: 2008-06-24
forum: General Help
---

### Post by dinbrca on 2008-06-24
title.. grub doesnt show windows xp in dual boot menu

---

### Post by fooman on 2008-06-24
please post the output of:

```
sudo fdisk -l
```

---

### Post by dinbrca on 2008-06-24
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04d304d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       38912   312560608+   f  W95 Ext'd (LBA)
/dev/sda5            9139       35246   209712478+  82  Linux swap / Solaris
/dev/sda6           35247       38912    29447113+   7  HPFS/NTFS
/dev/sda7               1        9138    73400890+  83  Linux

Partition table entries are not in disk order

```

---

### Post by logos34 on 2008-06-24
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

except for root use (hd0,1) or (hd0,5).

but it may not work

are you sure sda6 is windows system partition (c:\) ? If so, how did it end up on logical partition?

---

### Post by dinbrca on 2008-06-24
I dont realy know how to check the number of the windows hd i mean like what is the hd(x, x) of windows.. (i am new to linux).. how do i check this?

---

### Post by logos34 on 2008-06-24
grub starts counting from 0

linux designation - grub designation

sda2 --> hd0,1   (i.e. first drive, second partition)  this is the extended partition containing the others, with boot flag (*)
sda5 --> hd0,4   (first drive, fifth partiiton)
sda6 --> hd0,5    ( "       "    sixth  "       ) windows/NTFS
sda7 --> hd0,6  ubuntu root

---

### Post by dinbrca on 2008-06-24
so what i need to add in GRUB configuration is:
title		Microsoft Windows
rootnoverify	(hd0,5)
savedefault
makeactive
chainloader	+1

let me understand: title means the title it get in the grub menu, root.. means the HardDrive that the operation system is there (where to boot from)
and the others i dont realy understand can you tell me what they are for? i assume that the "savedefault" means that this will be the default boot command.. (windows will boot by default) am i correct?

---

### Post by logos34 on 2008-06-24
sorry for the delayed response...I was troubleshooting my k3b app

yes to all the above...savedefault means grub will boot the last used OS if the 'default' line near top is set to 'saved'  

more[ here]("http://users.bigpond.net.au/hermanzone/p15.htm")

try hd0,1 or hd0,5

*if hd0,5 gives error, take out line 'makeactive'

---

### Post by dinbrca on 2008-06-24
when i try hd0,1 or hd0,5 it tells me error 12: Invalid device requested.
what should i do?

---

### Post by logos34 on 2008-06-24
give me some more details...like in what order ubuntu and windows were installed (or rather in the case of windows, copied), why on a logical partition, etc.  Can you mount windows in ubuntu and access files there?

---

### Post by dinbrca on 2008-06-24
windows was installed first i dont know why logical (i didnt do anything) what is mount? like in daemon tools? (if you know what it is)

---

### Post by logos34 on 2008-06-24
again, are you sure sda6 is system partition, c:\, and not a windows data partition?  (windows cannot be installed on a logical unless there is a prexisting c:\ on a primary partition on which to put the boot files.) Can you mount sda6 and access files?  What do you see? If it is c:\ you should see files like boot.ini, ntdetect.com, ntldr, etc

---

### Post by meierfra. on 2008-06-24
logos34: 
you might want to look at this:
[URL="http://ubuntuforums.org/showthread.php?t=838647#4"]
http://ubuntuforums.org/showthread.php?t=838647#4[/URL]

---

### Post by logos34 on 2008-06-24
> **meierfra. said:**
> logos34: 
you might want to look at this:
[URL="http://ubuntuforums.org/showthread.php?t=838647#4"]
http://ubuntuforums.org/showthread.php?t=838647#4[/URL]

well, that certainly clears up matters and proves what I was saying above.  

dinbrca,

why didn't you mention that thread?  Could have saved a lot of time.  Looks like sda1 had the windows boot files, and its gone.  If so, forget booting windows.  

>  Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04d304d2

   Device Boot      Start         End      Blocks   Id  System
[COLOR=Red]/dev/sda1   *           1         443     3558366    7  HPFS/NTFS[/COLOR]
/dev/sda2             444       38912   309002242+   f  W95 Ext'd (LBA)
/dev/sda5            9139       35246   209712478+   7  HPFS/NTFS
/dev/sda6           35247       38912    29447113+   7  HPFS/NTFS
/dev/sda7             444        8778    66950824+  83  Linux
/dev/sda8            8779        9138     2891668+  82  Linux swap / Solaris

and now after deleting sda1, rearranging/expanding you have 

>  Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04d304d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       38912   312560608+   f  W95 Ext'd (LBA)
/dev/sda5            9139       35246   209712478+  82  Linux swap / Solaris
/dev/sda6           35247       38912    29447113+   7  HPFS/NTFS
/dev/sda7               1        9138    73400890+  83  Linux

Lemme look at the other thread again

---

### Post by dinbrca on 2008-06-24
no no no no 
i formated my pc again because i had this problem and i couldn't find someone to help me so it isnt realy updated..

now..
look.. i am kind of new in linux.. i know how to use the basic commands ++ in the terminal and that a lot because windows cmd.. now i have 3 drives:
1: Linux System- 70GB
2: Games + Softwares (thats why i dual booted)- 200GB
3: Windows System- 30GB
and as i showed you the sudo fdisk -l command gives me the partations table:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04d304d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       38912   312560608+   f  W95 Ext'd (LBA)
/dev/sda5            9139       35246   209712478+  82  Linux swap / Solaris
/dev/sda6           35247       38912    29447113+   7  HPFS/NTFS
/dev/sda7               1        9138    73400890+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   7  HPFS/NTFS

but i didnt realy understood what is the sda2..

---

### Post by logos34 on 2008-06-24
delete--just saw your post

---

### Post by logos34 on 2008-06-24
> **dinbrca said:**
> Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   7  HPFS/NTFS

but i didnt realy understood what is the sda2..

more surprises...you must have truncated the fdisk output in post #3 above, or else this is an external you just plugged in.

So what is it, internal or external hard disk?

Doesn't appear to be a system partition--no boot (*) flag.  But maybe it is for all I know.

For menu.lst entry, try

>  title		Microsoft Windows
rootnoverify	(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader	+1

---

### Post by logos34 on 2008-06-24
> now i have 3 drives:
1: Linux System- 70GB
2: Games + Softwares (thats why i dual booted)- 200GB
3: Windows System- 30GB
and as i showed you the sudo fdisk -l command gives me the partations table:again, if you're saying this is the system partition 
> 
/dev/sda6           35247       38912    29447113+   7  HPFS/NTFS you can no longer boot it because it appears you deleted the partition with the boot files. 
> 
2: Games + Softwares (thats why i dual booted)- 200GBI think that got deleted, unless you copied it to sdb1 beforehand
> 
[COLOR=Red] /dev/sda5            9139       35246   [/COLOR][COLOR=Red]209712478+[/COLOR]   7  HPFS/NTFS[COLOR=Black] --deleted[/COLOR]Based on the info provided, you originally had 3 ntfs partitions (sda1 with boot files) [plus a fourth, sdb1], then stuff happened and you now have one big extended partition, minus sda1 and one of the ntfs partitions.  I recommend backing up files on sda6, shrinking the extended down, making a new primary partition at the end, and reinstalling windows there. Restore grub after that.

---

### Post by dinbrca on 2008-06-24
/dev/sdb1 1 60800 488375968+ 7 HPFS/NTFS:
is an 500gb external HD..
maybe:
/dev/sda6 35247 38912 29447113+ 7 HPFS/NTFS 
doesnt show because i didnt format it when first started windows..

---

### Post by meierfra. on 2008-06-24
Looking at the fdisk

> /dev/sda5 9139 35246 209712478+ 7 HPFS/NTFS
> /dev/sda5 9139 35246 209712478+ 82 Linux swap / Solaris

it seems like your Game and Software partition got formated as "swap".  But this actually does not do much damage. So you might be able to rescue the partition by changing its type to "HPFS/NTFS" and running "chkdsk".  Also your boot problem can be solved, by downloading the boot files from the Web.

logos34 suggestion  to reinstall windows  is   easier and faster.  But if you like, I  can  help you to try  to  rescue  your system.

---

### Post by dinbrca on 2008-06-24
i think i would like to learn.. i like to learn about computers..
with formating i already know..

---

### Post by meierfra. on 2008-06-24
O.k. I'll start writing instruction.

To avoid further damage:

```
sudo swapoff /dev/sda5
```

---

### Post by meierfra. on 2008-06-24
This should allow you to boot into XP:

Step 1) Get the boot files and copy them to your Windows partition:

Download this file: [http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573]("http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573")
and save it to your home folder (/home/your_username). Then 


```
sudo mkdir /Win
sudo mount /dev/sda6 /Win    
cd /Win
sudo tar -xvzf /home/your_username/Archive.tar.gz
ls /Win
```

Make sure   the files "boot.ini", "NTLDR" and "NTDETECT.COM" appear on the list.


Step 2) Edit boot.ini:

```
sudo nano /Win/boot.ini 
```   

Change all "partition(1)" to "partition(2)" 

Save the file.


Step 3) Edit menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```

Use

title XP
rootnoverify (hd0,5)
chainloader +1

for your windows item. Do NOT use "makeactive".

Save the file and reboot. Sometimes this does not work right away and you have to do one more step.

Step 4) Rebuild the Boot sector of the Windows partition:

Install and run "testdisk:

```
sudo apt-get install testdisk

sudo testdisk /dev/sda
```

Press "enter" to "proceed"
Press "enter" to select "intel"
Use the "down arrow" and "enter" to select "advanced"
Use the down error to select the "XP" partition and then "enter" to select "boot"
Use the "right arrow" key and "enter" to select "Rebuild BS"
This might take a while. Once done just follow the instruction on the screen to save the new boot sector and quit testdisk.

Reboot.

( You can delete "Archive.tar.gz" at any time, but I would wait until you successfully booted into XP)

---

### Post by meierfra. on 2008-06-24
To rescue your Games/Software partition:


To change the type of /dev/sda5 to "7"  (HTTP/NTFS), boot into Ubuntu, open a terminal:

```
sudo fdisk /dev/sda
```

Type:

t

5

7

w


Then boot into windows and follow these[ instructions]("http://www.updatexp.com/windows-xp-chkdsk.html") run a file system check on your Games/Software partition.  (Your D: drive ?)

Edit:   I just  tried it myself:  Formated a spare NTFS partition to swap. Changed its type back to "7" and then run "chkdsk".  chkdsk didn't  find any errors and the partition behaved just like normal.  So as long as you didn't use your swap space too much, you should be able to recover your Game/Software partition.

---

### Post by dinbrca on 2008-06-25
ok do you have msn or something?
you said:
Get the boot files and copy them to your Windows partition
you mean to get boot files from my windows cd?.. how they are called?

---

### Post by meierfra. on 2008-06-25
> you mean to get boot files from my windows cd?..


No.  You can download them via the  link in the next line of the instruction.

---

### Post by meierfra. on 2008-06-25
I'm off to the the airport right now and will be without internet for the next few weeks. But  other people in the forum  should be able to answers any questions you might have concerning my instructions.

---

