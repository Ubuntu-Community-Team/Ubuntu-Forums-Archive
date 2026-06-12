---
title: "Avoiding data loss and file corruption?"
date: 2007-04-16
forum: General Help
---

### Post by utkjamie on 2007-04-16
This is not meant to be a rant (even if my frustration comes across as such).

Since I began using Ubuntu/Linux in late January I have had to reinstall the OS 3 times due to file corruption. In order to minimize data loss, I created a separate partition for my /home directory. 

Today I shut down my laptop so I could leave for class and when I tried to boot it while on campus I received FSCK errors on my /home partition. Fortunately, the only files FSCK notified me as having problems were insignificant files that could easily be replaced. So I instructed it to fix them...and now I cannot even boot into my account because apparently a lot more files were destroyed (I'm using my WinXP partition at the moment so I get online).

The reason I don't have very recent backups is because Linux wasn't able to write to my external USB drive because it was NTFS. I had to wipe the backups to free up enough space for me to convert it to FAT32 -- and this recent data loss comes before I could rebuild the backups. But that's a different Linux frustration entirely.

Data loss is the unforgivable sin of an OS -- so what am I missing here? My understanding is that EXT3 is supposed to prevent data loss, yet I've never lost this much data this many times in such a short period of time when I was using Windows 95-XP. What am I doing wrong to have so many crashes and to loss so much data with Linux?

After the second time I lost data I thought maybe the brand new hard drive was faulty, so I ran some diagnostics and nothing came up screwy, so I'm under the assumption the problems I am having are software-related.

Any help is much appreciated for rebuilding my /home directory and preventing further data loss (with a solution better than simply keeping more recent backups in case Linux randomly deletes to corrupt more data).

---

### Post by ahaslam on 2007-04-16
I didn't get on with EXT3 either. I've now used XFS  for over 6 months and don't have a bad word to say about it.

---

### Post by ajgreeny on 2007-04-16
Are you really using kubuntu 4.10 as your info on the post suggests.  If so I would recommend you to get the new version of (k)ubuntu and hope that nothing goes wrong again.  I must say that you seem to have been very unlucky, at least, I presume it's just bad luck, as I've been using various versions of ubuntu/kubuntu for over two years now without a single problem like you have now had several times in three months.

Are you certain you're not doing something odd to cause these problems, or that your hardware is not just at the end of its life?

---

### Post by az on 2007-04-16
EXT2/EXT3 are rock-solid.  That's why they are the default filesystem.

I can't explain your data-loss problems, but it is unlikely that it is software-related.

---

### Post by utkjamie on 2007-04-16
I don't think I'm doing anything out of the ordinary that would cause the problems I've been experiencing (I'm using Kubuntu 6.10). The first two times I ran into data corruption were due to the system freezing up, once during shutdown -- possibly caused by a faulty driver.

After I made my first post, though, I recalled that the files that FSCK identified as corrupted had been copied from WinXP to my /home (EXT3) partition using Ext2FS for Windows. But would that cause the problems I am having?

---

Here's where I am now:

I have backups of my /home directory on DVD from several weeks ago. I booted into recovery mode and used rsync -au to copy only the files from my backups that aren't in the /home directory (for those that might have been corrupted and then deleted by FSCK).

After trying to login, Kubuntu appears to be going through the login process and then returns to the login screen without error. Thinking that this might be a sign of corrupt or missing files in the /home directory I booted into recovery mode again (since trying to login into console mode from the login screen only returns me to the login screen) and then created a new user account. Trying to log into that user account also kicks me back to the login screen without error.

I'm at a loss to make sense of what's going on or how to fix it and I'm a more than a little frustrated at this point.

---

### Post by felix.rommel on 2007-06-19
> **utkjamie said:**
> I don't think I'm doing anything out of the ordinary that would cause the problems I've been experiencing (I'm using Kubuntu 6.10). The first two times I ran into data corruption were due to the system freezing up, once during shutdown -- possibly caused by a faulty driver.

