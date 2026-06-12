---
title: "About Backing Up your valuables ..."
date: 2006-12-01
forum: General Help
---

### Post by newagelink on 2006-12-01
The thought occurred to me that, rather than do something complex in trying to upgrade to Ubuntu 6.10 from 6.06 (fixing broken dependencies before the distro download in the Updater thing -- even though I'd already downloaded the iso, verified it, and burnt it to CD-R), I could simply burn all my valuable files -- probably with file structure intact -- to a CD- or DVD-R, then completely wipe clean the partition (erase it?) and install Ubuntu 6.10 fresh.

I stopped myself from posting "how do i do this" and did a quick search and found [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) from [a post by deadgobby]("http://ubuntuforums.org/showpost.php?p=1827370&postcount=2").

But I don't care about backing up my entire system; I've not made hardly any changes from the default. I was tempted to right-click on /home/daniel > Create Archive instead. (I'd burn the compressed folder to disc, then copy it back to desktop, extract it, cut/paste it back into place?)

But I want to save Firefox bookmarks and settings, Thunderbird settings and emails, gaim settings, and Rhythmbox ratings. I know I can backup the Mozilla programs seperately (pretty sure I can, anyway) but there must be a more effecient way to do them all at once. Doesn't Ubuntu store all application settings in some folder?

... so I guess I'm creating this thread after all.

What other folders do I need to back up, and what's the most efficient way of doing it?

Those are pretty much the only programs I use; I have other things installed but I've never used them. Google Earth and ZSNES have never worked, other programs I've installed but have never tried and so can reinstall, etc.

Somehow -- according to System > Administration > Disks (Disk Manager) > Partition 3 I seem to have 6.26 GB on this partition -- that can't be all data, can it? Either way, I have a DVD burner.

I plan to continue searching and browsing threads here later; I've wasted too much time not being productive, and now I feel anxious about not having done homework. ](*,) 

I'm slowly learning, I think, which is good. I've seen some threads where people post knowing even less than I.

I should just keep browsing. Shortly after posting this thread I found this:
> **aysiu said:**
> From what I know, applications generally live in /usr, libraries to support applications usually live in /lib, systemwide settings usually live in /etc, and user-specific settings live in /home/*username* from [http://ubuntuforums.org/showthread.php?t=309326&highlight=backup+data](http://ubuntuforums.org/showthread.php?t=309326&highlight=backup+data) ... but should I back up these folders "just because"? I'm thinking it would cause problems if I repasted my /usr without the right applications installed, etc.

---

### Post by gerbman on 2006-12-02
> **newagelink said:**
> The thought occurred to me that, rather than do something complex in trying to upgrade to Ubuntu 6.10 from 6.06 (fixing broken dependencies before the distro download in the Updater thing -- even though I'd already downloaded the iso, verified it, and burnt it to CD-R), I could simply burn all my valuable files -- probably with file structure intact -- to a CD- or DVD-R, then completely wipe clean the partition (erase it?) and install Ubuntu 6.10 fresh.

I stopped myself from posting "how do i do this" and did a quick search and found [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) from [a post by deadgobby]("http://ubuntuforums.org/showpost.php?p=1827370&postcount=2").

But I don't care about backing up my entire system; I've not made hardly any changes from the default. I was tempted to right-click on /home/daniel > Create Archive instead. (I'd burn the compressed folder to disc, then copy it back to desktop, extract it, cut/paste it back into place?)

But I want to save Firefox bookmarks and settings, Thunderbird settings and emails, gaim settings, and Rhythmbox ratings. I know I can backup the Mozilla programs seperately (pretty sure I can, anyway) but there must be a more effecient way to do them all at once. Doesn't Ubuntu store all application settings in some folder?

... so I guess I'm creating this thread after all.

What other folders do I need to back up, and what's the most efficient way of doing it?

Those are pretty much the only programs I use; I have other things installed but I've never used them. Google Earth and ZSNES have never worked, other programs I've installed but have never tried and so can reinstall, etc.

Somehow -- according to System > Administration > Disks (Disk Manager) > Partition 3 I seem to have 6.26 GB on this partition -- that can't be all data, can it? Either way, I have a DVD burner.

I plan to continue searching and browsing threads here later; I've wasted too much time not being productive, and now I feel anxious about not having done homework. ](*,) 

I'm slowly learning, I think, which is good. I've seen some threads where people post knowing even less than I.

I should just keep browsing. Shortly after posting this thread I found this:
 from [http://ubuntuforums.org/showthread.php?t=309326&highlight=backup+data](http://ubuntuforums.org/showthread.php?t=309326&highlight=backup+data) ... but should I back up these folders "just because"? I'm thinking it would cause problems if I repasted my /usr without the right applications installed, etc.If you're going to be reinstalling your system, you probably only need to back up your home directory (unless you have other important files elsewhere). Ideally, your home directory would live on a partition separate from the rest of your system, in which case you could simply tell the Ubuntu installer to use your previous home directory for the new installation (no backup required). If you have everything on the same partition, I would follow the directions in your first link and only back up your home directory. All Firefox, GAIM, etc. preferences are saved in your home directory.

---

### Post by newagelink on 2007-10-27
Thank you for your reply; I think that's precisely what I'll do. I think I should upgrade to the new Ubuntu release, as it may fix some glitches I'm having. (My mouse goes crazy with the scroll button for some reason, and my external hard drive will not Eject, and I have to sudo umount it every time.)

Sorry for not replying sooner, or for thanking you sooner ...

---

### Post by gerbman on 2007-10-28
> **newagelink said:**
> Thank you for your reply; I think that's precisely what I'll do. I think I should upgrade to the new Ubuntu release, as it may fix some glitches I'm having. (My mouse goes crazy with the scroll button for some reason, and my external hard drive will not Eject, and I have to sudo umount it every time.)

Sorry for not replying sooner, or for thanking you sooner ...Wow, that really was a delayed reply ;)  No problem though...glad to hear the suggestion might be of some use.

---

### Post by newagelink on 2008-02-16
[COLOR="Navy"]From [https://help.ubuntu.com/community/BackupYourSystem#head-de480b373eb0d8792f72058e9f5ca443040d5c57](https://help.ubuntu.com/community/BackupYourSystem#head-de480b373eb0d8792f72058e9f5ca443040d5c57) I found [https://help.ubuntu.com/community/UbuntuHomeBackup](https://help.ubuntu.com/community/UbuntuHomeBackup) ("This page does not exist yet.")

How do I back up my home directory? I've copy/pasted the folder onto my external hard drive, but I doubt that's the best way to go about it: My experience with Windows makes me think that often filesystems change between operating system releases, and that simply pasting back into "/home/daniel" may not work (programs won't recognize data, things will have changed in where data is stored, etc.)

I'm now attempting to update from 7.04 to 7.10. I just want to backup Firefox, Thunderbird, gaim chat logs, and Rhythmbox data.[/COLOR]

---

### Post by newagelink on 2008-02-18
[COLOR="Indigo"]I'll do more searches, Google searches as well as ubuntuforums searches, I suppose is the best way to go about it.[/COLOR]

---

### Post by drpaul on 2008-02-18
If you look in your home folder [with hidden stuff displayed] I think you'll find most of the stuff you've referenced.

HTH

Paul

---

### Post by newagelink on 2008-03-01
After showing hidden files, I right-clicked on /home, and selected "Create Archive..." and told the next dialog window to create home.tar.gz at /media/My Book/Backup.

I received the following error message, after a while of a 'processing' window thing saying 'Getting file list' or something: > An error occurred while adding files to the archive. Failed to fork (Cannot allocate memory) What does it mean and how do I fix it?

---

### Post by SyL on 2008-03-01
> **newagelink said:**
> After showing hidden files, I right-clicked on /home, and selected "Create Archive..." and told the next dialog window to create home.tar.gz at /media/My Book/Backup.

I received the following error message, after a while of a 'processing' window thing saying 'Getting file list' or something:  What does it mean and how do I fix it?



Must be due to the fact that some files located under /home are currently used.

---

### Post by newagelink on 2008-03-01
[COLOR="Indigo"]Should I exit XChat and gaim and firefox and Rhythmbox and try again? (Thanks for the reply.)[/COLOR]

---

### Post by SyL on 2008-03-01
> **newagelink said:**
> [COLOR="Navy"]
How do I back up my home directory? I've copy/pasted the folder onto my external hard drive, but I doubt that's the best way to go about it: **My experience with Windows makes me think that often filesystems change between operating system releases**, and that simply pasting back into "/home/daniel" may not work (programs won't recognize data, things will have changed in where data is stored, etc.)
[/COLOR]

ext3 partitions will always work on the same way under 7.04 or 7.10

---

### Post by SyL on 2008-03-01
All applications you are currently running might use some files related to your profile, located under /home/username/.applicationname

So you can try to exit all applications your are running.

(you are welcome)

---

### Post by Zimmer on 2008-03-01
> **SyL said:**
> All applications you are currently running might use some files related to your profile, located under /home/username/.applicationname

So you can try to exit all applications your are running.

(you are welcome)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

The method I used in the past, before I re installed Dapper some time ago and created a separate /home partition at install, was to copy  my /home directory to a DVD or copy it via the network to my other machine.

This forced me to tidy up my files and discard the rubbish and archive the little used files.

When the new install was done I copied back the relevant 'hidden' files and settings.

---

### Post by newagelink on 2008-03-01
Exiting all open applications and then attempting to create home.tar.gz didn't seem to make any difference. Same error message and behavior.

In addition, clicking "Command Line Output" opened the window a bit, displaying a blank white area (something I forgot to mention the first time.) So I guess there's no command line output ...?

---

### Post by newagelink on 2008-03-01
> **Zimmer said:**
> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

The method I used in the past, before I re installed Dapper some time ago and created a separate /home partition at install, was to copy  my /home directory to a DVD or copy it via the network to my other machine.

This forced me to tidy up my files and discard the rubbish and archive the little used files.

When the new install was done I copied back the relevant 'hidden' files and settings.[COLOR="Indigo"]If I do this, then I won't have to worry about backing up the folder before an upgrade, right? But how much space should I allocate to this new home partition? I have 11.22 GB available for Linux and 8.08 of it is already full.[/COLOR]

---

### Post by Zimmer on 2008-03-01
Sounds like you do not have a lot of room for personal files, maybe that is why you are getting the error with tar.

Check you have not created an incomplete tar file which is taking up space.
As for your requirements for saving your settings for Firefox etc..

the folder to save is   home/.mozilla       (this folder may contain Thunderbird stuff , too. I do not know as I use evolution )

Please note that inside that folder is a firefox folder containing a folder randomly named which has your settings. A fresh install will create a fresh random folder there, too.

I cannot remember whether I 1) renamed my old folder to the new random folder name or 2) just copied in the old folder... and then deleted the other one...  
So i may have a bit of fun when I upgrade to HArdy later this year. 

The Rhythmbox settings appear to be located at usr/share/rhythmbox  . That looks straightforward.

FYI  I have a 160 gb HD and 131 of that is for my /home partition and I have 99gb left!

My /  (root)  partition is 10gb and I have used about half of that..

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)  
 recommends between 5 to 10 gb for the root   and the remainder for /home 
 
and, yes, my understanding is that when I upgrade I will tell the installer to leave that partition alone and install on the / partition

---

### Post by wolfen69 on 2008-03-01
i never backup because everything i download automatically goes to another drive. i keep nothing of value on my ubuntu install. it is the best way IMO.

---

### Post by newagelink on 2008-03-01
I am posting this from the Ubuntu 7.10 Live CD.

I've been following the instructions at [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) and while executing (or should I say "after entering the command in Terminal"?) ```
sudo mv /old/home /media/My\ Book/Backup/home_backup
``` I received the following error message: > mv: failed to preserve ownership for `/media/My Book/Backup/home_backup/daniel/Documents/videos/100_1023.MOV': Operation not permitted
mv: failed to preserve ownership for `/media/My Book/Backup/home_backup/daniel/Documents/videos/Hardware.Info -Build.Your.Own.PC - English - HDTV - 720p - 5mbps.wmv': Operation not permitted
mv: failed to preserve ownership for `/media/My Book/Backup/home_backup/daniel/Documents/videos': Operation not permitted
mv: failed to preserve ownership for `/media/My Book/Backup/home_backup/daniel/Documents/8,0km.png': Operation not permitted[COLOR="Indigo"]Is that important? What does it mean? I copied it for a few lines there; it appears to have applied to every file being moved onto the external hard drive. It appears to have now finished:[/COLOR] > mv: failed to preserve ownership for `/media/My Book/Backup/home_backup/daniel/.metacity': Operation not permitted
mv: failed to preserve ownership for `/media/My Book/Backup/home_backup/daniel/aaaaaa': Operation not permitted
mv: failed to preserve ownership for `/media/My Book/Backup/home_backup/daniel/.bashrc': Operation not permitted
mv: failed to preserve ownership for `/media/My Book/Backup/home_backup/daniel': Operation not permitted
mv: failed to preserve ownership for `/media/My Book/Backup/home_backup': Operation not permitted
ubuntu@ubuntu:/old/home$

[COLOR="Indigo"]I must make the backup on my external hard drive because I have 1% free space in /dev/sda3 -- what is called "old" there: It was originally 11 GB and the majority of my Linux partitions (I had a 1 GB extended partition for the linux swap and whatnot.) I resized that 11 GB to something like 8.03 GB (and it has 8 GB) in order to give my new partition the remaining 3 GB. Currently /home/daniel takes up 1.5 GB of the now 8 GB, so I figured the backup must go on my external hard drive. Then, if everything is successful, I hope to delete /home/daniel and reallocate the free space to the new home partition created, called /dev/sda6 ... Does that make sense?

It's pretty sad that my iPod has as much hard drive space as my laptop ... Thank God for this 250 GB Western Digital hard drive.

I tried continuing, and received another error message. I am wondering if it is wise to continue:[/COLOR] > ubuntu@ubuntu:/old/home$ sudo mkdir /old/home
mkdir: cannot create directory `/old/home': File exists I guess I should include this simply to be complete, so I have a record of what I did afterward: ```
ubuntu@ubuntu:/old/home$ sudo cp /old/etc/fstab /old/etc/fstab_backup
ubuntu@ubuntu:/old/home$ sudo nano /old/etc/fstab
```

---

### Post by newagelink on 2008-03-01
[COLOR="Indigo"]Thanks for your help, again, I'd be lost without you. ... Is there a place I can go to look up, for example, where my taskbar settings are stored? I've lost my taskbar customizations, among other things: program settings didn't transfer successfully, but they're backed up on my external hard drive.[/COLOR]

---

### Post by Zimmer on 2008-03-02
So, I take it you are using your new /home partition  ?

From what you wrote in your post #18 it would appear the mv command did not like  MoVing  
the files to that external disk.  What format is that disk ? VFAT ? NTFS? EXT3?    so did the files copy across ? 

I am guessing that instead of moving the files and directories it copied them , losing the permissions settings in the process and left  the /old/home directory sitting on the old partition, which is probably why the later command to re create it failed  , because it was still there...(this is still speculation, of course).

Can you see your partitions using System > Admiministration>Disks  ? and does that show a partition with an access path of /home  ?

PS sorry for the time delay on responding.... I am on a different continent.. :)

---

### Post by newagelink on 2008-03-02
I'm viewing GNOME Partition Editor instead of Disks, but yes, I now have /dev/sda6 with the Mountpoint /home ... I now have another problem:
[IMG]http://img.photobucket.com/albums/v36/NewAgeLink/screenshots/diskspace.png[/IMG]
When I tried to take that screenshot, it wouldn't let me save it on my desktop, despite having (only) 153 MB free ... What should I do? When cropping the image and saving it to my external hard drive, I received the following error: > GIMP Message
Failed to open '/home/daniel/.thumbnails/normal/gimp-thumb-6971-7390981b' for writing: No space left on device :(
Can I and should I reallocate the remaining space from /dev/sda3 to /dev/sda6? I don't think I can, because it wouldn't let me log on with 0.08 GB, so I had to delete my home folder from /dev/sda3 -- you're right, by the way, it copied the files to /dev/sda3 instead of moving them.

---

### Post by Zimmer on 2008-03-02
You are stuck for space... hmm, ok, try freeing up space by cleaning up the thumbnails in the hidden thumbnail folder   and setting Nautilus to use less space for thumbnails in 
edit >preferences>preview  and empty the trash folder (I just noticed I have 2gb of Trash !!!)


The other thing you can do ( as a previous poster suggested) is to copy your data files (pictures, music etc) to your external drive and just leave the necessary hidden stuff on the  /home partition  and always save data to that external drive.... but I expect you will still be short on space... as for the reallocation of space? I don't know. I would need to read a bit more on partitioning to answer that with confidence.

---

