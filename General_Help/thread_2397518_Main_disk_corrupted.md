---
title: "Main disk corrupted"
date: 2018-07-30
forum: General Help
---

### Post by julienbonnet on 2018-07-30
Hello,
First of all, sorry for my english, I'm a poor french guy... 
I have a laptop with a single SSD of 256Go with a single partition.
Windows 10 is/was installed.
All my documents are on a NAS except some fresh files & some pictures on the desktop...
After a reboot with an external USB disk connected to the laptop, my main disk crashed.
No more disk in boot option when I start my computer.
I am using Ubuntu on a live USB stick to analyse & to try to solve my problem.
I used Testdisk and here are some results:

[ATTACH=CONFIG]280595[/ATTACH][ATTACH=CONFIG]280596[/ATTACH][ATTACH=CONFIG]280597[/ATTACH][ATTACH=CONFIG]280598[/ATTACH]

I can see some folders/files on some partitions (one of each couple), but not mine, only foldings like recovery...


I analysed also with Intel style disk:
[ATTACH=CONFIG]280599[/ATTACH]

Results of different tests (don't remember which one among gparted and different command I found on the internet...) is I think a partition (the main) disapeared and only 2 (one at the beginning & one at the end) are readible.

I see in testdisk that it is possible to add a partition, but I don't know how to specify it: which cylinders for the beginning and the end one?

Do you have any suggest / tool / solution for me?
I just want to recover my files on the desktop.
Thanks in advance
Julien

---

### Post by oldfred on 2018-07-30
Is drive old MBR(msdos) or newer gpt(GUID)?
Post this, it will in memory convert to gpt if MBR, but do not save if that is the case.

sudo gdisk -l /dev/sda

Hopefully it really is gpt, as then you have a backup partition table. With MBR there is no backup.

---

### Post by TheFu on 2018-07-30
Use Windows tools to recover Windows stuff.  Restoring from a backup would be the easiest by about 1000x.

If you've tried all the Windows stuff and still like pain, you can try these things: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) It won't be easy or fun.

Backups are 1,000,000 times easier.

---

### Post by HermanAB on 2018-07-31
Hmm, a SSD is pretty much binary: It either works, or it doesn't.

So, if your SSD decided to give up the ghost, then I don't have much hope for your data and it may be best to buy a new SSD, rather than try to use it again.  If you don't want to spend much money, buy a smaller SSD and keep your data external on your NAS, as you are doing.

---

### Post by julienbonnet on 2018-07-31
Hello,
thank you for your answers.
It is a GPT disk.
I can't anymore load windows as it is my main & only disk. And I can't remove it from the laptop because it has less than 1 year...

---

### Post by HermanAB on 2018-07-31
Well, you can install on a USB stick or SD card, but it will be much slower than using a proper SSD.

---

### Post by TheFu on 2018-07-31
> **julienbonnet said:**
> Hello,
thank you for your answers.
It is a GPT disk.
I can't anymore load windows as it is my main & only disk. And I can't remove it from the laptop because it has less than 1 year...

MSFT will let you download a trial disk that works for 30 days (at least that long). You can use it to run data recovery stuff inside Windows.

I have no idea what might have corrupted the main disk. From what you've described, I don't see anything that would do that from the Linux side unless you decided to install Linux onto the SSD (or made a mistake trying to install it somewhere else by accident).  We'll never know. 

The best ways I know to deal with running 2 OSes on 1 machine are:
a) use a virtual machine
b) dual boot from SATA or eSATA storage
...
...
...
zzz) Use USB drive

---

### Post by oldfred on 2018-07-31
Does gdisk show anything?

---

### Post by julienbonnet on 2018-07-31
thank you. I have results of boot-repair soft just done, but I can't attach here.
I will try to install win10 on a USB stick, thank you.
Here is the result of sudo gdisk -l /dev/sda


GPT fdisk (gdisk) version 1.0.3

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Warning! Main partition table overlaps the first partition by 33 blocks!
You will need to delete this partition or resize it in another utility.

Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sda: 500118192 sectors, 238.5 GiB
Model: SanDisk SD8SN8U2
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): 15932E9E-826C-0347-A676-D65373560BB6
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 1-sector boundaries
Total free space is 0 sectors (0 bytes)

Number  Start (sector)    End (sector)  Size       Code  Name
   1               1       500118191   238.5 GiB   0700

---

### Post by oldfred on 2018-07-31
That is showing just one large partition that is entire drive. Which does not seem correct.
Was this really your boot disk or just a formatted data drive?

---

### Post by TheFu on 2018-07-31
> **julienbonnet said:**
> thank you. I have results of boot-repair soft just done, but I can't attach here.

Just post the URL it creates, please. That's best for everyone.

---

### Post by julienbonnet on 2018-07-31
> **oldfred said:**
> That is showing just one large partition that is entire drive. Which does not seem correct.
Was this really your boot disk or just a formatted data drive?

It is my boot and only disk in the laptop: just one partition for windows and all the softs. My documents/music/videos are on my NAS and the shortcuts are pointing to the NAS.

---

### Post by julienbonnet on 2018-07-31
Here is the boot-repair URL: [http://paste.ubuntu.com/p/FsWPsPqcxy/](http://paste.ubuntu.com/p/FsWPsPqcxy/)

---

### Post by TheFu on 2018-07-31
> **oldfred said:**
> That is showing just one large partition that is entire drive. Which does not seem correct.
Was this really your boot disk or just a formatted data drive?

Doesn't Windows require EFI boot with GPT disks?  
And doesn't EFI require 2-3 partitions to boot?

---

### Post by oldfred on 2018-07-31
Windows in UEFI boot mode has multiple partitions. 

But there is no UEFI entry to boot Windows which would survive a disk failure unless drive was disconnected (or not seen at all).
And there is still a Windows BIOS mode boot loader in MBR.

It almost looks like OP created one very large partition, not following UEFI and SSD drive requirements for partition alignment, nor typical Windows partition requirements.
And with partitions not aligned that may cause some of the issues.
But I thought all partitioning tools in recent history did it correctly unless you forced partition to be at certain start & end.

 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

### Post by julienbonnet on 2018-08-06
Hello,
some news of my SSD : I did not succeeded to recovered my files with all the tools I used.
So I formated it and I reinstalled Win10.
Thank you for your help and your advices.
Julien

---

