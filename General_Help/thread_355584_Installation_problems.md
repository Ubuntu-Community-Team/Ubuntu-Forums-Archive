---
title: "Installation problems"
date: 2007-02-07
forum: General Help
---

### Post by Nick001 on 2007-02-07
For the life of me I can't get the current Ubuntu/Kubuntu installers to work. It's strange because I have used previous versions in the past with no trouble.

The MD5 hashes are OK, and the CDs I've burnt seem fine. The CDs also work reasonably as live CDs (with the occasional glitch). But every time I try to install off them it nixs my Windows install. I get the following error and am unable to boot into Windows:

missing or corrupt <windows root>\system32\hal.dll

Unfortunately, I still need a Windows partition for some things, so it makes Ubuntu unusable for me. One problem is that the current Ubuntu/Kubuntu version, 6.10, won't recognize my wireless card. Again, I have to say it's strange because previous versions of Ubuntu did in the past with no trouble. This alone would mean I'd need to have a Windows partition, if there were nothing else.

But I digress. At the moment I need Windows and can't use an Ubuntu installer that will kill it. I've had to reinstall Windows from scratch twice now - you can't boot off the CD and fix the problems with that hall.dll file (Microsoft's Knowledge Base solution) if you haven't got an install CD, because Microsoft won't let OEMs distribute CDs. (Thank you, Bill, you [unprintable].) And believe me it's no fun reinstalling an OEM version of Windows--it takes, literally, *hours* to clean the OEM "crapware" off, to get updates, to replace dangerous software like Internet Explorer, and generally to get it in a usable state.

So, what's the problem? Does anyone know? I've seen scattered references online to others encountering this problem, but I wonder why it happens.

To be clear: I'm using an OEM version of Windows. It comes pre-installed and the hard drive is partitioned fairly evenly between C: and D:.  I've reinstalled it off recovery discs (DVDs) I've made, as per the OEM's instructions. But I've used Partition Magic to make the layout more sensible: C: (where the OS resides) is now only 15GB, and D: (for data) is around 60GB. I've deleted the "recovery" partition (since restore can be done of the DVDs).

Last time I tried to install Ubuntu I used software - Partition Magic again - to create free space. I partitioned D: and deleted the new partition. Then, when I ran the Ubuntu installer, I told it to install on "the largest continuous free space".

But the install somehow damages or deletes the <windows root>\system32\hal.dll and leaves me with a computer that won't boot into Windows. Is there something pretty damn stupid about the way I'm going about things that I'm missing?

I'd sure like another crack at getting Ubuntu/Kubuntu on there, but I'm dreading the thought of trying, breaking my Windows install, and having to reinstall Windows again. Hours--the pain, the pain. :-)

Thanks in advance for any help or suggestions anyone is able to give.

---

### Post by nickoli_02 on 2007-02-07
Not sure if this would work, but if you have ubuntu already installed on one partition and windows working on another, try just installing grub again so you can boot into ubuntu again. Might work :)

---

### Post by llamakc on 2007-02-07
Are you installing Windows first, Ubuntu second? That way should work. Also, make sure you are installing grub to the MBR of /dev/hda. If you have messed up grub and can boot into neither, 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Nick001 on 2007-02-07
> **llamakc said:**
> Are you installing Windows first, Ubuntu second?

Thanks for your response.

In short, yes, that's exactly what I'm doing. I'm going from a Windows-only installation, creating freespace with Partition Magic, and hoping to put Ubuntu onto the freespace. I'd thought that was a good strategy ... but maybe not.

> That way should work. Also, make sure you are installing grub to the MBR of /dev/hda. If you have messed up grub and can boot into neither

Not sure. I'm letting the installer do what it does. Perhaps that's not a good idea. Or perhaps I should let it take over the whole process and forget about Partition Magic? I had an idea the new Ubuntu installers were quite smart and would look at the hard disk, decide how much space they needed and handle it all. At the same time, I didn't want to risk it.  Any thoughts on that?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)[/QUOTE]

I'm the other way round. I've got Windows up and running and am trying to put Ubuntu (or Kubuntu) on there, too.

At the moment, I'm Windows only and wondering how I can get Ubuntu on there without killing Windows. It's a worry for me because twice before that has happened.

---

### Post by Rich78 on 2007-02-07
I would use something like GParted instead of Partition Magic.  It comes on a Live CD and is very easy to use.

---

### Post by llamakc on 2007-02-07
How many physical hard disks do you have? What are the partitions that exist on the first one (known in Windows as C:\, D:\, etc)?

If you put Windows on C:\ and left space on D:\ as mentioned before for data AND Ubuntu, you would want to partition /dev/hda2 (which was D:\) further. 

