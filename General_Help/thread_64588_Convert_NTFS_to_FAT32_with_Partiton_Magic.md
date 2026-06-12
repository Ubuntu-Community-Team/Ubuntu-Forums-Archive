---
title: "Convert NTFS to FAT32 with Partiton Magic"
date: 2005-09-11
forum: General Help
---

### Post by BoomShake007 on 2005-09-11
Ok, i'm trying to convert two of my ntfs partitons to fat32 so both windows and linux can read/write.  My current setup is like this:

20GB NTFS - XP Pro installed here
10GB NTFS - Personal documents, etc
75GB NTFS - Media storage
512MB SWAP - ubuntu swap
100MB EXT3 - ubuntu boot files
13.4GB EXT3 - ubuntu files (/home directory, etc.)

Dual boot works fine, everything is dandy.  However, it's a real pain in the butt to have to reboot into each to modify files in the other.   I got something for windows that lets it see the EXT3 partitions, and supposedly write.  I can see the NTFS partitions in Ubuntu, no write.  I figure, making my Personal Docs and Media storage into FAT32, it would eliminate most of my problems and make things significantly easier.

I then fired up Partition Magic 8.0, selected the personal documents one to start. Clicked "Convert"-->"FAT32".  It added it to the tasks, then I hit "apply".  It started to work a bit, then gave me an error.  Basically, it said I have a file over 4GB in directory 5 on that partition.  Confused, i looked around, searched with the search feature in windows for anything over even 1GB on that drive.  Nothing.  When it rebooted to do the media drive, it seemed to work, but when it finsihed, rebooted, adn went back to windows, it still was NTFS.  The biggest file on that is a little over 2GB.  I know for a fact that I have nothing even close to 4GB on either partition.

So, what should I do?  Is there any way that I can get around this?

EDIT: Wrong forum, cant find delete button. Follow it [HERE](http://ubuntuforums.org/showthread.php?p=345075#post345075) instead.

---

