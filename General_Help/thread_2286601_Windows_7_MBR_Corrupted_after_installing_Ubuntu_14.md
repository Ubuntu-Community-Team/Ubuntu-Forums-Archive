---
title: "Windows 7 MBR Corrupted after installing Ubuntu 14.04"
date: 2015-07-13
forum: General Help
---

### Post by Mitesh_Manani on 2015-07-13
Hello,

I am new to Ubuntu and had installed it in a 100 GB Partition. My Laptop already had Windows with McAfee Endpoint Protection. 
Ubuntu made a Dual Boot but when i select Windows i cannot boot into it and the system prompts an error saying that Changes by Recent Hardware or Software has caused a failure. 
0xc000000f is the reason for the same. 

When i try to mount the ntfs drive using mount command it gives me below Errors.

NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I have also attached information generated from BootRepair Tool. 

I have checked using fdisk -l and i am able to view the partitions /dev/sda2 and /dev/sda3 as HPFS/NTFS/extFAT

I wanted to know When Ubuntu got installed did it take the whole backup of Current MBR ? 

Also what is the way to correct the bootloader so that the system boots both the OS Correctly. 

Please help.

Regards,
Mitesh

---

### Post by oldfred on 2015-07-13
Do not know McAfee.

But grub totally replaces MBR, with its boot loader. 
Windows has a standard boot loader which you can easily restore.
But often these types of Windows software totally take over the MBR. 
Are partitions also encrypted, as they are shown as NTFS, but cannot be mounted.

Some with these modified Windows systems, just have a separate drive with a full install of Ubuntu, others install to same hard drive, but install grub's MBR to an external drive. But some systems are so security locked that you cannot boot another device.

Does McAfee have a way to recover MBR so you can boot it?
Quick search found this:
[https://kc.mcafee.com/corporate/index?page=content&id=KB61022&actp=null&viewlocale=en_US&showDraft=false&platinum_status=false&locale=en_US](https://kc.mcafee.com/corporate/index?page=content&id=KB61022&actp=null&viewlocale=en_US&showDraft=false&platinum_status=false&locale=en_US)

---

### Post by Mitesh_Manani on 2015-07-13
> **oldfred said:**
> 
But grub totally replaces MBR, with its boot loader. 

I think Ubuntu being such an advanced OS, should have taken backup somewhere. Because, i remember (i aint sure) even installation screen shows Backing up ... something.. before writing MBR. 

Yes, Drives too were encrypted. I have asked my local csd person and he said we'll have to format the drives. :mad: . But im sure there should be a simple solution to this. 
When i inserted the Windows Recovery CD, and went on to startup repair ,  it simply showed D: (0MB) and finally startup underran with some internal Exceptions and asked me to send report. 

i seriously doubt whether i should execute the fixmbr commands. 

This was a Org. (Corporate) Laptop so they have McAfee support but i doubt to what level guys would help. 

As an end user, i would blame mcafee if it cannot recover the data.

---

### Post by oldfred on 2015-07-13
I have seen a lot of suggestions of backing up MBR, and Boot-Repair does just that.

But standard MBRs are so easy to reinstall and that is usually the case, so backup hardly ever needed.

I would think the McAfee recovery might work for you.

If this is now your computer, not corporate any more I might consider undoing McAfee.

---

### Post by Mitesh_Manani on 2015-07-14
> **oldfred said:**
>  I would think the McAfee recovery might work for you. 

Thanks fred for the kind and positive words. Hope Mcaffe recovery is able to get my data back. ! 

Thanks for your time to reply on this problem thread !

---

