---
title: "help adding new sata drive"
date: 2007-09-27
forum: General Help
---

### Post by barmaley on 2007-09-27
Hello, ubuntu people
A simple hard drive upgrade has become a disaster for me.
I've been struggling for several hours trying to add a new sata drive to my comp with a small ide drive having ubuntu on it.
The problem is that neither BIOS nor ubuntu see the sata drive.
I have searched the internet and posts here but nothing helped.
Please, help me with this issue.
I'll appreciate any idea, from jumpers to bios update, etc.
I have Chaintech SK8T800 motherboard (for AMD) and WD 250GB SATA drive.
Thank you in advance.

---

### Post by kidders on 2007-09-28
Hi there,

If your BIOS won't talk to the drive, then nothing else will, I'm afraid.

Your BIOS may be misconfigured, your cabling may be faulty, or the disk itself might be dead ... or incompatible with your motherboard. You could try...
[LIST]
[*]Double-checking that you haven't done something obvious, like disabled SATA support in your BIOS.
[*]Comparing your disk's specs against what your motherboard supports.
[*]Checking/replacing your cabling.[/LIST]My advice would be not to even consider updating your BIOS unless you are _certain_ that your current version has a bug that would prevent you from using your new disk, and the documentation accompanying any upgrade specifically indicates that the issue is addressed. As far as I can make out, your motherboard doesn't have a dual BIOS, so there is no point in needlessly risking bricking your computer.

---

### Post by barmaley on 2007-10-01
Thank you, kidders

I've been trying to solve this problem and that's what I arrived at:
First of all, the hd works,  I've checked it on another MB.

If I connect a smaller SATA hd to my comp, 37 GB instead of 250 GB - everything works fine. The disk is correctly identified by the MB.

If I connect only power to  the bigger SATA hd - it rotates, I can feel it.

When I connect both power and SATA cable - the hd does not even rotate, and thus is not identified.

What do you think about this?

If this has something to do with the MB update, I'm in trouble, since I don't know how to do it, even though I have downloaded some BIOS update from the manufacturer site.

I appreciate your help, thank you very much.

---

### Post by kidders on 2007-10-01
Hey again,

> **barmaley said:**
> If I connect a smaller SATA hd to my comp, 37 GB instead of 250 GB - everything works fine. The disk is correctly identified by the MB.

If I connect only power to  the bigger SATA hd - it rotates, I can feel it.

When I connect both power and SATA cable - the hd does not even rotate, and thus is not identified.Thanks for that extra detail. This is all very odd! Exactly what hard disk do you have?

> **barmaley said:**
> If this has something to do with the MB update, I'm in trouble, since I don't know how to do it, even though I have downloaded some BIOS update from the manufacturer site.An update *might* fix your problem, but as I mentioned before, I would personally be very reluctant to try it, unless I was reasonably sure, because of the risk associated with flashing BIOS. BIOS updates can also introduce new bugs. If you can establish that the update is likely to help, take a look at the instructions provided by your manufacturer. Because of the riskiness of the whole procedure, update instructions are usually quite detailed.

---

### Post by barmaley on 2007-10-01
Thanks, again

The MB is Chaintech SK8T800 (VIA chipset), and HD is WesternDigital SATA 250 GB WD2500KS.

The problem is that Chaintech site provides very poor (underestimate) information on their MB, at least it is so in my case. The manual is also a joke. So, I'm afrraid I have to do more web searching, in order to get some reliable info and, most likely, some guru help, since I'm myself afraid to damage the MB.

I did not expect someone will answer my question, since this is not the right place. I just relied on ubuntu people mercy. It worked ;)

---

### Post by kidders on 2007-10-02
> **barmaley said:**
> The MB is Chaintech SK8T800 (VIA chipset), and HD is WesternDigital SATA 250 GB WD2500KS.As far as I can make out, the SK8T800 doesn't support SATA II. Could that be true?

---

### Post by barmaley on 2007-10-02
That's absolutely correct. But when I bought it I thought it will just work as SATA I. Could it be the reason?

---

