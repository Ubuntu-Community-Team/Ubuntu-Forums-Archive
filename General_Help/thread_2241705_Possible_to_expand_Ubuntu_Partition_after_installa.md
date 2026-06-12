---
title: "Possible to expand Ubuntu Partition after installation?"
date: 2014-08-27
forum: General Help
---

### Post by azitizz on 2014-08-27
Im running Win 7 and Ubuntu 12.04. Im plannin on upgrading soon, but I realise Im running out of hard-drive space. I have a large HD but when originally partitioning it I believe I gave more space to Windows than I should have. Can I change this now that its been done at installation?
Thanks for any help.

EDIT: I realised I can do this with gparted with a live USB.

I looked at my partitions, and Im wondering if I messed up somewhere. It looks to me like there a lot of wasted space Im not using, and need. All I want was Ubuntu and Windows, nothing else. I origianlly made them relatively equal in size, but I would like to allot more to Ubuntu and shrink windowns as I use it less and less.
[ATTACH=CONFIG]255894[/ATTACH]

Im almost sure sda6 is Ubuntu. sda2 is windows. But whats sda1 and sda3? Can anyone clarify by looking at this?

Thanks again.

---

### Post by yancek on 2014-08-28
sda1 is a 100MB partition, your windows boot partition and sda3 is an Extended partition.  A primary partition can be used as an Extended partition in which to create logical partitions  and they are numbered beginning with five so your Ubuntu is on a logical partition.  You can boot windows and shrink its partition which is usually safer than using Linux software such as gparted.  Many have used gparted to do it successfully however.  You could then create another Ubuntu partition with the free space for data.  It's also possible to move the Ubuntu partition to the left.  I expect you would have to first move the Extended partition to the left before the Ubuntu logical partition and this would be higher risk since you are moving the location of the boot files.  The first option would definitely be safer.

Definitely back up and important data before changing partitions.

---

### Post by Cliff_Simonds on 2014-08-28
One more thing on shrinking the windows partition: You definitely need to shrink windows partition form windows. If your using a Hdd and [COLOR=#ff0000]not[/COLOR] an SSD then you need to defrag first. Here's how to do it correctly so you won't lose any data or fudge your system files when you shrink: 
1-You'll need a third party defragmenter like defraggler to defragment in safe mode.
2-Use a system cleaner like ccleaner or wise care.
3-Shut off pagefile, system restore and hibernate
4-Reboot
5-Now that your pagefile, system restore and hibernation files are gone, reboot again this time to safe mode. (You'll have to reactivate them when all is finished) They use alot of space and are spread all over the disk.
6-Use your system cleaner once more to delete files that were in use in normal mode.
7-Now defrag your disk using third party defragger and don't forget to [COLOR=#ff0000]consolidate files[/COLOR] (very importment) might even have to do it a couple of times.
8-Now your disk is consolidated you can boot back to normal mode and shrink the windows partition using Disk Management. For shrinking see [this]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/") article at How To Geek.
9-After shrinking your partition turn system restore, pagefile and hibernation (if you use it) back on.
10-Now you can adjust your ubunutu partitions or better yet, I recommend downloading 14.04 and installing that. But be veeery careful expanding an moving the ubuntu and swap partitons to the left, I've done it 4 times. The first two on an Hdd (both times worked like a dream) Twice on an ssd(first work good, the second fudged, and I had to reinstall ubuntu so I could see grub, my laptop is my only computer and I didn't have a boot repair disk. Remember GRUB is now your boot loader.

---

### Post by Atomic Dog on 2014-08-28
[edited] Yea, you do have lots of extra room on the ntfs partition.  There is risk in resizing.  I have done it successfully, and I have had things go wrong.  I have never even defragmented before shrinking, but it would not hurt for sure.  On a personal note I would not run a windows "cleaner" -they are often more trouble than they are worth.

---

### Post by Mark Phelps on 2014-08-28
You have a couple of choices regarding the tool to use to shrink the Windows partition (sda2).  First, you could use Windows Disk Management.  It doesn't provide much flexibility, but it's built-in and will allow you to shrink the OS partition -- it will simply reboot to do that.  Second, you could use the Minitool Partition Wizard Boot CD.  It has more flexibility, but you have to download the ISO file, burn it to CD, and reboot from that CD.

Just be sure NOT to use GParted to do the Windows OS partition shrinkage as doing so risks corrupting the Windows filesystem.

---

### Post by azitizz on 2014-08-30
Thanks all for the advice. I never got the messages until now. I thought I was subscribed for email notifications by default...

So, is my partition setup considered normal for what I want. (rarely used Win 7 and Ubuntu as the only two OS, booted up through Grub) 

Im still not clear on that point despite all the good info shared...

---

### Post by yancek on 2014-08-31
> So, is my partition setup considered normal for what I want. (rarely  used Win 7 and Ubuntu as the only two OS, booted up through Grub) 

Yes it is.  The simplest install is a / (root) partition for the filesystem and a swap partition as you have.  You can always create additional partitions later forr data if you want, preferably using a Live CD of GParted or some other partition manager.

---

### Post by Cliff_Simonds on 2014-08-31
My disk setup is basically like yours, except I have 8 GB swap because I have 8GB ram. My system almost never uses it because I have an ssd and swappiness set to 10 instead of 60. But there are some programs that require swap to function, just like in windows there are programs that require pagefile.. I never set up extra partitions like home or data for ubuntu, I just use Deja Dup Backup tool and backup to an external Hdd. For everything else I let Ubuntu take care of it. This is because, if you make a wrong choice in reinstalling the os, or something goes wrong with a version upgrade those partitions can be fudged. Personally I would shrink windows down to no smaller than 100GB: windows needs room to defragment(a must), plus you'll have space to add any other needed programs in the future, then expand sda3 your extended partition to fill the gap, then adjust sda6 ext4 and maybe give a little more swap space if you have more than 2GB ram. But remember: backup backup and backup before making any partition changes, and with windows make a system image and have your windows system repair disk handy.

---

