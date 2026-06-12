---
title: "Linux Driver for &gt;2TB drives that are already formatted by Windows DiscWizard??"
date: 2013-12-12
forum: General Help
---

### Post by heywoodjbm on 2013-12-12
I'm brand new both to Linux and this forum, but I think this is more a general question than a newbie question.

I have a 3TB Seagate internal drive that I've been using on Windows for a while.  My PC doesn't have UEFI, and I needed to boot Windows from the Seagate drive, so I couldn't format it as GPT (Windows doesn't allow booting from a GPT disk with a legacy BIOS).  The only way to see all 3TB was to use Seagate's DiscWizard utility.  Please note that although DiscWizard also has backup functions, my only use for it was the driver it installs that makes a 3TB drive look like two separate drives, one of 2TB and one of about 800GB.  This question has nothing to do with backup.

I just installed Ubuntu 13.10 today, on a different drive.  I'm not using any kind of dual boot scheme, I just pick which drive to boot from with the BIOS.

When I'm in Ubuntu, I can see the 2TB portion of the Seagate drive, but not the 800GB part.  I went to the Seagate website to see if they had a Linux version of DiscWizard, but apparently they don't.   The drive is almost full, so I really, really don't want to reformat it.

So my question is, is there any driver for Ubuntu that will allow me to see the last 800GB of my data, without forcing me to back up all 3TB and reformat it?  

Thank you.

---

### Post by electrohandyman501 on 2013-12-12
Do you still have access to your windows software? I'm thinking an install of Virtual Box, or VMWare. I'm just brain storming here. I don't know either if the DW utility will work in a Virtual machine.
If you can mount/see the seagate drive,(in the virtual machine) you could copy it to a shared folder on the linux drive and then re-partition it for total capacity use. If you are wanting to go away from windows. 

How did you format your linux drive. Is it all ext format? or do you have an NTFS partition.
My thought here, if you can still boot your windows system, you could just copy your data from the seagate drive to the linux data drive.

Sounds like the DiscWizard does nothing more than create a 'virtual' disk and storing the information in a file that the wizard software uses, which is why you can't see it in Linux. I had a similar situation many years ago with connor drive when drive sizes went over 850Mb(yes Mb).
They physical head/sector/cylinder count was beyond the direct reading capacity of the bios, hence the need to 'emulate' or translate the data storage.

---

### Post by heywoodjbm on 2013-12-13
Thanks for your response, but I want to keep the drive intact, because the Windows installation on it is my primary system, and will be for quite a while (I'm on it as I type this).  And it's not feasible for me to copy the data to Linux.  For one thing, the Linux drive isn't big enough.

I'm just experimenting with Linux for now, and I'm afraid the experiment may be cut short if I can't find a solution for this.

---

### Post by deadflowr on 2013-12-13
What program or command are you using to view the drive?

---

### Post by heywoodjbm on 2013-12-13
> **deadflowr said:**
> What program or command are you using to view the drive?

Here's a screenshot of what it looks like in gparted:

[ATTACH=CONFIG]248583[/ATTACH]


By the way, this is almost exactly what it looked like in Windows Disk Management, before the DiscWizard driver is installed.  The NTFS partition is just a normal NTFS data partition, and Ubuntu can read the files on it.  The three partitions marked "unknown" are encrypted with TrueCrypt, including the 32GB Windows system partition, so Linux can't read them unless they are mounted with the correct password, which is what I intended.

But the partition marked "unallocated" is the part of the drive above the 2TB limit that DiscWizard made useable in Windows. Like the part below 2TB, it has a mix of encrypted and NTFS partitions on it --- DiscWizard somehow made an MBR drive able to have 7 primary partitions, because it looks like two physical drives to the OS.  But Ubuntu evidently doesn't know how to handle it without a driver similar to DiscWizard.  My question is, does such a driver exist in the Ubuntu universe?

---