### Post by kidders on 2007-10-02
Yes, I'd say that's likely. It's important to make sure your hardware is intercompatible.

Many SATA hard drives have a pair of pins you can cross to switch them to SATA I mode. Hopefully yours is one of them. (Even so, buying an SATA I hard disk in the first place would probably have been cheaper, I suppose.)

---

### Post by barmaley on 2007-10-02
Thank you for the information on jumpers.
This one was cheaper than IDE with 8 MB buffer.
You never know how they sell.

---

### Post by kidders on 2007-10-02
Lol... interesting!

Anyhow, I hope we've found the cause of your problem. Be sure to post back if you can't make the disk work.

---

### Post by barmaley on 2007-10-03
The jumper thing worked!!! Thank you, thank you, thank you.

But I still cannot do with the disk anything.
I got this error during the boot:
Buffer I/O Error on device sda...
It cycles for about 10 min, and then enters the ubuntu.
The disk is in the hardware, but is not seen by the system and is not mounted.
sudo gpared gives the following row
Could not stat device /dev/sda - no such file or directory

I don't know what to do now.
Searching the web did not result into usefull info.
Have no idea. Need help urgently, before I got uncontrolled and make the disk ide manually.

---

### Post by kidders on 2007-10-03
Hmm...

Could you post a little about your disk configuration? For instance, how many hard disks do you have? How are they arranged?

---

### Post by barmaley on 2007-10-04
I have only one hd (60GB, ide) with ubuntu 7.04. It works, but is almost full, so I have decided to upgrade it to a bigger one.
The 2nd hd is the one that I try to connect (250GB, SATAII). This one is problematic.

Yesterday, I've connected it to my wife's comp with Windows2000 (which has one small SATA hd), and there was the following story. The disk was  seen by Win2k, but also was not mounted. It appeared in hardware. I have tried to format it with PartitionMagic, but the program gave some error and could not work. After that I used some smaller programm PTEDIT32 to see and fix the partition table, but also failed. The program sees the disk, it sais that the MBR is bad and could not write the settings which I changed.
I see only two possible explanations:
1) The problem is with the motherboard which does not support SATAII, even though I have shortened the 2 pins in order to make the disk SATAI;
2) The disk itself is somehow corrupted, although it is a brand new.

This is the story.
What's your opinion?
Tell me if you need more details.

---

### Post by dwasifar on 2007-10-04
> **barmaley said:**
> I have only one hd (60GB, ide) with ubuntu 7.04. It works, but is almost full, so I have decided to upgrade it to a bigger one.
The 2nd hd is the one that I try to connect (250GB, SATAII). This one is problematic.

Yesterday, I've connected it to my wife's comp with Windows2000 (which has one small SATA hd), and there was the following story. The disk was  seen by Win2k, but also was not mounted. It appeared in hardware. I have tried to format it with PartitionMagic, but the program gave some error and could not work. After that I used some smaller programm PTEDIT32 to see and fix the partition table, but also failed. The program sees the disk, it sais that the MBR is bad and could not write the settings which I changed.
I see only two possible explanations:
1) The problem is with the motherboard which does not support SATAII, even though I have shortened the 2 pins in order to make the disk SATAI;
2) The disk itself is somehow corrupted, although it is a brand new.

This is the story.
What's your opinion?
Tell me if you need more details.
Does the Win box support SATA II?  If so, did you remove the jumper when you installed it in that box?

---

### Post by kidders on 2007-10-04
What happens when you try to partition it with Linux and set up a filesystem on it?

---

### Post by barmaley on 2007-10-04
The Win box does not support SATAII, I removed the jumper and the motherboard did not recognize the hd, that's why I say that the problem could be due to SATAII.
I tried to format and partition the hd in ubuntu with the help of gparted, but dparted does not see the big hd, it sees only the small one.
If you know how to do it without gparted, I will appreciate you help.

---

### Post by barmaley on 2007-10-12
Hello, ubuntu people
Thanks for those who were trying to help.
There is no SATAII hd now - no problem. I'm back to ide.

---

