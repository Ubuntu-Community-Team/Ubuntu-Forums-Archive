---
title: "Triple booting Ubuntu, XP, and OS X"
date: 2006-12-16
forum: General Help
---

### Post by escape on 2006-12-16
I have four partition currently on my Thinkpad T43: one has Ubuntu, one has the swap for Ubuntu, one has OS X, and one I want to install XP on. When I try to install XP it says the maximum number of partitions is already being used, so it can't be installed. 

Rather than force XP to work I want to make ubuntu work for it, since ubuntu is a bit more flexible. My question is, do I need a separation partition for the swap?

Thanks.

---

### Post by padre999 on 2006-12-16
I guess extended partition would be the magic word. You can't have more than 4 primary partitions on a hdd.

see [http://www.minix3.org/doc/partitions.html](http://www.minix3.org/doc/partitions.html)

But it looks like it's going to be a major operation... Also I think Windows requests no less than the first partition (not sure though) and will overwrite your MBR, so you will have to reinstall the bootloader afterwards.

On partitioning in Ubuntu see [http://www.ubuntuforums.org/showthread.php?&t=282018](http://www.ubuntuforums.org/showthread.php?&t=282018) and [http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

************

just realized that you don't need more than 4 partitons :oops: 

Can't you asign the free partition to the WinXP Installer? If not it is maybe true that XP likes the first partition. Maybe it would work with hiding the other partitions? Maybe you should find a howto on installing WinXP on another partition. But I didn't install Windows for a long time so I can't say much more on this... [-(

---

### Post by escape on 2006-12-16
[i]I guess extended partition would be the magic word. You can't have more than 4 primary partitions on a hdd.

see [http://www.minix3.org/doc/partitions.html](http://www.minix3.org/doc/partitions.html)[/i]
Interesting. Seems to say MBR supports up to 4 partitions though; I only have 4 partitions. I guess I could install XP one one partition, then use something like partition magic to make partitions for the rest...

*But it looks like it's going to be a major operation... Also I think Windows requests no less than the first partition (not sure though)*
False.

*and will overwrite your MBR, so you will have to reinstall the bootloader afterwards.*
True, which is very annoying...

*Can't you asign the free partition to the WinXP Installer?* 
I do this and XP says there are too many partitions for it too be installed.

*Maybe it would work with hiding the other partitions?*
How would I do this?

*Maybe you should find a howto on installing WinXP on another partition. But I didn't install Windows for a long time so I can't say much more on this... *
I have successfully dual booted Ubuntu with either Win XP and OS X, so I'm ok with dual boot. Just running into problems now. Thank you for your help though.


I'm starting to think I should install XP first, then OS X, then Ubuntu, as that seems to be the order of least to most flexible OS'es.

---

### Post by Sef on 2006-12-16
> then use something like partition magic to make partitions for the rest...

Best not to use PM as it and Linux don't always get along.   Best to either use [GParted]("http://gparted.sourceforge.net/livecd.php") which is on the Live CD, or to get the most recent [GParted]("http://gparted.sourceforge.net/livecd.php") download and burn it.

---

### Post by padre999 on 2006-12-16
> **escape said:**
> 
I'm starting to think I should install XP first, then OS X, then Ubuntu, as that seems to be the order of least to most flexible OS'es.

Well. That would be the "easiest" way to go I guess. But you have already 3 OSs on your system up and running... If there should be a way to get WinXP to install into the free partition it would save you the weekend :-k 

I am not sure if you can hide partitions with Gparted. But I remember that it was possible with Partitionmagic under Windows. But anyway that seems a rather dodgy solution to me, if it should be a solution at all. 
If you change the partition layout on your disk it will probably confuse the already installed OSs. At least in Linux you would have to change the fstab I guess.

---

### Post by padre999 on 2006-12-16
According to [http://support.microsoft.com/?scid=kb%3Ben-us%3B283260&x=9&y=13](http://support.microsoft.com/?scid=kb%3Ben-us%3B283260&x=9&y=13) WinXP needs to format the first partition during setup...

---

### Post by escape on 2006-12-16
^^ That's interesting... I'm positive I had linux as the first two partitions (system and swap) , and Windows last, but who knows.

Also, I mentioned Partition Magic, mostly just because it's well known. I actually use Acronis Disk Director Suite; you can do almost any filesystem (no HFS for mac though...), including linux swap; it's worked well in the past. I'd recommend it if people find gparted somewhat problematic, as I have in the past.

I'm considering wiping this ubuntu partition and swap, as I only reinstalled it a couple days ago, and install XP. From there partition with Acronis to get partitions for ubuntu and swap. That at least would save me the time of reinstalling OS X, which is actually a huge pain to get set up...

Can someone talk a little more about hidden partitions? How does that work? Would they just be hidden for the XP install? How does grub handle it?

Thanks for the help guys!

---

### Post by escape on 2006-12-18
Sorry for double post; just posting to say the above worked--wipe linux, install xp, make room for linux again. Stupid windows...

---

### Post by masinick on 2007-12-13
> **escape said:**
> I have four partition currently on my Thinkpad T43: one has Ubuntu, one has the swap for Ubuntu, one has OS X, and one I want to install XP on. When I try to install XP it says the maximum number of partitions is already being used, so it can't be installed. 

Rather than force XP to work I want to make ubuntu work for it, since ubuntu is a bit more flexible. My question is, do I need a separation partition for the swap?

Thanks.

Sounds like you came up with a solution.  But trashing everything and starting over is a real pain.  Next time try this and see if it works:

Keep one partition for OS X, one partition for Linux, and one partition for swap.  Leave enough room for Windows, but do not add a fourth partition.  Leave the space unpartitioned.  When Windows installs, I believe XP is smart enough to see it.  Older versions of Windows were not smart enough.  When there is available unpartitioned space and at least one primary partition is available, the Windows disk partition program will be able to create a Windows partition for its own use.

---

