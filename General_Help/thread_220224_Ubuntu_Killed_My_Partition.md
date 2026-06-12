---
title: "Ubuntu Killed My Partition"
date: 2006-07-21
forum: General Help
---

### Post by turkish on 2006-07-21
Last week i get a few disks with Ubuntu/Kubuntu/Edubuntu from your shipment.

Ubuntu/Kubuntu work as a Live-CD and I decide to test it.

I work with it about 15 minutes.

My hard drive is 80 Gb with 2 partitions on NTFS.

First partition is system with Win XP and  the second partition is my file storage.

Before all of trouble free space on first partition was 1.5 Gb and free space on second partition was 248 Mb.

After all my 15 minutes with   Ubuntu/Kubuntu as a Live-CD I reboot my comp and I saw next screen.

Windows run the checkdisk on my second partition an tell me that a MFT index is incorrect.

Also checkdisc tells me: Deleting orphan fragment file #1...N.

I think that windows deleting temporary files after Ubuntu/Kubuntu works but after windows boot I saw that my second partition almost empty.

All my works, photos and other documents just vanished.

69 Gb info was erased L

How could your Live CD work so rude? How could Ubuntu Linux was so unUBUNTU?

Please tell me what can I do now?

---

### Post by ifokkema on 2006-07-21
> **turkish said:**
> Ubuntu/Kubuntu work as a Live-CD and I decide to test it.

I work with it about 15 minutes.
Did you just run the Live CD or install it?

> **turkish said:**
> I think that windows deleting temporary files after Ubuntu/Kubuntu works but after windows boot I saw that my second partition almost empty.
Sorry for the loss of files, but the Live CD does NOT touch your hard drive, unless you tell it to (mount rw, install, etc)...

---

### Post by turkish on 2006-07-21
I'm only run the Live CD. 
There is an option Install\ run Live cd. mayby 512 Mb memory was not enough for Live CD and the system goes to my hard drive and try to have more space on it for work as Live CD?

---

### Post by Mirko Scurk on 2006-07-21
Did you have any signs of problems in windows before you tried ubuntu live cd?
It looks to me like hw (hdd) problem!

---

### Post by turkish on 2006-07-21
No. There was no problem with my drive before this live cd launch.
I'm always knew my drive SMART status, always do defragmentation procedure, and check partition for errors. this drive was OK.
Only one thing. There was just 248 Mb free space on it.

---

### Post by turkish on 2006-07-21
](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Thirsteh on 2006-07-21
The liveCD deleting your harddrive contents is not possible, regardless of lack of RAM or other reasons -- It will attempt to create and fill a RAM-drive with the Operating System, and if it fails, it won't boot, it won't start loading data onto your harddrive.

To be honest, this would be a hard thing to -do- via Linux, you can't just destroy a partition like that, unless you had commenced the install process at some point, if you haven't, I really do believe it's a hardware issue, not Ubuntu.

---

### Post by Sef on 2006-07-21
Here is a data recovery tool:

[Data Recovery]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by 3rdalbum on 2006-07-21
I'm not trying to be rude, but I think your partition had errors weeks before your Ubuntu CD arrived. Did you order them after noticing that Windows was running slower and less stable?

The reason I ask is because I have dreamt about my computer's hard disk crashing just days before it actually happened. I must've subconciously noticed the warning signs.

No live Linux distro puts anything on the hard drive without you actually directing it to. Ubuntu doesn't even mount Windows-formatted partitions by default. I've never even heard of someone losing data after using a Live CD, and 512 RAM is more than enough for a satisfactory experience.

---

### Post by turkish on 2006-07-25
Thank you all :)
As i wrote it before, there was no signes of errors on my hard drive, win rans normally without of anything wrong.
I know that live cd doesn't need to use hdd space for a work, but 
mayby there was a source bug that cause such actions?

---

### Post by turkish on 2006-07-25
It is very intresting but here is another similiar topic on this forum [http://ubuntuforums.org/showthread.php?t=166621](http://ubuntuforums.org/showthread.php?t=166621)

---

### Post by turkish on 2006-07-26
hey UBUNTU creators !!! You'w got somyhing to say?

---

### Post by turkish on 2006-07-27
What ? Here's no reglament at this forum? Where is a canonical ltd technicians? 
Is anybody here?

---

### Post by ifokkema on 2006-07-27
If I read the bug report correctly, it's a bug in the installer which is causing the problems. It seems to crash on some occasions, leaving the disk damaged.

However, you claim not to have touched the installer. Therefor, I see no connection between the mentioned bug report and your situation.

Did you manage to recover any of your files, by the way?

---

### Post by turkish on 2006-07-28
there is istall/run live cd option in the live cd menu if you saw that disks. it's a one option. not two different options.
unfortunately every recovery soft that i tryed to use show me only files that i delete manualy one day before.
so all my needed files is gone. forever  :(

---

### Post by ravindran.k on 2006-07-28
Hi .. 
 
:( sorry of the loss tho..
 
My views on what could have happened:
 
1.You have an NTFS Partition c:.
2. The Live CD mounted the NTFS partition in Read/write mode..
 
Now...
 
Im not sure about #2 as i dont have Ubuntu Live CD. But,  I guess this is possible because I was using another Linux Live CD with My NTFS C: drive and after few days if using the C: in Read/Write mode under Linux, i encountered strange Blue Screen of Deaths in WinXp. Finally, it stopped booting.. However, I could still boot with Linux Live CD  and Backup all my Data on C:..and reinstalled XP. Ofcourse I had run CHDSK many times and it used to fix those.. still was crashing. Very strange.. Maybe u can try the same..
 
All the best!!

---

### Post by turkish on 2006-07-28
:) Thanx
but i do not mount my NTFS drives when i use this live cd.

Sorry for such a bad product like Ubuntu/Kubuntu/ etc. Linux.
I'll will never use it again.
And no one from my friends neither will.

I have just one quastion to Ubuntu developers:
How can you send this distr to us when you allready now that this distr have such a wrong actions?
i claim it like you are just incompetent.

i promise that i raise the ANTIUBUNTU company in the RUnet.

**** this distr!!!

---

