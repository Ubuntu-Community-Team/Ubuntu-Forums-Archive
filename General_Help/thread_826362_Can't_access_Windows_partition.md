---
title: "Can't access Windows partition"
date: 2008-06-11
forum: General Help
---

### Post by Stoodle on 2008-06-11
I've had to reinstall Ubuntu because my uncle messed it up by turning off my computer while it was updating. 

The problems started when I was trying to partition my hard drive. Any ext2 or ext3 partition I made, made the computer whine that there was an incompatible feature. So much for manually partitioning it. I said whatever, maybe I don't need to manually partition it. I'll just keep backing up if there's a problem. I chose guided partition using the free space available.

For a little bit, everything was running fine. After about two restarts, it all fell apart. I was having more bugs than I could count. I figure maybe I should just use windows on that computer for a while or something. Well, I can't access Windows! I'm positive that I didn't delete it because it still shows up in GParted. However, it can't find out any information about it and I can't access any files from Ubuntu. I also can't boot into windows because it forever says "Starting up...". What do I do?

---

### Post by Stoodle on 2008-06-12
So! It turns out I can access my NTFS partition from the Live CD! I just can't actually boot Windows or do it from my internal Ubuntu.

---

### Post by Stoodle on 2008-06-12
Well guys. I'm copying everything from my Windows partition to my hueg (like XBox) external harddrive. My question is what if I wanted to put Windows back on there? I could just recopy the files and use it as normal right?

---

### Post by heatblazer on 2008-06-12
I've had to reinstall Ubuntu because my uncle messed it up by turning off my computer while it was updating. 

Really?! This is some suckin` uncle of yours. Well try to get ntfs-config tool. Search in synaptic.

---

### Post by MaxNorris on 2008-06-12
Not sure how your partitions are laid out, and what exactly you're trying to accomplish.  But, if you're trying to basically just get rid of a Linux install and make it so it'll boot directly into Winders, you could always reinstall the Windows MBR.  (Grub replaces it when you install Ubuntu.)

For XP, you can boot off of an XP install disc, and it should give you an option to boot into a "Recovery Console".  It'll ask for the admin account's password, then dump you in a DOS prompt.  The FixMBR utility will re-built XP's boot sector.  I know Vista has something similar but I forget the exact procedure as I don't own that.. nothing Google won't find though.

That said, simply file copying an Windows installation is usually a crap-shoot at best.  Personally, your best bet if you're really wanting to go back to Windows is to boot off of an Ubuntu LiveCD, and copy the stuff you don't want to lose.  Documents and the like.  Then, do a fresh re-install of Windows.  More of a hassle, yes, but you'll be better off in the long run.  (And just as a side note, I personally wouldn't install SP3.. has a few issues yet.)

---

### Post by MaxNorris on 2008-06-12
> **heatblazer said:**
> Really?! This is some suckin` uncle of yours. 

Heh really.  My family knows my personal system is off limits.  Wife and children can be replaced a lot easier than repairing a borked operating system ;D

---

### Post by Stoodle on 2008-06-12
Well, I was reinstalling because it wouldn't boot up into linux anymore. I upgraded to 8.04 but had so many problems, including not being able to access Windows. I can with the LiveCD (the files at least) so I'm backing up Windows and I'm going to to clear it off the HD I think. However, if I wanted windows back on there, could I just copy the files back on to my HD? The computer didn't come with Windows install CDs (None of them do! Why does everyone suggest using them?).

---

### Post by MaxNorris on 2008-06-12
I had problems myself with 8.04, sticking with 7.10 as on my hardware it works a lot better.. waiting for 8.10 before I try again.

Anywho, you will still need to fix the MBR.  There's no way around that.  You'll need a bootable XP install disc to do this.  Not sure if third party utilities like BootMagic and the like will take care of it.  Either way, even if you copy, reformat, and copy back, you'll still wind up with an unbootable system. 

Your system should have come with some sort of recovery discs too if it was sold "legit".  Reinstalling the OS will give you the cleanest and most reliable solution.

---

### Post by MaxNorris on 2008-06-12
Quick addition.

Never tried this, use at your own risk blah blah.

[Third party MBR repair](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---

