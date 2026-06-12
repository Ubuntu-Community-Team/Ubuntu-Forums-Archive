---
title: "Deleted Extended Partition 2"
date: 2021-05-21
forum: General Help
---

### Post by slim-j on 2021-05-21
Hi - I am an Ubuntu noob and I just installed on 2 machines.

Once up and running I stupidly deleted a partition on both (!) 120gb ssd's that the OS are on. It showed as extended partition partition 2. Yes, I did this on both machines :oops:

I rebooted one of the machines and it got to the grub screen so clearly i have messed up the OS drive. I hadnt done much with this machine so i just reinstalled from the usb boot.

The other machine is still on and working fine, and i have done plenty on this so dont want to have to reinstall. Is there anyway I can fix this while it is on? I tried some googling and there are some grub commands but this route sounds complicated for me so i would rather fix while it is still on.

Thank you for any help and understanding of my stupidity!

---

### Post by TheFu on 2021-05-21
Probably not.

Do you have a backup of the partition table from before you dumb thing?  BTW, you aren't the first to do this. I'm 100% certain I've done something similar.
What needs to happen is that the old partition table needs to be rewritten exactly as it was. If you cannot do that, then start backing up all the stuff you can and do a reinstall.
Sorry.

If you have a spare HDD that has nothing on it, you could make an image, but this image won't have the partition table and while the data will be there, it won't be organized. Searching through 50 versions of each file **MANUALLY**, when there are 500,000 files, isn't usually worth our time.

Learn from this.

If you have weekly or daily, file-based backups, this would be a minor inconvenience, probably.  I've written here all too much about backups and restores.  It isn't just about failed devices or stupid-user-tricks.  Everyone has done something similar, so don't beat yourself up too badly.  In fact, you can fix the entire MSDOS partition table problem and force GPT with the next install. GPT doesn't use Extended Primary Partitions or Logical partition. GPT supports 128 primary partitions, which is likely to be more than enough.  Just sayin'.

---

### Post by grahammechanical on 2021-05-21
Just to be clear in our understanding. Let us talk about only one machine at a time. How many hard drives do you have in the first machine you are talking about? One or two?

It usually is not possible or at least very difficult to delete partitions that are in use by the operating system. We call it "mounted." We normally run a Ubuntu live session and use a utility called Gparted to create, move, resize and delete partitions with the operating system not in use. So, how did you delete this partition that you say is called extended partition 2?

Another point to note is that Extended partitions were used in the old days when hard drives were partitioned as Master Boot Record (MBR) partitioning. The partitioning scheme allowed an maximum of 4 primary partitions. The way to work around this was to use one of those primary partitions as a special partition called an Extended partition. Inside the Extended partition we could create many Logical partitions.

If the OS was in a logical partition inside the extended partition then deleting the extended partition would remove the OS. Is that the problem that you fixed by re-installing?

As for the second machine. If you did the same to the second machine as to the first, then how is it possible that the OS is still working? It would have been next to impossible to delete the partition the OS was on at the time the OS was running. The fact that the machine is still on indicates to me, at least, that you either had a different set up on the second machine or did things differently with this second machine when compared to the first machine. Or have not given a clear description of what you did and what is wrong.

Please start again. I assume that the first machine is functioning correctly. So, tell us about the second machine. Specifications? Dual booting? UEFI or BIOS motherboard? Version of Ubuntu? Are the SSDs partitioned with MBR partition scheme or GPT (GUID partition table) scheme? How many partitions? What are the partitions used for? And exactly what you did to produce this problem. 

Regards

---

### Post by HermanAB on 2021-05-21
Since you just did the install, I take it that there is nothing important on the machines yet, so reinstalling will be very much quicker than fixing the problem.  You posted the question 2 hours ago, so you could have installed about 4 machines already... :)

---

### Post by oldfred on 2021-05-21
This is now older, so do not know if it still applies or not.

If not rebooted, use fdisk to manually recreate table posts by srs5694 post34 on page#4:
[http://ubuntuforums.org/showthread.php?t=1668247](http://ubuntuforums.org/showthread.php?t=1668247)

---

### Post by garvinrick4 on 2021-05-21
Don't ever feel bad or stupid about asking questions on this forum that is what it is here for. 
We were all where you are now at one time. You will enjoy Ubuntu and the Linux experience.
Dont worry about messing up a partition table while you are learning. 
If you do not have gparted installed then install it 
 > sudo apt install gparted
Learn all there is about gparted lots of links available.
Making partition tables is the first step.  The help before me is sound and you 
will get all the help you need keep asking one day you be helping a new user yourself.
 Enjoy Ubuntu linux slim-j.

---

