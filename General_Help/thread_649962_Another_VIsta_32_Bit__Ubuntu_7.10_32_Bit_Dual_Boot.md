---
title: "**Another VIsta 32 Bit / Ubuntu 7.10 32 Bit Dual Boot Question...**"
date: 2007-12-25
forum: General Help
---

### Post by TR3GO on 2007-12-25
Hello,

I have Vista already installed on my Samsung 500 GB SATA drive and I have partitions. I have another 80 GB EIDE drive that doesn't have an OS on it.

My problem is that I have installed Ubuntu before, but never dual booted with my new SATA drive. I have read tutorials but they don't seem to work for me. I have shrunk my Vista partition to 10 GBs and planned on installing it on there.

NO LUCK. It won't recognize the partition, it says its "Unusable" & it won't let me change the partition to EXT2 or EXT3. I disconnected my 80 GB EIDE drive and only start with my 500 GB SATA drive and it won't let me follow the tutorial by selecting "Use Largest Continual Space" in the Ubuntu installation.

How can I setup Vista and Ubuntu 7.10 in HARMONY and not lose my Vista installation?

I APPRECIATE ANY HELP!! 

THANK YOU!!

-STEFAN

---

### Post by logos34 on 2007-12-25
Try selecting 'Manual' install option.  Create a 1 GB /swap (primary partition, filesystem 'linux swap') and the remaining ~9 GB or so for root (primary partition, 'ext3').

---

### Post by TR3GO on 2007-12-25
It won't allow me to edit the space I already designated.

---

### Post by logos34 on 2007-12-25
strange...umm, try Gparted on the live cd

>System>Admin>Gnome Partition Editor

try making the new partitions that way and then starting the installation again

---

### Post by dcstar on 2007-12-25
> **TR3GO said:**
> 
...........
How can I setup Vista and Ubuntu 7.10 in HARMONY and not lose my Vista installation?
...........

If you really want a flexible system, I would recommend installing Ubuntu and then installing the **vmware** server package (enable the "partner" repository in Synaptic), and then installing Vista as a virtual machine.

Then you can run Vista (or any Windows, or other Linux distros etc. etc.)  inside Ubuntu and simultaneously use them without having to reboot!!

I have just installed vmware server (the licences are free from the vmware web site) and I can run a 32 bit version of Ubuntu inside vmware which runs on my 64 bit Ubuntu install.

---

### Post by TR3GO on 2007-12-25
I appreciate your input, but I don't want Ubuntu as my primary OS. I would rather virtualize Ubuntu over Vista. But frankly I just want to be able to dual boot Vista and Ubuntu and have the boot loader work and everything else. 

But doesn't seem I can get it to on my SATA drive. Does Ubuntu work on a SATA drive?

I have allocated a 10 GB chunk of space from my Vista partition from the shrink tool under Disk Manager in Vista.

BUT... Ubuntu will not recognize that space as USABLE... It classifies it as UNUSABLE space. I can't change the format to EXT2 or EXT3 what-so-ever. 

Does anyone have any SOLUTIONS to this problem?

Thanks!

---

### Post by logos34 on 2007-12-25
I don't think SATA is the problem here...There's a slight possibility it's a Bios issue with a large drive like that, i.e. can't 'see' the entire disk--and you're trying to make a bootable partition at the end of it.  (Windows can see all of it because it supports 48-bit LBA.)  I know that my own motherboard had a Bios update not too long ago because it couldn't even detect large Maxtor SATA II drives 500 GB or larger.

You could also try the text-mode Alternate install CD.

---

### Post by TR3GO on 2007-12-25
Well I have updated all my BIOS. I have an ASUS A8N-SLI Premium -- and I updated the BIOS just recently. There are BIOS updates for Linux I believe -- but I'll have to look into it.

As for the text based installation -- I'm not sure if i'm that L33t. I've taken a UNIX/Linux fundamentals class at college but I'm not skilled enough yet for a text based installation. But I'll look into finding a tutorial or something.

Do you know about installing Ubuntu with WIBU under Vista? I know it creates an expandable file under the Vista installation. Maybe that would be a considerable option. It's not virutalization either. Do you have any knowledge or experience with this tool?

Thanks for your continual help!
-Stefan

---

### Post by logos34 on 2007-12-25
The text-based alternate cd is easier than you think.  [This page]("http://users.bigpond.net.au/hermanzone/p3.htm") will give you a good idea of what it looks like.  (It looks more complicated than it really is. It's techinically for Feisty but the gutsy version hasn't changed).

Yes, I've tried Wubi--inside XP though.  It might be an option.  I runs from a folder inside windows as a loopmounted file system.  A bit slower though.  But the nice thing is that you can convert it (in theory) using LVPM to a regular ubuntu installation on a dedicated partition.  If you could convert it, that would be great.

add: 
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

---

