---
title: "Flash drives not auto-mounting properly"
date: 2017-04-24
forum: General Help
---

### Post by ishmael3 on 2017-04-24
Greetings. Thanks for any help here.
 
 The problem is that suddenly I cannot dependably auto-mount flash drives (FAT16-FAT32) as I have always been able to.  Usually fine but sometimes the following occurs: The drive APPEARS to mount normally (i.e, the icon appears on the sidebar and the drive appears normally in the disks utility as mounted), BUT the content window does not automatically appear and I cannot open the drive or view contents by left-clicking the icon. I CAN still eject the drive normally by rt-clicking and ejecting.  ALSO , whenever this situation occurs  the file manager utility (file cabinet icon) becomes non-functional. Also, I am NOT able to log out of the current account, but CAN shut down normally (after ejecting the drive, of course). Once this starts the same thing happens with every flash inserted. After restart everything seems fine -- flashes mount/read normally again.
 
 The following would seem to be significant:
 Just prior to the first occurrence of this behavior I had bought a new USB-HDD (Seagate Expansion 2-TB portable) to use for backups. I formatted two partitions (one-ext4, another NTFS ). I encountered  some problems mounting/reading this HDD both out-of-the-box and after formatting. (Prior to noticing  the flash drive problem I was planning to request help regarding the Seagate HDD!)
 
 I'm running Ubuntu 16.04 on a machine dedicated to that OS. There are four accounts which I switch between frequently. I have no other problems except as stated here.  
 
 Seems something changed after my attempts to use the Seagate HDD. Can I get flash drives to mount/read normally again? (Or do I need to work on the Seagate issue first??). I don't know where to start. Any help appreciated.

---

### Post by ajgreeny on 2017-04-24
Just to check; have you inserted the USB with those two partitions, into a Windows machine and not ejected it properly from that machine?
If you do that, or even pull the USB after a "normal" Windows shutdown, which is actually hibernation, the NTFS partition will not be available to your Linux machine as it will be flagged as still in use.

I would expect that the FAT32 partition would still be available in Linux, but I just wonder if the fact that there is an unmountable partition on the disk is causing this problem for you.

---

### Post by ishmael3 on 2017-04-24
ajgreeny, thanks for your input.
 
 
 The USB-HDD has never been used with a Windows machine. And was always properly ejected from the Linux machine (if it had mounted).  
 
 
 I intended on not muddying the waters in this thread with details particular to the USB-HDD, but, if it helps: the NTFS partition mounts/functions exactly as it should, HOWEVER the ext4 partition, after its creation, was found to be owned by root and remained owned by root no matter which account was active when the drive was mounted. My plan was to ask for particular help regarding the USB-HDD after solving the flash issue .  
 
 
 I fear confusion between the flash-drive problem, and the different USB-HDD problem, though I realize that the issues are almost certainly related. It seems like there was some systemic change after first attempts to use the USB-HDD (exhibited by subsequent flash behavior) and I was hoping to find and fix that before attempting (again) to deal with the USB-HDD.  
 
 
 I'm hoping someone who knows Linux better than I (i.e., everyone in this community) might spot some pattern in the flash behavior and have an idea what changed.
 
 
 The irony of this is that I was finally getting things in order to set up good, dependable backup system. (sigh!)

---

### Post by ajgreeny on 2017-04-24
Ah!
You mention that one partition was ext4, and it is this that causes your problem as it will be owned by root by default and you need to change the owner to you as user in order to be able to write to it as user.
I am uncertain if it is only this disk with an ext4 partition that is giving you the problem or all other USB disks following your use of that disk.

I suggest that you give the ext4 partition a **Label** using gparted; once you have done that the partition will always mount to the same folder, ie, /media/*username*/*Label*.
Now you will need to mount the partition to that **Label** named folder simply by inserting the USB, then run the command ```
sudo chown -R *username:username* /media/*username*/**Label**
```In future the partition will always mount to that folder which is now owned by you as user and should allow you to write to the partition without a problem.

---

### Post by ishmael3 on 2017-04-24
ajgreeny, thank you again! That's valuable information! I thought I'd done my research regarding formatting drive to ext4 (or not) for backups but found NO reference to any ownership considerations.
 
 I mounted the drive just now to check some points. Seems that merely selecting the icon for the ext4 partition causes buggy, pre-freeze-type behavior (slow, jerky mouse response). Obviously a problem in need of solution.   
 
 I gave the partitions labels when I created them. They are:
 ext4 partition called: "ext4part"
 NTSF partition called: "ntfspart"
 
 Currently when I mount the drive logged in to user acct "cam" both partitions show up as follows:
 [COLOR=#000000] /media/cam/ext4part[/COLOR]
 [COLOR=#000000]/media/cam/ntfspart[/COLOR]
 
 [COLOR=#000000]The "ext4part" folder is owned by "admin01" which is the default administrator account; "ntfspart" is owned by "me." [/COLOR] 
 
 [COLOR=#000000]I have got some learning to do![/COLOR]
 
 [COLOR=#000000]Something I don't understand: Once I, as "cam", become the owner of the "ext4part" folder does that mean I cannot use the drive (the ext4 partition) within other user accounts without having the same problem again?[/COLOR]
 
 [COLOR=#000000]Also: since this drive is meant to be a backup drive, containing disk image and other files, is the ownership issue likely to affect me during some future crisis.[/COLOR]
 
 [COLOR=#000000]Also (if you're still with me):  Should I have just kept it simple and stuck with one, NTFS partition![/COLOR]
 
 [COLOR=#000000]Thank you![/COLOR]

---

### Post by ajgreeny on 2017-04-25
Normally the user with the current working user account, and who is active will, I think, be owner of the ext4part, folder, but that is something I do not know for certain.

It is certainly true of an external disk formatted as ext4 which is moved from machine to machine with different users on each, but it may be down to the UID of both users being 1000 on that machine.

However, there are ways of allowing all users to make use of this partition by giving it the correct permissions, or perhaps better, depending on your security needs, creating a separate subfolder for each user which is owned by them.

Linux ownerships and permissions are extremely flexible and allow you to pretty well do whatever you want if you set them appropriately.

---

### Post by Autodave on 2017-04-25
Making them NTFS is simpler, but may not easily allow you to do what you want with them. If you are only copying data to them for storage or backup, NTFS would be the easiest.

---

### Post by ajgreeny on 2017-04-25
Autodave has a point there, but you may have good reasons for needing or wanting an ext4 partition which we are unaware of.

Having checked the situation re different users on the same machine, they will not be able to write to the ext4 partition by default without using appropriate permissions for it; on a different machine the main user probably will, as he or she will have the same UID of 1000.

---

### Post by ishmael3 on 2017-04-25
[COLOR=#000000]Very interesting information![/COLOR]
 
 [COLOR=#000000]It seems obvious to me now that my most immediate problem is not flash drive behavior, but my misunderstanding of formatting, and permissions and using an external drive for backups.  Since that discussion seems a bit off-topic from my original question I'll call this thread solved having learned some things about ext4 formatting and permissions. Hopefully that info may be useful to someone else as well. [/COLOR] 
 
 [COLOR=#000000]But, talk about irony, I am right back where I started regarding researching best backup procedures. I love Ubuntu, and really appreciate the great support community, but it can be frustrating trying to  find a comprehensive overview of a particular topic. [/COLOR] 
 
 [COLOR=#000000]Thanks very much, ajgreeny and Autodave.[/COLOR]

---

