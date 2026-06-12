---
title: "What is the advantage of separate /home partition"
date: 2012-12-06
forum: General Help
---

### Post by Quazze on 2012-12-06
Hello everyone

I always read that it is good to make a separate /home partition for your documents and that if you make it NTFS you can share it between Linux and Windows in a dual boot.

But what is actually the advantage of this configuration as opposed to where I just keep my documents on my Windows partition and mount that one when working in Ubuntu? (except that you don't loose your documents when formatting the windows partition)

And if I were to make a separate home partition, on which partition would I best locate my (Windows) program files? On the home partition?

thanks in advance
cheers

---

### Post by The Cog on 2012-12-06
Having a separate home partition allows you to reinstall the operating system (including a reformat) without losing all your data. Much the same as keeping all your data on a separate D: drive in windows (I think). In fact, I tend to have two system partitions as well, so I can try out the next version without wiping a known working system, and I share the data partition between them.

---

### Post by Habitual on 2012-12-06
[http://ubuntuforums.org/showthread.php?t=1496609](http://ubuntuforums.org/showthread.php?t=1496609)
[http://ubuntuforums.org/showthread.php?t=1411215](http://ubuntuforums.org/showthread.php?t=1411215)
[http://ubuntuforums.org/showthread.php?t=1854501](http://ubuntuforums.org/showthread.php?t=1854501)

---

### Post by Vaphell on 2012-12-06
separate home means you can reinstall (which means nuking the partition assigned to root /) and have all your files and configuration accessible right off the bat, as if nothing happened. I don't think you can make /home NTFS though, i'd say it has to support native linux permissions which NTFS does not do.
People suggest yet another partition purely for win-linux interaction, let's call it DATA, where your movies music and what not are stored. In such a scenario /home can be very thin and store only gui customizations and program settings.
The general idea is to have system stuff and your personal data on separate partitions, so wiping system doesn't touch your data at all.

If you use windows in your dual boot a lot, the advantage is much smaller because most likely you hold your data in D: accessible from both systems either way (more or less an equivalent of the scenario with DATA partition)
Separate /home (and/or separate DATA) are most useful when linux is your main system and you upgrade a lot, jump distros, tinker, break things and reinstall frequently. You save time you'd otherwise spend on backuping/moving/copying

---

### Post by oldfred on 2012-12-06
You normally keep your Windows programs in Windows, but put data an a shared NTFS data partition. You cannot use NTFS for /home.

I do like to separate system from data, both for Windows & Ubuntu. Then it is easier to upgrade system without messing with data, but your data should be backed up anyway before any system changes.

For new users I suggest the separate /home. And if dual booting with Windows another data partition formatted NTFS for shared data. But once you start putting most data in data partition(s), then a separate /home has less utility. I am back to including /home in my / (root) but have all data in separate data partitions. Once is still NTFS from when dual booting XP and all new data now goes into a shared ext3 (if creating now I would use ext4)  partition.

---

### Post by greatsirkain on 2012-12-06
I did have a separate partition in NTFS (yup, so windows could use it too) then I decided it would be more secure not to. So earlier last week I moved everything. I broke ubuntu a little over an hour ago, using a Ubuntu live USB now and I can't access any of my files. Sometimes I just want to punch myself in the face, really hard.

---

### Post by colin.p on 2012-12-06
> **oldfred said:**
>  But once you start putting most data in data partition(s), then a separate /home has less utility. I am back to including /home in my / (root) but have all data in separate data partitions. 

^^^ Ditto. Even though on this laptop I have a separate "home", by doing regular backups using lucky or grsync it makes it rather redundant as a complete backed up "home" is on another partition or drive anyway.

I had a slight hickup doing a fresh install of 12.04 from 10.04 and keeping my current separate "home" caused some issues. I was able to sort it out but when I did a complete fresh install of xubuntu 12.04,on my desktop (server), I nuked the HD completely and had my home in "/". I just brought any backed up data over, from another drive, and had no issues at all. Turned out to be much faster and easier. So from now on, I won't use a separate "home" as I don't really need it.

---

### Post by C.S.Cameron on 2012-12-07
I agree with Colin.
I upgraded my wife's computer from 10.04 to 12.04 recently.
She did not have a separate home partition so I rsynced her home folder to a new partition on a fresh install using grsync.
It was easy and all is working well.

---

### Post by greatsirkain on 2012-12-07
Well now I've got a clean install of Lubuntu, a partition for my vm's, a windows xp partition and two large NTFS dump partitions along with swaps & I managed to save everything, but only just. All your music/films/games etc should definitely be on a separate NTFS partition, especially if you encrypt your home directory. It just takes too long to replace everything. ;)

---

