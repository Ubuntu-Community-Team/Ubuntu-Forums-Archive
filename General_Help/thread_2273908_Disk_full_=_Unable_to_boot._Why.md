---
title: "Disk full = Unable to boot. Why???"
date: 2015-04-16
forum: General Help
---

### Post by fkervin on 2015-04-16
Hi all, 

I've experience this a few times, in a xubuntu install, if the system disk get full, system refuses to boot after restart and the only way to repair is booting from a livecd/liveusb, go to the partition and delete files.

I know... we must be carefull and don't let the disk get full, but if we left torrent in the system disk by mistake it can happend. Is there a way to prevent it to happend? I Mean... I way that when disk have only 5 gigabytes free we have an error message and cant continue writing it.

I only want a way to make system most stable and having a way to solve this problem automatically.

Regards

---

### Post by SeijiSensei on 2015-04-16
Start by running "sudo apt-get autoremove" at a terminal prompt.

---

### Post by fkervin on 2015-04-16
> **SeijiSensei said:**
> Start by running "sudo apt-get autoremove" at a terminal prompt.

Many thanks.

As far as I know (please tell me if I'm wrong), it removes packages that are not needed by system, but how does it help me with this issue? I mean, I don't want to free space on the disk, I want operative system to "be smart" and not suicide himself writing more data on the disk than it can support.

Regards

---

### Post by pmi2 on 2015-04-16
> **fkervin said:**
> ...I don't want to free space on the disk, I want operative system to "be smart" and not suicide himself writing more data on the disk than it can support...This is something you have to configure yourself, the OS will not do it out of the box.  

In general, you can set quotas, to prevent a directory like the one where your torrent client stores files from growing too large.

Search the man pages for "quota", or something similar, or rephrase your question and someone (I have not implemented this in Ubuntu), will tell you how.

---

### Post by dragonfly41 on 2015-04-16
setup Crontab? as discussed here .. [http://www.linuxjournal.com/content/tech-tip-send-email-alert-when-your-disk-space-gets-low](http://www.linuxjournal.com/content/tech-tip-send-email-alert-when-your-disk-space-gets-low)

---

### Post by SeijiSensei on 2015-04-16
1) If your torrent client can be configured to allocate the entire amount of space required when the torrent starts up, that can help with your specific problem.  KTorrent has this option, as does Azureus I believe.  I can't find that setting in Transmission though.

2) Buy a big [external hard drive]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100029226%208000%20600030775%20600030803%20600030784&IsNodeId=1&bop=And&ActiveSearchResult=True&Order=PRICE&PageSize=30") and store the torrents there.

---

### Post by Impavidus on 2015-04-16
By default 5% of the disk space is reserved for root (that is, if less than 5% is available, only root is allowed to write). This is just to guarantee enough headroom to boot a system and clear some disk space. I hope you don't run the torrent software as root...?

---

### Post by fkervin on 2015-04-17
Many thanks to all, I use transmission, its included in Xubuntu, and I open it simply from menu.

I've had this problem with a few computers, and it's a pain to fix, much more if I've not phisical access to the computer.

I can warning the computer user to change the path of the download torrents, and ask them to change it to mechanical disk instead of SSD, but you will agree that the best would be making the system not to go to this "no boot" problem.

Further this, the desirable is not only make transmission not to do this, but any program.

The best advice seems to be the one from pmi2, but I want it to be a global solution, not only for one folder.

Hope someone can guide me a bit to a solution.

Regards and thanks

---

### Post by dino99 on 2015-04-17
Linux/ubuntu have some rules for working; and the user have to do with them, not the opposite.

---

### Post by SeijiSensei on 2015-04-17
You can run a system monitor like [logwatch]("https://help.ubuntu.com/community/Logwatch") that will email you status reports every day.  That's not a real-time solution though.

I've run out of space on servers; it's not pleasant.  Most services handle the problem "gracefully;" they just stop functioning.

> I can warning the computer user to change the path of the download torrents, and ask them to change it to mechanical disk instead of SSD

If you have a large physical disk, you should [migrate /home to a partition on that drive](https://help.ubuntu.com/community/Partitioning/Home/Moving) and off the SSD.

---

### Post by fkervin on 2015-04-19
> **9d9 said:**
> Linux/ubuntu have some rules for working; and the user have to do with them, not the opposite.

Many thanks for your answer,

I understand linux have some features that make it not ok for a not advanced user. This problem would not happend with a Windows system since this system is ready to control this problem automatically and doesn't allow the user to completely full the disk and broke the boot. For many or those Linux features it's still a minoritary OS and Windows is the most used system. The truth with this problem is that a "normal" user will not have the  problem using Windows but will with Linux. So Windows is better.

And here, you're going to tell me "use windows", but I don't want to use windows, I want to use Linux, and** I want people to use it**, but I want it to be an user friendly system, I want it to be easy to use and not to require an advanced user that control the free space on the system disk.

You say that Linux is in this way, and if I don't like I don't use. I say Linux nowadays is a great operative system, but with attitudes like yours it will never compete with Windows and will always be "*this system difficult to use, used by freaks that are programmers*".

I think problems like the one I tell in this thread could be easily solved (not by me, of course, I have no idea) and would make Linux a better system, I don't understand why in those situations there are people that excuse Linux like you're doing (it's not the first time it happends to me)

I simply want this system (Linux) to be used by people that doesn't care at all about terminal commands, control free space on system disk and million of other stuff windows makes automatically.

My idea for a better system is this one that one that can be used by a non experienced user. For me, the more bombproof the system is, the better it is. I see you don't agree me. I wan't Linux to be BETTER, I'm sorry my idea of a better system is not the same you have.

Please don't get offended, I simply say what I think.


> **SeijiSensei said:**
> You can run a system monitor like [logwatch]("https://help.ubuntu.com/community/Logwatch") that will email you status reports every day.  That's not a real-time solution though.

I've run out of space on servers; it's not pleasant.  Most services handle the problem "gracefully;" they just stop functioning.



If you have a large physical disk, you should [migrate /home to a partition on that drive]("https://help.ubuntu.com/community/Partitioning/Home/Moving") and off the SSD.

Many thanks, it's a good approach, but not valid always.

Since there is no solution for this, I'll warn the user to change torrent download folder to a big disk and ask them to be carefull with free space, but think those users are users that want the computer to work for them, not opposite.

Regards and many thanks again

---

### Post by leclerc65 on 2015-04-19
In kTorrent you have the setting to point the download files elsewhere, don't know about others

I don't have a separate home folder, but symlink all the sub folders to a separate data partition. The advantage of this approach is:
1- Backup (by Imaging , like Clonezilla) of the system (~5G) is very fast and you don't loose data when doing a system recovery.
2- Distro upgrades or new installs don't affect old data which maybe our most valuable possession of all

---

### Post by Impavidus on 2015-04-19
As I wrote in post #7, by default a non-root process cannot fill the hard drive up to the point where Ubuntu cannot boot any longer, because 5% of the disk space is reserved for root. Either the file system has non-default settings or the program filling it up runs as root. A different problem is that by filling up the drive (as ordinary user) we may no longer be able to login. This is not a boot problem, but a login problem. It can be solved by logging in on the console (ctrl+alt+F2, return to the GUI with ctrl+alt+F7) and deleting some files there.

It's true that Ubuntu can be more difficult to use than Windows. This is the price we pay for freedom. But to those who are capable of using this system, despite its difficulties, this price is naught. Then the lack of freedom on Windows (or Mac, let's not single out one system) turns into a difficulty.

---