After I made my first post, though, I recalled that the files that FSCK identified as corrupted had been copied from WinXP to my /home (EXT3) partition using Ext2FS for Windows. But would that cause the problems I am having?

---

Here's where I am now:

I have backups of my /home directory on DVD from several weeks ago. I booted into recovery mode and used rsync -au to copy only the files from my backups that aren't in the /home directory (for those that might have been corrupted and then deleted by FSCK).

After trying to login, Kubuntu appears to be going through the login process and then returns to the login screen without error. Thinking that this might be a sign of corrupt or missing files in the /home directory I booted into recovery mode again (since trying to login into console mode from the login screen only returns me to the login screen) and then created a new user account. Trying to log into that user account also kicks me back to the login screen without error.

I'm at a loss to make sense of what's going on or how to fix it and I'm a more than a little frustrated at this point.

What harddisk controller do you have? Is it ATA (old IDE controller) or SATA (new IDE controller)?

I have SATA in my Lenovo Thinkpad Z61m and I had same problems like you! When powering down with off switch of my notebook, some files got corrupted. It destroyed for example my apt database so I wasn't able to install or delete packages any more.

It got worse when I installed Feisty alpha/beta versions for testing - this time it also destroyed data on my home partition! :(

I haven't dived too much into that bug but this is a BLOCKER for me! Sth. like that must not happen and Edgy shouldn't have released in that state. That was a reason for me to change my Linux distribution.

If you still have Edgy 6.10 installed on your system: can you please file a bug report at

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

and post the bug number here so that I can comment it, too? You can add that this bug is a blocker.

You should add thinks like 

/var/log/messages
output of lspci -v
output of fsck

That would be great cause I will never install Edgy 6.10 on my notebook again!

It seems that these data corruption errors were fixed only a few days before Feisty came out. That means with Feisty they should have been gone in case of my problems.

I advice you to make a FRESH installation of FEISTY 7.04! Then your problems should be gone - but without guarantee.

PS: if you already have installed Feisty - are your problems gone?

---

### Post by utkjamie on 2007-06-19
I've not had any problems in Feisty.

While I'm not sure what caused the initial data corruption, I suspect that it may have been writing to my Ext3 partition from Windows using one of the Ext3 drivers available for that OS. The reason I suspect it is that files and directories I had written to from Windows were the ones that took the brunt of the corruption. Since I've stopped writing to the Linux partitions from Windows I've not noticed any corruption problems (but I did lose a lot of data that I hadn't yet backed up).

As far as the login returning me to the login screen...that appears to have been something completely different: I had inadvertently filled up my /home partition. Had Kubuntu simply told me "can't login because there is no disk space," it would have saved me a lot of freaking out to figure out what was going on.

---

### Post by zaffod on 2008-01-24
I have also experienced data loss with Ubuntu (fiesty). 

I posted for help [here]("http://ubuntuforums.org/showthread.php?t=674409") but no bites yet.

---

### Post by fyo on 2008-01-24
> **utkjamie said:**
> The reason I don't have very recent backups is because Linux wasn't able to write to my external USB drive because it was NTFS.

This says to me you AREN'T using 7.10 (Gutsy), although your profile now states that to be the case. 7.10 has full read/write support for NTFS enabled by default.

---

### Post by Herman on 2008-01-24
> I suspect that it may have been writing to my Ext3 partition from Windows using one of the Ext3 drivers available for that OS. The reason I suspect it is that files and directories I had written to from Windows were the ones that took the brunt of the corruption. Since I've stopped writing to the Linux partitions from Windows I've not noticed any corruption problems (but I did lose a lot of data that I hadn't yet backed up). Windows's Ext3 driver has been reported to be suspected of corrupting several Linux ext3 file systems. Probably a lot more go unreported.
Regards, Herman :)

---

### Post by articpenguin on 2008-01-28
> **Herman said:**
> Windows's Ext3 driver has been reported to be suspected of corrupting several Linux ext3 file systems. Probably a lot more go unreported.
Regards, Herman :)


thats because the windows driver converts the ext3 fs to ext2 and if the power goes out there is a chance of data loss as ext2 isnt journaled.

---

