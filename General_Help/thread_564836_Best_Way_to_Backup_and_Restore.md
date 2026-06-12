---
title: "Best Way to Backup and Restore"
date: 2007-10-01
forum: General Help
---

### Post by tech9 on 2007-10-01
To backup:

**tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /**

To Restore:

**tar xvpfz backup.tgz -C /**

excluding the boot dir and fstab file will give you the ability to restore all your data/settings on a new partition

Just posting a helpful tip, for all of you out there trying to find a decent backup solution.

Ein Prosit

---

### Post by tech9 on 2007-10-02
sorry, I realized that this should have been posted in the tutorials forum. 

Would a moderator be so kind as to move this thread there?

Thanks!

---

### Post by Nightwalker07 on 2007-10-18
Thanks a lot for giving me the tip about excluding the 'boot' dir, I hope that solves my GRUB problems, will try tomorrow.

---

### Post by shane2peru on 2007-10-19
Thanks for the new Thread!

Shane

---

### Post by tech9 on 2007-10-19
> **shane2peru said:**
> Thanks for the new Thread!

Shane

no problem :)
I want to save some of you the frustration and time spent - with this problem

---

### Post by Nightwalker07 on 2007-10-20
**_My exact testing steps:_**
1. Freshly Installed 7.10 (Gusty-Gibbon-i386-desktop)  on a Laptop.
2. Copied test data to system (600MB / 1,400 files) to both my home dir and desktop. And then installed KTron application (just a small-game to test if it works later).
3. Opened the Terminal and ran the following: ```
cd /
sudo tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
4. I then inserted a USB flash-drive & backed up the 'backup.tgz' and removed the drive.
5. As part of the test I intended to serverly damage the filesystem, so again, still at root on the terminal I ran the following to destroy the system:```
sudo rm -fr *
```
6. Manually powered-off the system.
7. Powered on system and booted with the ubuntu-7.10 disc, and performed a new, fresh installation.
8. Once booted into my new installation I then inserted my USB flash-drive and proceeded to extract/restore my system/files back onto the system drive:
```
sudo tar xvpfz /media/USB-DRIVE/backup.tgz -C /

```
9. Restarted the system and all was restored fine. System & files restored and working. :)

**Thanks a lot for helping me tech9.**

---

### Post by shane2peru on 2007-10-20
> **Nightwalker07 said:**
> **_My exact testing steps:_**
1. Freshly Installed 7.10 (Gusty-Gibbon-i386-desktop)  on a Laptop.
2. Copied test data to system (600MB / 1,400 files) to both my home dir and desktop. And then installed KTron application (just a small-game to test if it works later).
3. Opened the Terminal and ran the following: ```
cd /
sudo tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
4. I then inserted a USB flash-drive & backed up the 'backup.tgz' and removed the drive.
5. As part of the test I intended to serverly damage the filesystem, so again, still at root on the terminal I ran the following to destroy the system:```
sudo rm -fr *
```
6. Manually powered-off the system.
7. Powered on system and booted with the ubuntu-7.10 disc, and performed a new, fresh installation.
8. Once booted into my new installation I then inserted my USB flash-drive and proceeded to extract/restore my system/files back onto the system drive:
```
sudo tar xvpfz /media/USB-DRIVE/backup.tgz -C /

```
9. Restarted the system and all was restored fine. System & files restored and working. :)

**Thanks a lot for helping me tech9.**

Thanks for posting the exact steps.  After destroying the system, and then reinstalling with your 7.10 disc, that is why before it wouldn't boot.  Excluding the boot directory is necessary so that when you restore your data that stuff doesn't get overwritten.  Glad it worked!

Shane

---

### Post by tech9 on 2007-10-25
> **Nightwalker07 said:**
> **_My exact testing steps:_**
1. Freshly Installed 7.10 (Gusty-Gibbon-i386-desktop)  on a Laptop.
2. Copied test data to system (600MB / 1,400 files) to both my home dir and desktop. And then installed KTron application (just a small-game to test if it works later).
3. Opened the Terminal and ran the following: ```
cd /
sudo tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /
```
4. I then inserted a USB flash-drive & backed up the 'backup.tgz' and removed the drive.
5. As part of the test I intended to serverly damage the filesystem, so again, still at root on the terminal I ran the following to destroy the system:```
sudo rm -fr *
```
6. Manually powered-off the system.
7. Powered on system and booted with the ubuntu-7.10 disc, and performed a new, fresh installation.
8. Once booted into my new installation I then inserted my USB flash-drive and proceeded to extract/restore my system/files back onto the system drive:
```
sudo tar xvpfz /media/USB-DRIVE/backup.tgz -C /

```
9. Restarted the system and all was restored fine. System & files restored and working. :)

**Thanks a lot for helping me tech9.**

No Problem Nightwalker07 :)

---

### Post by UK-Wobbie on 2007-10-25
> **tech9 said:**
> To backup:

**tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /**

To Restore:

**tar xvpfz backup.tgz -C /**

excluding the boot dir and fstab file will give you the ability to restore all your data/settings on a new partition

Just posting a helpful tip, for all of you out there trying to find a decent backup solution.

Ein Prosit

Thats top.. I am so going to give that a go thanks :)

---

### Post by filsed on 2007-10-30
Hi all.

I was looking for something like this and I can confirm that this backup procedure works just fine. In my case, it was a project to move my current Gutsy install to new HDD.

Thanks for a great howto! :-)

---

### Post by Nightwalker07 on 2007-10-30
> **filsed said:**
> Hi all.

I was looking for something like this and I can confirm that this backup procedure works just fine. In my case, it was a project to move my current Gutsy install to new HDD.

Thanks for a great howto! :-)Glad it worked well for you. May I enquire how well matured your installation was when you backed-up & restore? Im just interested how many things you had installed etc. I know this backup method works well with relatively fresh installs that I have tested it on, but im pondering if its gona be a reliable method to use with matured systems that have got lots of stuff on, like my MythTV box for example. Let me know if you can, thanks!

---

### Post by tech9 on 2007-10-30
> **filsed said:**
> Hi all.

I was looking for something like this and I can confirm that this backup procedure works just fine. In my case, it was a project to move my current Gutsy install to new HDD.

Thanks for a great howto! :-)

Excellent - No Problem :)

---

### Post by Xealot on 2007-11-01
> **Nightwalker07 said:**
> Glad it worked well for you. May I enquire how well matured your installation was when you backed-up & restore? Im just interested how many things you had installed etc. I know this backup method works well with relatively fresh installs that I have tested it on, but im pondering if its gona be a reliable method to use with matured systems that have got lots of stuff on, like my MythTV box for example. Let me know if you can, thanks!

Given that everything in linux are files, then just making a compressed archive out of your root and unpack it later would work flawlessly as long as your file does not get corrupt.

The only obvious catch is if you are running a software that needs specific hardware, and then you unpack your archive on a different machine than on the one you made your backup on..

but theres nothing a little configuration magic cant solve :)

---

### Post by tech9 on 2007-11-02
> **Xealot said:**
> Given that everything in linux are files, then just making a compressed archive out of your root and unpack it later would work flawlessly as long as your file does not get corrupt.

The only obvious catch is if you are running a software that needs specific hardware, and then you unpack your archive on a different machine than on the one you made your backup on..

but theres nothing a little configuration magic cant solve :)

same goes for backing up corrupt files through any other type of backup mechanism

---

### Post by Nightwalker07 on 2007-11-03
Well here goes... **hard-drive failure!** yes thats right, my matured MythTV box has had a HDD failure :( So im gona get to test this for real now. Thankfully I have backup.tgz file from just four days ago, so I hope this method will perform :???: The only hardware that will change will be the hard-drive that has failed and was holding the filesystem, so all should be good 	[-o<

---

### Post by Nightwalker07 on 2007-11-03
Im **extremely** happy to report this method has saved my butt for the first time! My 300GB filesystem drive died, good old clicking-of-death :(

I grabbed another spare 120GB off the shelf and restore it with my backup.tgz
I was worried that the difference in the sizes of disk's might cause some trouble, but it didnt. The only thing that didnt work straight off the bat was that my slave drive (500GB SATA drive containing all my media) wasnt mounted at /var/lib/mythtv as it normall would be, then I remembered this backup method excludes the /etc/fstab (and hence no automated disk mounting at startup) solved that in a minute.

Everything's back to normal and the wife's got her media center back! few!

---

### Post by drs305 on 2007-11-03
If you have partitions mounted under /media do you need to unmount them before running this scipt? Does the script copy everything under root, including anything in the /media directory?

If so, what would happen when you restore the file and the partitions aren't there or aren't mounted?

Thanks.

---

### Post by dvase on 2007-11-03
Could someone comment on their experience with the final size of the *.tgz backup file?   I would like to do a backup of my own system, however I am quite limited right now on available disk space.  Thus, I am concerned about the method's compression ability.  FYI: My system takes up about 10 GB.

---

### Post by georges023 on 2007-11-03
Thank you very much for the great tut ;)

---

### Post by Nightwalker07 on 2007-11-03
> **dvase said:**
> Could someone comment on their experience with the final size of the *.tgz backup file?   I would like to do a backup of my own system, however I am quite limited right now on available disk space.  Thus, I am concerned about the method's compression ability.  FYI: My system takes up about 10 GB.My 'backup.tgz' was a ubuntu 7.04 installation, roughly 100,000 files in the filesystem, 3.1GB prior to being archived, **1.27GB** when finished.

---

### Post by dvase on 2007-11-03
> **Nightwalker07 said:**
> My 'backup.tgz' was a ubuntu 7.04 installation, roughly 100,000 files in the filesystem, 3.1GB prior to being archived, **1.27GB** when finished.

Thanks for the info.  I took the plunge and my 'backup.tgz' file ended up being about 4 GB, not bad for a 10 GB system!

EDIT:  I ran into the 4 GB limit of FAT32 with my first attempt, the final and successful attempt was closer to 6 GB.

---

### Post by tech9 on 2007-11-05
> **Nightwalker07 said:**
> Im **extremely** happy to report this method has saved my butt for the first time! My 300GB filesystem drive died, good old clicking-of-death :(

I grabbed another spare 120GB off the shelf and restore it with my backup.tgz
I was worried that the difference in the sizes of disk's might cause some trouble, but it didnt. The only thing that didnt work straight off the bat was that my slave drive (500GB SATA drive containing all my media) wasnt mounted at /var/lib/mythtv as it normall would be, then I remembered this backup method excludes the /etc/fstab (and hence no automated disk mounting at startup) solved that in a minute.

Everything's back to normal and the wife's got her media center back! few!

Excellent!:guitar:

---

### Post by tech9 on 2007-11-05
> **georges023 said:**
> Thank you very much for the great tut ;)

no problem!:)

---

### Post by wlc3069 on 2007-11-16
just used this to change from a dual boot with xp to reformat and use ubuntu as my entire disk, and it worked flawlessly. Thank you very much for the tutorial

---

### Post by tech9 on 2007-11-16
> **wlc3069 said:**
> just used this to change from a dual boot with xp to reformat and use ubuntu as my entire disk, and it worked flawlessly. Thank you very much for the tutorial

fantastic! your welcome :)

---

### Post by emarti on 2007-11-18
I'll be try this backup & restore ubuntu 7.10 gutsy with clear setup. If operation is unsuccessfully, I will write this topic. Thanks from Turkey.

---

### Post by tech9 on 2007-11-19
> **emarti said:**
> I'll be try this backup & restore ubuntu 7.10 gutsy with clear setup. If operation is unsuccessfully, I will write this topic. Thanks from Turkey.

It works for me and many others

good luck!

---

### Post by atulkakrana on 2007-11-28
My 80 GB HDD is divided into three partitions....in C partition...I have done everything required for ubuntu 7.10...I mean two ext3 partitions and one swap.....But rest of two partitions are FAT32....used by me when i was on XP....now i dont have XP ( shifted completly to ubuntu 7.10) but i use the data stored on these two partitions i.e song movies pictures and all....I wish to restore my  ubuntu installation...its matured completely...So tat i dont need to setup drivers nd applications .....

QUE1- i just want to restore ubuntu and not other two fat 32 partions mounted in media? 

QUE2- Wat will happen to those two fat 32 partitions when I m going to restore Ubuntu sometime?

---

### Post by ruibernardo on 2007-11-28
Did not tested this and it seems very simple and fine, except for three things:

Why is /boot excluded? It seems to me that if /boot is excluded from the backup, if the system is trashed, there will be no grub menu on boot and no kernel images to boot from.

Why not exclude /media instead? This way there will be no backup from cdroms on the drive and mounted partitions that you don't want to backup.

Why exclude /etc/fstab?

---

### Post by tech9 on 2007-11-29
> **epimeteo said:**
> Did not tested this and it seems very simple and fine, except for three things:

Why is /boot excluded? It seems to me that if /boot is excluded from the backup, if the system is trashed, there will be no grub menu on boot and no kernel images to boot from.

Why not exclude /media instead? This way there will be no backup from cdroms on the drive and mounted partitions that you don't want to backup.

Why exclude /etc/fstab?

The reason for excluding /boot and fstab is that when you completely rebuild ubuntu and wipe your existing partitions and create partitions the UUIDs are different - which could result in errors loading GRUB

---

### Post by ruibernardo on 2007-11-29
Ok for fstab, but the user can use the command "blkid" to check the new UUIDs.

If a user completely trashes the system, not restoring /boot will make the system not bootable. I wouldn't exclude it.

---

### Post by tech9 on 2007-11-29
> **epimeteo said:**
> Ok for fstab, but the user can use the command "blkid" to check the new UUIDs.

If a user completely trashes the system, not restoring /boot will make the system not bootable. I wouldn't exclude it.

what's the difference? :-#
If a user completely trashes the system, one should just rebuild from scratch (clean build) and restore from there... the /boot will be there from the clean build. ;)

---

### Post by ruibernardo on 2007-11-29
> **tech9 said:**
> what's the difference? :-#
If a user completely trashes the system, one should just rebuild from scratch (clean build) and restore from there... the /boot will be there from the clean build. ;)
Ok, I suppose it works that way, although a new install will not have the updated kernel and modules that are already on the backup (I can see many things that will not work from the restored files with a new install - compiled modules for wireless and other drivers and related stuff, etc).

To be constructive, here is an alternative to save the new installation and fixes time. It implies that you did backup /boot and /etc/fstab. Then:[INDENT]- Using a LiveCD, restore the backup on the partition(s);
- Run "blkid" on a terminal. Then edit the file /etc/fstab in the restored / partition and update the UUIDs;
- Run grub-install as described [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0") from the LiveCD to restore the system to a bootable state (MBR).
[/INDENT]Did not tested this but it should work. If there is an error please someone correct it so no bad surprises appears in the worst case scenario (trashed and unbootable system).

---

### Post by tech9 on 2007-11-29
> **epimeteo said:**
> Ok, I suppose it works that way, although a new install will not have the updated kernel and modules that are already on the backup (I can see many things that will not work from the restored files with a new install - compiled modules for wireless and other drivers and related stuff, etc).

To be constructive, here is an alternative to save the new installation and fixes time. It implies that you did backup /boot and /etc/fstab. Then:[INDENT]- Using a LiveCD, restore the backup on the partition(s);
- Run "blkid" on a terminal. Then edit the file /etc/fstab in the restored / partition and update the UUIDs;
- Run grub-install as described [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0") from the LiveCD to restore the system to a bootable state (MBR).
[/INDENT]Did not tested this but it should work. If there is an error please someone correct it so no bad surprises appears in the worst case scenario (trashed and unbootable system).

As far as the updated kernel and modules go, just run the update manager...

Please provide an in depth reason why you think many that things won't work from the restored files with a new install as far as compiled modules for wireless and other drivers go.

no offense, but your alternative method seems tedious / monotonous :-?

---

### Post by gnelson on 2007-11-29
I'm still cutting my teeth on linux, so forgive me if some of these questions are basic or way off base.

I recently added a large (320GB) USB external hard drive for the purpose of baking up my ubuntu server.

I'd like to have an automated, 3 day rotating backup to the external drive.  Could that be done by creating 3 scripts and a cron job for each one?  The script would delete the previous backup file and write the new one using the OP's tar command.  Or is there a better way?

---

### Post by tech9 on 2007-11-29
> **gnelson said:**
> I'm still cutting my teeth on linux, so forgive me if some of these questions are basic or way off base.

I recently added a large (320GB) USB external hard drive for the purpose of baking up my ubuntu server.

I'd like to have an automated, 3 day rotating backup to the external drive.  Could that be done by creating 3 scripts and a cron job for each one?  The script would delete the previous backup file and write the new one using the OP's tar command.  Or is there a better way?

yes, this can be done... and I think your best bet is to create one cron script and set it up to run every three days/ deleting your prior backup.

---

### Post by ruibernardo on 2007-11-29
> **tech9 said:**
> As far as the updated kernel and modules go, just run the update manager...

Please provide an in depth reason why you think many that things won't work from the restored files with a new install as far as compiled modules for wireless and other drivers go.

no offense, but your alternative method seems tedious / monotonous :-?
A simple and usual scenario: John installed Ubuntu. After his first reboot he got the usual icon telling him that he has 100 updates to download with a kernel update in the middle. It happens a lot. He updates and reboots again.

After the second reboot with the new kernel, John installs the restricted modules and installs the driver for his ATI/nvidia graphic card and his wireless card - please note that this kind of thing happens all the time.

John makes the backup without /boot included.  A week after John trashes his system. 

John makes a fresh install (30 minutes or so) and restores the files from the backup without /boot.

When John reboots, the first thing that will happen is that xorg will complain that he cant start with the "actual" configuration - he can't run the update-manager! John spends more 10 minutes to set xorg to boot with the vesa/vga driver - it happens all the time on notebooks.

When finally John gets gnome to start, he finds that his wireless is not working as well as his graphic card. John has to plug the computer to his network and run the update-manager - another 10/15 minutes to download the updates, and again the new kernel. Another reboot with a new kernel, a new backup.

John trashes again his system 2 days after. John has to 
repeat all over.

Mary makes a backup after the updates.  Mary backed up /boot and /fstab. Mary trashes her system. Mary formats her partitions. Mary boots from a LiveCD, restores the system, updates the UUID's and runs grub-install. Mary reboots. End of story.

Of course these were "worst case scenarios" and Murphys Law says that things like that never happens...;)

No offence taken, I liked the simple way you backup the system, just wanted to help to make it better and save some work to who might use it.

---

### Post by gnelson on 2007-11-29
> **tech9 said:**
> yes, this can be done... and I think your best bet is to create one cron script and set it up to run every three days/ deleting your prior backup.
But how would I keep the 2 prior backups?

---

### Post by tech9 on 2007-11-29
> **epimeteo said:**
> A simple and usual scenario: John installed Ubuntu. After his first reboot he got the usual icon telling him that he has 100 updates to download with a kernel update in the middle. It happens a lot. He updates and reboots again.

After the second reboot with the new kernel, John installs the restricted modules and installs the driver for his ATI/nvidia graphic card and his wireless card - please note that this kind of thing happens all the time.

John makes the backup without /boot included.  A week after John trashes his system. 

John makes a fresh install (30 minutes or so) and restores the files from the backup without /boot.

When John reboots, the first thing that will happen is that xorg will complain that he cant start with the "actual" configuration - he can't run the update-manager! John spends more 10 minutes to set xorg to boot with the vesa/vga driver - it happens all the time on notebooks.

When finally John gets gnome to start, he finds that his wireless is not working as well as his graphic card. John has to plug the computer to his network and run the update-manager - another 10/15 minutes to download the updates, and again the new kernel. Another reboot with a new kernel, a new backup.

John trashes again his system 2 days after. John has to 
repeat all over.

Mary makes a backup after the updates.  Mary backed up /boot and /fstab. Mary trashes her system. Mary formats her partitions. Mary boots from a LiveCD, restores the system, updates the UUID's and runs grub-install. Mary reboots. End of story.

Of course these were "worst case scenarios" and Murphys Law says that things like that never happens...;)

No offence taken, I liked the simple way you backup the system, just wanted to help to make it better and save some work to who might use it.

nice scenarios...

I guess "to each his own" 

All I know is that I have tried backing everything up then having to modify the UUIDs and messing with grub was too much hassle for me.

---

### Post by ruibernardo on 2007-11-29
As you can see, updating the UUIDs and re-installing GRUB might save you time, trouble and downloads, but as you say "to each his own".

---

### Post by tech9 on 2007-11-30
> **epimeteo said:**
> As you can see, updating the UUIDs and re-installing GRUB might save you time, trouble and downloads, but as you say "to each his own".

when I can find some time in my busy schedule... I will try your method and see if it is truly a time saver.

---

### Post by holyowned on 2007-11-30
Where does it back up to?  And how do I change this to back up to a thumbdrive?
TIA

---

### Post by tech9 on 2007-11-30
> **holyowned said:**
> Where does it back up to?  And how do I change this to back up to a thumbdrive?
TIA

to your home directory
you can copy and paste the backup to your thumbdrive

---

### Post by ayenack on 2007-11-30
Maybe you could suggest that the user install all updates on their system after the fresh install before doing the restore. This in most cases will avoid any issues as long as no new updates have come down the tube and their system was up to date in the first place.

---

### Post by tech9 on 2007-11-30
> **ayenack said:**
> Maybe you could suggest that the user install all updates on their system after the fresh install before doing the restore.

This should be a given, as basics to ubuntu :!:

---

### Post by lswest on 2007-11-30
both ways seem to do the trick, however the original process mentioned here is better if you actually want to continually (e.g. use a cron script) create backups, or if you want to back up a system, after the /boot/ folder has gone awry (happened to me once, too many OSes on my laptop:P  (XP, Vista, Ubuntu)) and it just got rather confused (ended up installing grub and just restoring system settings, and getting rid of XP as it didn't work on the laptop due to driver problems).  However both methods look like they'd work just fine.  Personally i prefer fixing problems without having to clean install and restoring backups ;) but hey, nice work.

---

### Post by tech9 on 2007-11-30
> **lswest said:**
> both ways seem to do the trick, however the original process mentioned here is better if you actually want to continually (e.g. use a cron script) create backups, or if you want to back up a system, after the /boot/ folder has gone awry (happened to me once, too many OSes on my laptop:P  (XP, Vista, Ubuntu)) and it just got rather confused (ended up installing grub and just restoring system settings, and getting rid of XP as it didn't work on the laptop due to driver problems).  However both methods look like they'd work just fine.  Personally i prefer fixing problems without having to clean install and restoring backups ;) but hey, nice work.

Thanks!

I agree about fixing a problem before resorting to this kind of restore. This is more for disaster recovery - and good point about my method working better if you want to automate the process with cron jobs. :)

---

### Post by ayenack on 2007-11-30
> **tech9 said:**
> This should be a given, as basics to ubuntu :!:

Your correct it should. Maybe you could have mentioned it in your previous exchanges with epimeteo. There are a lot of new users who would not know whether installing the updates would be the correct thing to do or not.

Edit: Just noticed you did. My mistake.

---

### Post by tech9 on 2007-12-03
> **ayenack said:**
> Your correct it should. Maybe you could have mentioned it in your previous exchanges with epimeteo. There are a lot of new users who would not know whether installing the updates would be the correct thing to do or not.

Edit: Just noticed you did. My mistake.

No problem... Happy Holidays!

---

### Post by GaryAndersonMissed on 2007-12-04
I used this backup method and was presented with this error....

mdadm: No devices listed in conf file were found.


I assume this has something to do with Feisty?

---

### Post by Nightwalker07 on 2007-12-04
I've used this backup process fine on both Feisty & Gusty. Maybe the more knowledgeable will enlighten us with a solution to your problem.

---

### Post by GaryAndersonMissed on 2007-12-05
My apologies.  It would seem that I did not exclude boot in my backup command.  This caused issues.

Now I have some xorg issues, but this is to be expected with moving to new hardware.

---

### Post by tech9 on 2007-12-05
> **GaryAndersonMissed said:**
> My apologies.  It would seem that I did not exclude boot in my backup command.  This caused issues.

Now I have some xorg issues, but this is to be expected with moving to new hardware.

detail is everything :)
I am glad that you got it working though.

---

### Post by evets on 2007-12-05
Wow! I wished I had seen this 3 days ago.  I made a nice mess of things that I, now, have to clean up.

But, you can bet I have it copied and saved. LOL


Thanks for taking the time to help us all.

tschuess

---

### Post by tech9 on 2007-12-05
> **evets said:**
> Wow! I wished I had seen this 3 days ago.  I made a nice mess of things that I, now, have to clean up.

But, you can bet I have it copied and saved. LOL


Thanks for taking the time to help us all.

tschuess

No Problem! :)

Glad I could help!

---

### Post by evets on 2007-12-06
> **tech9 said:**
> No Problem! :)

Glad I could help!

I'm runnging your backup sequence now. I notice a few lines going by that say access denied. Should I have run this in the root terminal or use sudo?

thanks

---

### Post by tech9 on 2007-12-07
> **evets said:**
> I'm runnging your backup sequence now. I notice a few lines going by that say access denied. Should I have run this in the root terminal or use sudo?

thanks

yes, use sudo... and I found that when you run the restore, it works best when actually using the root account. I know this is not recommended, but this would be the only time I utilize the root account.

---

### Post by FakeOutdoorsman on 2007-12-07
What are the advantages of backing up using your method over partimage or gparted?

[Howto: Backup with Partimage]("http://ubuntuforums.org/showthread.php?t=287522") [ubuntuforums.org]
[Using PartImage in Ubuntu]("http://www.psychocats.net/ubuntu/partimage") [psychocats.net]
[Copy and Paste your Entire Hard Drive with Two Clicks with GParted]("http://lifehacker.com/software/backup-utilities/copy-and-paste-your-entire-hard-drive-with-two-clicks-with-gparted-296850.php") [lifehacker.com]
[Partition and Image Your Hard Drive with the System Rescue CD]("http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php") [lifehacker.com]

---

### Post by Nightwalker07 on 2007-12-07
> **FakeOutdoorsman said:**
> What are the advantages of backing up using your method over partimage or gparted?

[Howto: Backup with Partimage]("http://ubuntuforums.org/showthread.php?t=287522") [ubuntuforums.org]
[Using PartImage in Ubuntu]("http://www.psychocats.net/ubuntu/partimage") [psychocats.net]
[Copy and Paste your Entire Hard Drive with Two Clicks with GParted]("http://lifehacker.com/software/backup-utilities/copy-and-paste-your-entire-hard-drive-with-two-clicks-with-gparted-296850.php") [lifehacker.com]
[Partition and Image Your Hard Drive with the System Rescue CD]("http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php") [lifehacker.com]Its dam fast, easier, built in, easy to verify or open backups on other system, nice and compact packages.

---

### Post by davidallan on 2007-12-07
So let me get this straight.

This script backups up everything? Programs/ X settings / the lot?

Will it work if the hardware changes like motherboard? could i create a replica system by backing up then restoring on another pc? will it create new unique machine identifiers ?

sorry if these questions are obvious but im new to Linux - windows for 10+yrs!

Thanks

---

### Post by davidallan on 2007-12-07
also. if this script is ran from the console say in the users home folder. will the script also be backing up the backup file just created??

thanks

---

### Post by davidallan on 2007-12-07
i've just got this error while backing up. i think its because it was backing up itself ??


/etc/pango/
/etc/pango/pangox.aliases
/etc/pnm2ppa.conf
/vmlinuz
tar: Error exit delayed from previous errors

---

### Post by Nightwalker07 on 2007-12-08
Actually look at the command itself a bit harder for your answers, you'll see it excludes numerous things, like the backup.tgz file itself and certain directories. Before running the backup command move to the root of your filesystem ```
cd /
```

Then use sudo when you run the command (running it as root).

Yes it backs up near enough everything! If you want to see what excludes; once again refer to the command itself and it shows you clearly what it excludes.

Its not designed for you to be able to change serious hardware like the motherboard, I doubt very much it'd work unless the motherboard was a very close model. You can swap out hard-drives, and probably other smaller parts of hardware. Most complete filesystem/state backup techniques will not handle change of serious hardware for a new restore, its because the operating system customises itself around the hardware in your system. If you then take a backup of that custom OS, and then try to restore it on another completely different PC/hardware, it wont work.

---

### Post by davidallan on 2007-12-08
thanks for the reply. It didnt say to move to the root dir. I did look and the command and yes its obvious that it excludes its self (looks like from the root /) however one of the replies in the post he says its created in your home folder. so i was just running the command from there and i could see it backing up itself.

i'll try again anyways. and thanks again for the reply :)

---

### Post by tech9 on 2007-12-18
> **FakeOutdoorsman said:**
> What are the advantages of backing up using your method over partimage or gparted?

[Howto: Backup with Partimage]("http://ubuntuforums.org/showthread.php?t=287522") [ubuntuforums.org]
[Using PartImage in Ubuntu]("http://www.psychocats.net/ubuntu/partimage") [psychocats.net]
[Copy and Paste your Entire Hard Drive with Two Clicks with GParted]("http://lifehacker.com/software/backup-utilities/copy-and-paste-your-entire-hard-drive-with-two-clicks-with-gparted-296850.php") [lifehacker.com]
[Partition and Image Your Hard Drive with the System Rescue CD]("http://lifehacker.com/software/geek-to-live/partition-and-image-your-hard-drive-with-the-system-rescue-cd-292972.php") [lifehacker.com]

I would say that this is another alternative to partimage... also if you do not have another partition to backup to, this solution works well.

---

### Post by tech9 on 2007-12-18
> **Nightwalker07 said:**
> Its dam fast, easier, built in, easy to verify or open backups on other system, nice and compact packages.

Thanks Nightwalker07 :)

---

### Post by tech9 on 2007-12-18
> **davidallan said:**
> thanks for the reply. It didnt say to move to the root dir. I did look and the command and yes its obvious that it excludes its self (looks like from the root /) however one of the replies in the post he says its created in your home folder. so i was just running the command from there and i could see it backing up itself.

i'll try again anyways. and thanks again for the reply :)

sorry for the delay in response...

Yes, sorry, I should have mentioned that when you backup and restore the backup file will reside in the home dir, or for restoring moved to the root home dir. 

One more thing, I should have mentioned is that this command just creates and restores a backup. You have to manually manage the backup file, but I suppose you could throw this command into a script and then move the backup or delete when creating a new backup.

---

### Post by lvleph on 2007-12-18
I attempted to do this and needed it. Of course, it failed.

```
cd /media/external
tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/media --exclude=/home --exclude=/sys /
```
Some explanation to my excludes. My / partition is only 10GB, so I can't back up in that file system without filling it. I have a seperate partition for home with 45GB of music on it, so I want that backed up in a different way. I could have just excluded just the Music folder. I excluded the /media folder because that is where my external hd was and I don't want to back that up. When I tried to restore my system, it failed with some error referring to the symbolic link in /. Something about date being in the future. I was able to open the backup.tgz with archive manager in the LiveCD and get some important data from it, but... Any clue to why this happened? Because I am planning on breaking my system again, but would like to figure this out before I do that.

---

### Post by psusi on 2007-12-18
> **lvleph said:**
> I attempted to do this and needed it. Of course, it failed.

```
cd /media/external
tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/media --exclude=/home --exclude=/sys /
```
Some explanation to my excludes. My / partition is only 10GB, so I can't back up in that file system without filling it. I have a seperate partition for home with 45GB of music on it, so I want that backed up in a different way. I could have just excluded just the Music folder. I excluded the /media folder because that is where my external hd was and I don't want to back that up. When I tried to restore my system, it failed with some error referring to the symbolic link in /. Something about date being in the future. I was able to open the backup.tgz with archive manager in the LiveCD and get some important data from it, but... Any clue to why this happened? Because I am planning on breaking my system again, but would like to figure this out before I do that.

Sounds like your clock was wrong and tar complained that the file it was trying to extract was supposedly created in the future.  How exactly did you try to restore it?  Just cd / ; sudo tar xzf backup.tgz?

---

### Post by psusi on 2007-12-18
> **Nightwalker07 said:**
> Actually look at the command itself a bit harder for your answers, you'll see it excludes numerous things, like the backup.tgz file itself and certain directories. Before running the backup command move to the root of your filesystem ```
cd /
```

Then use sudo when you run the command (running it as root).

Yes it backs up near enough everything! If you want to see what excludes; once again refer to the command itself and it shows you clearly what it excludes.

Its not designed for you to be able to change serious hardware like the motherboard, I doubt very much it'd work unless the motherboard was a very close model. You can swap out hard-drives, and probably other smaller parts of hardware. Most complete filesystem/state backup techniques will not handle change of serious hardware for a new restore, its because the operating system customises itself around the hardware in your system. If you then take a backup of that custom OS, and then try to restore it on another completely different PC/hardware, it wont work.

It will work just fine; this isn't windows 98 ;)

The only issues you are likely to run into are getting Xwindows working again if you change video cards, and you might have to reconfigure grub/fstab to boot if the disk configuration changes.  Those are the only hardware related configurations stored on the disk -- everything else is plug and play.

---

### Post by tech9 on 2007-12-18
> **psusi said:**
> Sounds like your clock was wrong and tar complained that the file it was trying to extract was supposedly created in the future.  How exactly did you try to restore it?  Just cd / ; sudo tar xzf backup.tgz?

I agree...
try cd / to the tar file or manually move the file to the home dir

---

### Post by lvleph on 2007-12-18
> **psusi said:**
> Sounds like your clock was wrong and tar complained that the file it was trying to extract was supposedly created in the future.  How exactly did you try to restore it?  Just cd / ; sudo tar xzf backup.tgz?

probably due to trying to restore from the LiveCD.
But then again it didn't complete the restore after I had reinstalled my system.
I was moving partitions around and deleting partitions.
What I tried to do was fix GRUB and then restore all from the LiveCD. I fixed GRUB, but then Ubuntu would lock during startup. I ended up starting from scratch.

I am confused why the backup.tgz would be created in the home directory though. Can someone explain this to me.

---

### Post by psusi on 2007-12-18
> **lvleph said:**
> 
I am confused why the backup.tgz would be created in the home directory though. Can someone explain this to me.

Because you were in your home directory when you made it and didn't specify an absolute path.

---

### Post by lvleph on 2007-12-18
Okay, that is what I thought. And since I was not in the home folder, obviously that is not where it would have been made. So I wasn't confused, but I was. lol

---

### Post by tech9 on 2007-12-26
> **psusi said:**
> Because you were in your home directory when you made it and didn't specify an absolute path.

This is correct... by default when you launch the terminal... you are in you home dir...

type ls to view all files and you can verify that this is the location that you want to back up to.

---

### Post by garret on 2007-12-26
Just wanted to bring your attention to a nice new backup solution that I am involved with. It is a 100% open source solution called RESTORE. It can be found at [http://restore-backup.com](http://restore-backup.com). Worth a look.

---

### Post by tech9 on 2007-12-27
> **garret said:**
> Just wanted to bring your attention to a nice new backup solution that I am involved with. It is a 100% open source solution called RESTORE. It can be found at [http://restore-backup.com](http://restore-backup.com). Worth a look.

cool! I will try this. I am going to download the ISO later. I will let you know what I think. Definitely worth a look :)

So does this backup the entire hard drive cluster-by-cluster?

---

### Post by Green_Star on 2007-12-27
> **gnelson said:**
> But how would I keep the 2 prior backups?

I also using this kind of backup process. My machine backs up my entire root directory to a folder called 'backup' on every sunday morning 4am. after successful process of backup it deletes the files which are older than 15days from the 'backup' folder. that means at any time i will have two backups. the following example scripts may help you to implement your plan on backups.

[http://www.unix.com/unix-dummies-questions-answers/21322-find-files-older-than-5-days-remove-tem-after-listing.html](http://www.unix.com/unix-dummies-questions-answers/21322-find-files-older-than-5-days-remove-tem-after-listing.html)
[http://www.unix.com/shell-programming-scripting/4012-listing-files-older-than-2-months.html](http://www.unix.com/shell-programming-scripting/4012-listing-files-older-than-2-months.html)

---

### Post by rmores on 2007-12-27
I have made a bash script (still new at this) to backup using this method.

It comes in different flavours:

WIth or Without /boot and /etc/fstab
A simple /home backup (using bzip)

Reasons:

- I havent tested recovering from both methods, but I will tomorrow under VMs

- My Home folder tends to be quite larger than the other folders, and it's usually non-critical files that tend to be updated not-so-often, so by excluding the home folder from the original backup, I can genenerate faster/smaller system backups to use when I ruin my system :lolflag:

It should be pretty straightforward to use, so if anyone's interested in looking at the code I can post it. 

Also, a link as to how I can post files in this board would be helpful. 
*First post here*

---

### Post by lvleph on 2007-12-27
To attach files you need to be in the advanced post view; in there you will see a paper clip, click that and it should be obvious.

---

### Post by garret on 2007-12-27
> **tech9 said:**
> cool! I will try this. I am going to download the ISO later. I will let you know what I think. Definitely worth a look :)

So does this backup the entire hard drive cluster-by-cluster?

No, it's file level. It does handle diffs well though, has complex scheduling and revision control.

---

### Post by cdtech on 2008-01-09
Just wanted to add my 2 cents. I've been using this script for some time now to back up my home server as well as my laptop. Using cron to run on a specific day and time, the script knows what method to run. I've also included the do and don't backup files that the script searches for.

I have a 4G USB stick I leave on the server (where cron is executed), and with all the server data (LAMP), I use probably 1G per month of space. I mount the USB drive "ro" so if there is a server crash, the backup data is not effected, then mount "rw" through the script for backup.

This will also create a text file, listing all of the app's installed and clean out the local repository.

If you decide to give this a try please look over the do and don't files to see if thats what you want. The only other thing is the mount point for your backup medium.

I hope that I have been of some help for someone.


```
#!/bin/bash

# -----------------------------------------------------------------------
# Script written by Robert Crosby cdtech@comcast.net. This backup routine
# will create the directory and create a full, incremental and a monthly
# backup of selected directories using tar.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
# ----------------------------------------------------------------------

# -------------------------------------------------
# Set Variables:
# -------------------------------------------------

BACKUPPART=/backup
DIRECTORYNAME=`date +%m-%d-%y`"_backup"
MONTHLYDIRNAME=`date +%B`"-01-"`date +%Y`
MONTHLYLINK="monthly"
CURRENTLINK="current"
FULLBACKUPLABLE="Full backup of server on"`date +%B%e,%Y`
MONTHLYBACKUPNAME=`date +%B-%d-%Y`"_full.tar.gz"
FULLBACKUPNAME=`date +%Y-%m-%d`"_full.tar.gz"
MONTHLYBACKUPLOGNAME=`date +%B-%d-%Y`"_full.log"
FULLBACKUPLOGNAME=`date +%Y-%m-%d`"_full.log"
INCREMENTALBACKUPLABEL="Incremental Backup of server on "`date +%B%e,%Y`
INCREMENTALBACKUPNAME=`date +%Y-%m-%d`"_incremental"`date +%H%M`".tar.gz"
INCREMENTALBACKUPLOGNAME=`date +%Y-%m-%d`"_incremental"`date +%H%M`".log"

# -------------------------------------------------
# Functions:
# -------------------------------------------------

monthlybackup()
{

	# we need to be sure to set the partition to read-write.

	   echo -n "Remounting backup partition to read-write...."

	if ( mount $BACKUPPART -o remount,rw &> /dev/null ) then
	
	   echo "done"
	   else
	   echo "Failed to remount $BACKUPPART in read-write mode!"
	   echo "Aborting Monthly system backup"
	
	exit 1

	fi # end if statement

	# now create the backup directory
	# for the first day of the month

	   test ! -e $BACKUPPART/$MONTHLYDIRNAME
	   echo "Creating $BACKUPPART/$MONTHLYDIRNAME directory...."
	   mkdir $BACKUPPART/$MONTHLYDIRNAME

	# now the link to this directory
	   echo "updating the link to the current month....."
	   rm $BACKUPPART/$MONTHLYLINK
	   ln -s $BACKUPPART/$MONTHLYDIRNAME $BACKUPPART/$MONTHLYLINK

	# now the backup

	   echo "Running tar..."
	   tar --create --label "$FULLBACKUPLABEL" --files-from /etc/backup-scripts/do-backup --exclude-from /etc/backup-scripts/dont-backup --ignore-failed-read --absolute-names --verbose --gzip --file $BACKUPPART/$MONTHLYLINK/$FULLBACKUPNAME > $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPLOGNAME 2>&1 gzip $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPLOGNAME
	   gzip $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPLOGNAME
	   echo "Done creating $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPNAME"
	   echo "to view the log file, type:"
	   echo "zcat $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPLOGNAME.gz"

	# be sure to reset the partition to read-only

	   echo -n "Remounting backup partition read-only...."
	if ( mount $BACKUPPART -o remount,ro &> /dev/null ) then
	   echo "Done"
	else
	   echo "Failed to remount $BACKUPPART partition in read-only mode!"
	   echo "Aborting Monthly backup"
	   exit 1
	fi # end if statement
}

fullbackup()
{

	# set partition to read-write.
	
	   echo -n "Remounting backup partition to read-write...."

	if ( mount $BACKUPPART -o remount,rw &> /dev/null ) then
	
	   echo "done"
	   else
	   echo "Failed to remount $BACKUPPART in read-write mode!"
	   echo "Aborting Full system backup"
	
	exit 1

	fi # end if statement

	# now create the backup directory
	
	   test ! -e $BACKUPPART/$DIRECTORYNAME
	   echo "Creating $BACKUPPART/$DIRECTORYNAME directory...."
	   mkdir $BACKUPPART/$DIRECTORYNAME
	
	# now the link to this directory
	   
	   echo "updating the link to the current date....."
	   rm $BACKUPPART/$CURRENTLINK
	   ln -s $BACKUPPART/$DIRECTORYNAME $BACKUPPART/$CURRENTLINK

	# now we need to create a variable for the last full backup
	   
	   echo "Updating $BACKUPPART/$CURRENTLINK/lastfullbackupdate"
	   date > $BACKUPPART/$CURRENTLINK/lastfullbackupdate
	   
	# now the backup

	   echo "Running tar..."
	   tar --create --label "$FULLBACKUPLABEL" --files-from /etc/backup-scripts/do-backup --exclude-from /etc/backup-scripts/dont-backup --ignore-failed-read --absolute-names --verbose --gzip --file $BACKUPPART/$CURRENTLINK/$FULLBACKUPNAME > $BACKUPPART/$CURRENTLINK/$FULLBACKUPLOGNAME 2>&1 gzip $BACKUPPART/$CURRENTLINK/$FULLBACKUPLOGNAME
	   gzip $BACKUPPART/$CURRENTLINK/$FULLBACKUPLOGNAME
	   echo "Done creating $BACKUPPART/$CURRENTLINK/$FULLBACKUPNAME"
	   echo "to view the full backup log file, type:"
	   echo "zcat $BACKUPPART/$CURRENTLINK/$FULLBACKUPLOGNAME.gz"

	# make a list of all packages installed.
	  dpkg --get-selections > $BACKUPPART/$CURRENTLINK/selections

	# clean out the local repository of retrieved package files
	  apt-get clean
	   
	# remount partition to read-only

	  echo -n "Remounting backup partition read-only...."
	if ( mount $BACKUPPART -o remount,ro &> /dev/null ) then
	  echo "Done"
	else
	  echo "Failed to remount $BACKUPPART in read-only mode!"
	  echo "Aborting Full backup"
	  exit 1
	fi # end if statement

}

incrementalbackup()
{

	# mount partition to read-write	   

	   echo -n "Remounting backup partition read-write ... "
	if ( mount $BACKUPPART -o remount,rw &> /dev/null ) then
	   echo "done."
	   else
	   echo "Failed to remount $BACKUPPART in read-write mode!"
	   echo "Aborting Incremental System Backup."
	   exit 1
	fi # end if statement

	# create variable with date of last full backup
	   lastfullbackupdatevar=`cat $BACKUPPART/$CURRENTLINK/lastfullbackupdate`

	# check for existence of incremental backup

	if test -e "$BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPNAME"; then
	   echo "Please wait a minute and try again."
	else
	# create incremental backup
	   echo "Running tar..."
	   tar --create --label "$INCREMENTALBACKUPLABEL" --files-from /etc/backup-scripts/do-backup --exclude-from /etc/backup-scripts/dont-backup --ignore-failed-read --newer "$lastfullbackupdatevar" --absolute-names --verbose --gzip --file $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPNAME > $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPLOGNAME 2>&1
	   gzip $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPLOGNAME
	   echo "Done. Created $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPNAME"
	   echo "To view the incremental log, type:"
	   echo "zcat $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPLOGNAME.gz"

	fi # end if statement

	   echo -n "Remounting backup partition read-only ... "
	if ( mount $BACKUPPART -o remount,ro &> /dev/null ) then
	   echo "done."
	   else
	   echo "Failed to remount $BACKUPPART in read-only mode!"
	   echo "Aborting Incremental Backup."
	   exit 1
	fi # end if statement

}

# --------------------------------------------------
# main routine:
# --------------------------------------------------

	# perform the backup.
	   echo "---------- Backup Script Running... ----------"

	if test `date +%A` = "Sunday" && ! -e "$BACKUPPART/$DIRECTORYNAME"; then

	# if it's Sunday and you havent done a full backup, do so
	   echo "Performing Full Weekly Backup..."
	   fullbackup;

	elif test ! -e $BACKUPPART/$CURRENTLINK/*full.tar.gz; then

	# if there is no current fullbackup, make one now
	   echo "No Current Full Backup - Performing Full Backup Now..."
	   fullbackup;

	else

	# otherwise, do an incremental backup
	   echo "Performing Incremental Backup..."
	   incrementalbackup;

	fi # end if statement

	if test ! -e $BACKUPPART/$MONTHLYDIRNAME/*full.tar.gz; then

	# if there is no current Monthly Backup, make one now
	   echo "No Monthly Full Backup - Performing Monthly Backup Now..."
	   monthlybackup;
	fi # end if statement
	   echo "---------- Backup Script Finished ----------"

```

**do-backup :**

```
/boot
/etc
/home
/root
/usr/local
/var
/downloads
/scripts

```

**dont-backup :**

```
*.mp3
*.mpg
*.avi
*.wav
*.mov
*.asf
*.rm
*.iso
*.flac
*.zip
*.exe
data.bin
/cdrom
/usr/local/fonts
/usr/local/games
/usr/local/j2re
/usr/local/j2re1.4.0
/usr/local/winbackup
/var/cache/apt/archives
/media
/mnt
/backup
/dev
/var/lock
/var/run
/tmp
/var/tmp

```

---

### Post by tech9 on 2008-01-09
> **cdtech said:**
> Just wanted to add my 2 cents. I've been using this script for some time now to back up my home server as well as my laptop. Using cron to run on a specific day and time, the script knows what method to run. I've also included the do and don't backup files that the script searches for.

I have a 4G USB stick I leave on the server (where cron is executed), and with all the server data (LAMP), I use probably 1G per month of space. I mount the USB drive "ro" so if there is a server crash, the backup data is not effected, then mount "rw" through the script for backup.

This will also create a text file, listing all of the app's installed and clean out the local repository.

If you decide to give this a try please look over the do and don't files to see if thats what you want. The only other thing is the mount point for your backup medium.

I hope that I have been of some help for someone.


```
#!/bin/bash

# -----------------------------------------------------------------------
# Script written by Robert Crosby cdtech@comcast.net. This backup routine
# will create the directory and create a full, incremental and a monthly
# backup of selected directories using tar.
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
# ----------------------------------------------------------------------

# -------------------------------------------------
# Set Variables:
# -------------------------------------------------

BACKUPPART=/backup
DIRECTORYNAME=`date +%m-%d-%y`"_backup"
MONTHLYDIRNAME=`date +%B`"-01-"`date +%Y`
MONTHLYLINK="monthly"
CURRENTLINK="current"
FULLBACKUPLABLE="Full backup of server on"`date +%B%e,%Y`
MONTHLYBACKUPNAME=`date +%B-%d-%Y`"_full.tar.gz"
FULLBACKUPNAME=`date +%Y-%m-%d`"_full.tar.gz"
MONTHLYBACKUPLOGNAME=`date +%B-%d-%Y`"_full.log"
FULLBACKUPLOGNAME=`date +%Y-%m-%d`"_full.log"
INCREMENTALBACKUPLABEL="Incremental Backup of server on "`date +%B%e,%Y`
INCREMENTALBACKUPNAME=`date +%Y-%m-%d`"_incremental"`date +%H%M`".tar.gz"
INCREMENTALBACKUPLOGNAME=`date +%Y-%m-%d`"_incremental"`date +%H%M`".log"

# -------------------------------------------------
# Functions:
# -------------------------------------------------

monthlybackup()
{

    # we need to be sure to set the partition to read-write.

       echo -n "Remounting backup partition to read-write...."

    if ( mount $BACKUPPART -o remount,rw &> /dev/null ) then
    
       echo "done"
       else
       echo "Failed to remount $BACKUPPART in read-write mode!"
       echo "Aborting Monthly system backup"
    
    exit 1

    fi # end if statement

    # now create the backup directory
    # for the first day of the month

       test ! -e $BACKUPPART/$MONTHLYDIRNAME
       echo "Creating $BACKUPPART/$MONTHLYDIRNAME directory...."
       mkdir $BACKUPPART/$MONTHLYDIRNAME

    # now the link to this directory
       echo "updating the link to the current month....."
       rm $BACKUPPART/$MONTHLYLINK
       ln -s $BACKUPPART/$MONTHLYDIRNAME $BACKUPPART/$MONTHLYLINK

    # now the backup

       echo "Running tar..."
       tar --create --label "$FULLBACKUPLABEL" --files-from /etc/backup-scripts/do-backup --exclude-from /etc/backup-scripts/dont-backup --ignore-failed-read --absolute-names --verbose --gzip --file $BACKUPPART/$MONTHLYLINK/$FULLBACKUPNAME > $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPLOGNAME 2>&1 gzip $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPLOGNAME
       gzip $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPLOGNAME
       echo "Done creating $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPNAME"
       echo "to view the log file, type:"
       echo "zcat $BACKUPPART/$MONTHLYLINK/$MONTHLYBACKUPLOGNAME.gz"

    # be sure to reset the partition to read-only

       echo -n "Remounting backup partition read-only...."
    if ( mount $BACKUPPART -o remount,ro &> /dev/null ) then
       echo "Done"
    else
       echo "Failed to remount $BACKUPPART partition in read-only mode!"
       echo "Aborting Monthly backup"
       exit 1
    fi # end if statement
}

fullbackup()
{

    # set partition to read-write.
    
       echo -n "Remounting backup partition to read-write...."

    if ( mount $BACKUPPART -o remount,rw &> /dev/null ) then
    
       echo "done"
       else
       echo "Failed to remount $BACKUPPART in read-write mode!"
       echo "Aborting Full system backup"
    
    exit 1

    fi # end if statement

    # now create the backup directory
    
       test ! -e $BACKUPPART/$DIRECTORYNAME
       echo "Creating $BACKUPPART/$DIRECTORYNAME directory...."
       mkdir $BACKUPPART/$DIRECTORYNAME
    
    # now the link to this directory
       
       echo "updating the link to the current date....."
       rm $BACKUPPART/$CURRENTLINK
       ln -s $BACKUPPART/$DIRECTORYNAME $BACKUPPART/$CURRENTLINK

    # now we need to create a variable for the last full backup
       
       echo "Updating $BACKUPPART/$CURRENTLINK/lastfullbackupdate"
       date > $BACKUPPART/$CURRENTLINK/lastfullbackupdate
       
    # now the backup

       echo "Running tar..."
       tar --create --label "$FULLBACKUPLABEL" --files-from /etc/backup-scripts/do-backup --exclude-from /etc/backup-scripts/dont-backup --ignore-failed-read --absolute-names --verbose --gzip --file $BACKUPPART/$CURRENTLINK/$FULLBACKUPNAME > $BACKUPPART/$CURRENTLINK/$FULLBACKUPLOGNAME 2>&1 gzip $BACKUPPART/$CURRENTLINK/$FULLBACKUPLOGNAME
       gzip $BACKUPPART/$CURRENTLINK/$FULLBACKUPLOGNAME
       echo "Done creating $BACKUPPART/$CURRENTLINK/$FULLBACKUPNAME"
       echo "to view the full backup log file, type:"
       echo "zcat $BACKUPPART/$CURRENTLINK/$FULLBACKUPLOGNAME.gz"

    # make a list of all packages installed.
      dpkg --get-selections > $BACKUPPART/$CURRENTLINK/selections

    # clean out the local repository of retrieved package files
      apt-get clean
       
    # remount partition to read-only

      echo -n "Remounting backup partition read-only...."
    if ( mount $BACKUPPART -o remount,ro &> /dev/null ) then
      echo "Done"
    else
      echo "Failed to remount $BACKUPPART in read-only mode!"
      echo "Aborting Full backup"
      exit 1
    fi # end if statement

}

incrementalbackup()
{

    # mount partition to read-write       

       echo -n "Remounting backup partition read-write ... "
    if ( mount $BACKUPPART -o remount,rw &> /dev/null ) then
       echo "done."
       else
       echo "Failed to remount $BACKUPPART in read-write mode!"
       echo "Aborting Incremental System Backup."
       exit 1
    fi # end if statement

    # create variable with date of last full backup
       lastfullbackupdatevar=`cat $BACKUPPART/$CURRENTLINK/lastfullbackupdate`

    # check for existence of incremental backup

    if test -e "$BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPNAME"; then
       echo "Please wait a minute and try again."
    else
    # create incremental backup
       echo "Running tar..."
       tar --create --label "$INCREMENTALBACKUPLABEL" --files-from /etc/backup-scripts/do-backup --exclude-from /etc/backup-scripts/dont-backup --ignore-failed-read --newer "$lastfullbackupdatevar" --absolute-names --verbose --gzip --file $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPNAME > $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPLOGNAME 2>&1
       gzip $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPLOGNAME
       echo "Done. Created $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPNAME"
       echo "To view the incremental log, type:"
       echo "zcat $BACKUPPART/$CURRENTLINK/$INCREMENTALBACKUPLOGNAME.gz"

    fi # end if statement

       echo -n "Remounting backup partition read-only ... "
    if ( mount $BACKUPPART -o remount,ro &> /dev/null ) then
       echo "done."
       else
       echo "Failed to remount $BACKUPPART in read-only mode!"
       echo "Aborting Incremental Backup."
       exit 1
    fi # end if statement

}

# --------------------------------------------------
# main routine:
# --------------------------------------------------

    # perform the backup.
       echo "---------- Backup Script Running... ----------"

    if test `date +%A` = "Sunday" && ! -e "$BACKUPPART/$DIRECTORYNAME"; then

    # if it's Sunday and you havent done a full backup, do so
       echo "Performing Full Weekly Backup..."
       fullbackup;

    elif test ! -e $BACKUPPART/$CURRENTLINK/*full.tar.gz; then

    # if there is no current fullbackup, make one now
       echo "No Current Full Backup - Performing Full Backup Now..."
       fullbackup;

    else

    # otherwise, do an incremental backup
       echo "Performing Incremental Backup..."
       incrementalbackup;

    fi # end if statement

    if test ! -e $BACKUPPART/$MONTHLYDIRNAME/*full.tar.gz; then

    # if there is no current Monthly Backup, make one now
       echo "No Monthly Full Backup - Performing Monthly Backup Now..."
       monthlybackup;
    fi # end if statement
       echo "---------- Backup Script Finished ----------"

```**do-backup :**

```
/boot
/etc
/home
/root
/usr/local
/var
/downloads
/scripts

```**dont-backup :**

```
*.mp3
*.mpg
*.avi
*.wav
*.mov
*.asf
*.rm
*.iso
*.flac
*.zip
*.exe
data.bin
/cdrom
/usr/local/fonts
/usr/local/games
/usr/local/j2re
/usr/local/j2re1.4.0
/usr/local/winbackup
/var/cache/apt/archives
/media
/mnt
/backup
/dev
/var/lock
/var/run
/tmp
/var/tmp

```


Wow! nice work creating this script. :) I will try this when I have the time.

---

### Post by soldonz on 2008-01-09
I have a server (server1) with two IDE HDDs and raid 1 setup. 

now I would like to make another server (server2) based on server1. however, server2 has just a single SATA HDD and therefore no raid. 

Can I use this script to backup server1 and do a clean ubuntu install on server2 and do a restore on it to create a clone of server1?

Many thanks,

Sol

---

### Post by kdfuller on 2008-01-10
I used this method to backup and reinstall my computer. All worked great but I get an error when I restore. It gets to initrd/ and exits with an error. I haven't found anything that doesn't work so far. Any ideas?

---

### Post by tech9 on 2008-01-11
> **kdfuller said:**
> I used this method to backup and reinstall my computer. All worked great but I get an error when I restore. It gets to initrd/ and exits with an error. I haven't found anything that doesn't work so far. Any ideas?

Are you restoring from root?
I know that this is not recommended to ever use the root account, but that is what I use and only in the case of restore, because you know that you will have full permissions to put all files back in place.

What is the exact error message that you are getting?

---

### Post by kdfuller on 2008-01-11
I did the cd / and used the sudo command. Is this right? Here is the error I get.

lib/libblkid.so.1.0
lib/libulockmgr.so.1.0.1
lib/libnss_hesiod.so.2
lib/libbrlapi.so.0.4.1
srv/
initrd/
tar: Error exit delayed from previous errors

I am copying this to a new raid0 setup. Will that make a difference? Forgive me I am fairly new to linux but want to learn. Thanks.

---

### Post by tech9 on 2008-01-11
> **kdfuller said:**
> I did the cd / and used the sudo command. Is this right? Here is the error I get.

lib/libblkid.so.1.0
lib/libulockmgr.so.1.0.1
lib/libnss_hesiod.so.2
lib/libbrlapi.so.0.4.1
srv/
initrd/
tar: Error exit delayed from previous errors

I am copying this to a new raid0 setup. Will that make a difference? Forgive me I am fairly new to linux but want to learn. Thanks.

It should work from liveCD, but try going into your root account and see if you can get it to work. Sounds like a permission problem to me.

---

### Post by gilf on 2008-02-28
I'm wondering what the possibilities are for using remastersys.

I tried it in the dist mode which basically makes a liveCD of your existing system. I did that with my desktop computer and then installed it on my laptop. It worked okay except for a quirk which doesn't allow a user with the same name to be set up on the new install. Actually, you can do it, but I found you couldn't log into the new system. Basically the problem was that it didn't set up a Home directory for the username in that case. I solved the problem by using a LiveCD to transfer an existing (somewhat cleaned up) home folder.

It's been working fine for a month, and I did raise the bug with the developer.

There is also a mode for backups that copies the existing Home folder to the live CD (and subsequent install) I haven't tried that since I wanted to make a generic LiveCD that didn't copy my user data.

Anyway, I just thought this might be interesting to you.

Basically you re-master the Ubuntu liveCD to include you present installed apps.  Kind of a Yourbuntu.

---

### Post by gilf on 2008-02-29
I just transferred my whole system to a new SATA drive from a PATA drive using a Remastersys LiveDVD generated by the old system. The advantage of doing it this way is that the LiveDVD acts just like the original Ubuntu LiveCD: it does a lot of hardware probing and configuring (including adding the new SATA to fstab) allows you to format and set up the new partition structure with the new drive. But It also installs the new applications you had installed on your mature system, and of course does not install applications you may have removed from the original stock Ubuntu installation.

As an example of the advantage, I decided that this time, intead of /home residing on the / partition, I wanted a separate /home partition. No problem when doing a new install from a LiveDVD. Just tell it that's what you want.

After installing, I then copied over my /home folder to the new installation. I had  to change the permissions on my /home/username folder to my actual username, since it copied over the owner as "1000". Otherwise you are unable to logon. This is a quirk of the present version of Remastersys -- it can't handle setting up a new intallation user with the same name as the one that created the LiveCD. But, no problem. I just transferred the user home folder and corrected the permissions while in failsafe mode boot. After that everything was normal, except that the network manager had been set to roaming, instead of the wired static IP address that I normally use -- understandable because that is the default in a LiveCD, and the network settings aren't retained in the user's home directory. Oh also, I had to re-enable restricted drivers (in my case Nvidia) because they also are not set on a typical LiveCD. (You wouldn't want them installed by default on another non-Nvidia system)

Other than that I haven't seen any difference in the newly installed system. So far at least.

The nice thing is that I also now have a LiveDVD that I can use to reinstall the system if ever needed again. In fact it can be used on other unrelated systems as a liveCD with all your apps, or you can even install to a completely different system.

If you are interested in trying Remastersys, some caveats:

1.) Be sure to get the latest version from the author, as the current Ubuntu version (7.10) is flawed. Update /etc/apt/sources.list with
> # Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/
then upgrade Remastersys to latest.
2.) Don't run anything while remastersys is working to create an ISO ( a long time on a big system)
3.) Don't interrupt remastersys while working (again, a long time and little feedback -- be patient)
4.) If you've added much to your system without removing much, it will need to be burned to a DVD insead of a CD. You burn the ISO separately from Remastersys -- it just creates the ISO file.

---

### Post by Rohbart on 2008-07-08
> **tech9 said:**
> To backup:

**tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /**

To Restore:

**tar xvpfz backup.tgz -C /**

excluding the boot dir and fstab file will give you the ability to restore all your data/settings on a new partition

Just posting a helpful tip, for all of you out there trying to find a decent backup solution.

Ein Prosit

How can I do it? I mean excluding them.

---

### Post by tech9 on 2008-07-11
> **Rohbart said:**
> How can I do it? I mean excluding them.

I am not sure what your asking. 

The command excludes the fstab in order to keep your UUID - so you will be able to boot from grub still - is this what your asking?

---

