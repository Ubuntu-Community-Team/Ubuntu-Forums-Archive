---
title: "Your Choice of Filesystem for Shared Drive"
date: 2007-04-11
forum: General Help
---

### Post by Aikon- on 2007-04-11
I currently have Windows XP installed on one partition and Ubuntu 6.06 installed on another partition of a 40GB system drive.

My /home partition is on a 320GB SATA drive, under LVM, formatted to ext3.

I have a 120GB drive that I want to install for the purpose of sharing files between Windows and Linux. I want your opinion on the best file system to use.

At this time I'm primarily using Linux, and occasionally booting into Windows for things like games, VS.Net development, burning some DVDs etc.

The options I see are:

[LIST]
[*]FAT32 (for easy read-write in both systems)
[*]ext3 (proper operation when running Linux, could be some issues under Windows)
[*]NTFS (proper operation under Windows, could be some issues under Linux)
[/LIST]

Personally I would like to stay away from FAT32 because of the obvious reasons; as for NTFS, I tried **ntfs-3g** a while back (this was last October-ish, so I know there has been recent development) and it caused me to lose most of the data on the NTFS partition (corrupted the files); as for ext3, I've had fairly good experience using **ext2ifs** on Windows in the past, but I'm not sure if there could be other problems that crop up.

So, your input?

---

### Post by Spr0k3t on 2007-04-11
I would go with EXT3 on the shared drive personally.  Even in recent developments with ntfs-3g  I've lost some files.  Sticking with a native file system on your primary operating system would be the best move imho.

---

### Post by Aikon- on 2007-04-11
Just one reply, and he didn't even vote!

---

### Post by SniperSlap on 2007-04-11
Pull files using the operating system and its respective filesystem.

---

### Post by aysiu on 2007-04-11
I voted "other." I don't share any more. Everything's Ubuntu. I just keep Windows around so as not to hurt its feelings.

---

### Post by Aikon- on 2007-04-11
> **SniperSlap said:**
> Pull files using the operating system and its respective filesystem.

I'm not sure I understand what you mean?

---

### Post by energiya on 2007-04-11
If you want to share files between linux and win, use fat32. It's better for both of them.

---

### Post by bg1256 on 2007-04-11
I would lean toward FAT32, because it works well for both.  It's what I do, and I've never had a problem.

However, I also have ntfs3g installed, but not as a primary method for sharing data.

---

### Post by pointone on 2007-04-11
Here's a poll: You have one man who speaks English and French, and another who speaks English and Spanish. These two men need to work on a project together... which is the best approach?

a) Work in Spanish and provide the first man with a Spanish-to-English/French dictionary
b) Work in French and provide the second man with a French-to-English/Spanish dictionary
c) Work in English

---

### Post by Aikon- on 2007-04-11
Here's the problem:

The subject they are discussing could be discussed in either French or Spanish, but there are no appropriate words in English to use..

FAT32 partitions can't be larger than 32GB, and I want to use an entire 120GB drive for this sharing; plus its not inconceivable that I'd want to transfer a DVD image, breaking the 4GB file size barrier.

---

### Post by ElBuscador on 2007-04-11
I have been using Ext2IFS frequently for the last months or so with an internal 400GB SATA drive formatted as a single volume, and an Ext3 partition on my 60GB SATA notebook drive, and have never encountered an issue with it. Just this morning I moved the 400GB drive to an external USB case, and it still seems to work fine but I have only been using it for an hour or so. I realize that does not mean problems can't happen, but so far I have been completely satisfied.

---

### Post by rok3 on 2007-04-12
> **Aikon- said:**
> 

FAT32 partitions can't be larger than 32GB, and I want to use an entire 120GB drive for this sharing; plus its not inconceivable that I'd want to transfer a DVD image, breaking the 4GB file size barrier.

FAT32 partitions can be up to 4 TB.  The partitioner for Windows XP had a 32GB limit set in it.

FAT32 is the only file system that you'll be able to use on everyone's computer.  You can setup your own hardware to use either NTFS or EXT3 on both OSes.  If you really need a max file size larger than 4 GB then I would format it as EXT3 and also create a small FAT32 partition to hold the install files for Ext2 IFS.  That way you could always toss it on any M$ box you need to use.

Hope this helps.

Rob

---

### Post by farscape on 2007-04-12
With my limited experience. I've had no problems with NTFS using smbfs.

---

### Post by Spr0k3t on 2007-04-12
> **Aikon- said:**
> Just one reply, and he didn't even vote!

When I replied, the poll wasn't there.

---

### Post by coxy on 2007-04-12
I don't share partitions between OS' because my desktop is solely Windows which my mum and dad use and I don't touch. My laptop had Windows on until I removed it last night while messing with Debian Etch. When Feisty is released it will be the only OS on my laptop.

If I am sharing files between the OS' on different boxes then I use my file server which is Samba on a JFS file system.

Unless you have files over 4GB then FAT32 should work fine for you. Your other option is buy something old like this:

[http://cgi.ebay.co.uk/INTEL-PENTIUM-3-E-1-0GHZ-384MB-RAM-20GB-HD-COMPUTER-PC_W0QQitemZ230112651638QQihZ013QQcategoryZ179QQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/INTEL-PENTIUM-3-E-1-0GHZ-384MB-RAM-20GB-HD-COMPUTER-PC_W0QQitemZ230112651638QQihZ013QQcategoryZ179QQrdZ1QQcmdZViewItem)

and turn it into a file server. I don't know if that is an option for you, or you would be interested in it but building Linux servers is where I learnt most of the stuff I know.

---

### Post by Aikon- on 2007-04-12
> **Spr0k3t said:**
> When I replied, the poll wasn't there.

No problem, just trying to goad people into voting ;)

---

### Post by hoagie on 2007-04-12
I would go for FAT 32 if I were you. It's the only file system both operating systems can write without messing with third party software. I believe FAT 32 is your best choice,

---

### Post by markp1989 on 2007-08-17
I use NTFS with ntfs-3g  because i dont like the limitations of FAT32, no allowing file sizes to be over 4gb, and even though i have hardly any files over this limit (mostly are hard drive/dvd images).

---

### Post by p_quarles on 2007-08-17
Voted "other" because the only sharing I ever do goes through my fileserver. Samba for Windows access, SSH for for Linux. 

I *do *have NTFS3g installed, but stopped using it a while back.

---