Frankly, I recommend windows on C:\ (/dev/hda1), a shared data storage formated as FAT32 on D:\ (/dev/hda2), and then create a third partition at /dev/hda3 for Ubuntu to use.

Is there a way in Partition Magic to copy/paste your current partition scheme? I'm ignorant to how PM works, but every time I install Ubuntu I always seem to be saving data from earlier installs, so I never let Ubuntu just do what it wants when installing: i.e. i always edit the table manually.

If I confused myself above, I'm sure somebody will come by and straighten me out. I'm not too knowledgeable about Windows.

---

### Post by Nick001 on 2007-02-07
> **llamakc said:**
> How many physical hard disks do you have? What are the partitions that exist on the first one (known in Windows as C:\, D:\, etc)?

(1) Just one.

(2) Two partitions: C: and D:

> If you put Windows on C:\ and left space on D:\ as mentioned before for data AND Ubuntu, you would want to partition /dev/hda2 (which was D:\) further.

Except I don't care whether the Ubuntu/Kubuntu install can see the data or not. I'll duplicate the data if need be. It gets too complex for me. All I want is a working Ubuntu install, and a Windows partition to fall back on if I want to use wireless or want to use a Windows program. But when I try for that the Ubuntu installer kills Windows.

> Frankly, I recommend windows on C:\ (/dev/hda1), a shared data storage formated as FAT32 on D:\ (/dev/hda2), and then create a third partition at /dev/hda3 for Ubuntu to use.

Thanks, but that's too complex for me. What concerns me is I can't work an even simpler scheme, and I don't know why.

Anyway, thanks for all your suggestions. I think I'll leave Partition Magic alone and see what the installer will do by istelf if invited to use the defaults. If it screws up, I guess I'll just devote the whole disk to Linux and forgo my wireless.

---

### Post by llamakc on 2007-02-07
Tell the partitioner to install to /dev/hda2 and you'll be all set.

---

### Post by Nick001 on 2007-02-07
OK.

So I allowed the Kubuntu installer to do its thing.

As Arnold would say: Big mistake.

I just let it choose the option:

Resize IDE1 master, partition #5 (hda5) and use freed space

Uh, huh. When I rebooted after installation I got:

*********************

Windows could not start because the following file is missing
or corrupt:
<windows root>\system32\hal.dll
Please re-install a copy of the above file.

*********************


Allow me to restate the problem once more: the current Ubuntu/Kubuntu installers are killing Windows. No one seems to be aware of the fact, and no one seems to be able to tell why they are doing this.


No Partition Magic, no question of blaming things on a third-party product.

The Kubuntu installer screwed up. that's the THIRD time Ubuntu/Kubuntu installers have done that to me.

Now my view is that if you try to do unexpected things with your machine - such as installing an OS it didn't ship with - you only have yourself to blame if things go wrong.

I want to be quite clear: I'm not blaming Canonical for this screw up: I chose to use the installer even after it had failed on my twice before.

However, mark this well: if any loudmouth Linux fanboy starts prancing around on any forum anywhere preening himself and telling all and sundry that "Linux is ready for the desktop" he is telling lies. Use it at your own risk, and don't blame anyone when it doesn't work, but don't tell lies: Don't say it's ready when it isn't.

---

### Post by llamakc on 2007-02-07
I suggested you to TELL the installer which partition to use, namely /dev/hda2 as I posted before, and suggested you make sure that GRUB is installed to the MBR of /dev/hda. These are all things that YOU can control during the install.

Also, why are you not running the Windows installer on the Windows boot cd, agreeing to the EULA (F8) and pressing "r" for repair existing installs? 

The hal.dll errors usually point to bad boot.ini files in Windows.

Here's a way to check it out:

[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

Me? I'd use a liveCD and try editing the boot.ini file to what it should be after remounting the disk from within the LiveCD.

---

### Post by nickoli_02 on 2007-02-07
OK so let me get this straight. Your C: is where your windows partition is (~15GB) and D: is for data, media and the like (~60GB). If you want to install ubuntu on your 60GB partition and keep your data you'll have to resize it, and you'll end up with 3 partitions, one for ubuntu, one for windows and one for data/media. The data/media partition will need to be FAT32 so both windows and linux can read/write. 

So what you want to do is manually edit the partition table in the ubuntu install process. Then you can resize the 60GB partition (keep in mind that the size you enter is the amount you're taking off for the new partition)  and then use the newly freed space.

With regards to linux being ready for the desktop... at least it makes an attempt to accomodate other operating systems on the same machine. When you install windows it says "what the hell is this on the mbr? Oh well I'm just going to overwrite it with my own boot loader so no other OSs can boot".

Linux isn't perfect. When things are going smoothly, it's great. Much better than windows IMO, best spent.... oh, wait, linux is free, forgot :) How much is Vista again? $450 or something?

---

