---
title: "Recovery of deleted files and folders"
date: 2016-10-19
forum: General Help
---

### Post by usernamenottaken on 2016-10-19
Hello guys,

I did something very stupid and I need help. I have the following setup: a laptop dual booting Ubuntu 14.04 and Windows 7 (x64). I accidentally pointed my /home/$USER$ folder to somewhere in Android Studio's settings (I'm new to it, so I do not remember well where exactly) and after trying to build a project I got my home folder deleted. After that I rebooted the machine to Ubuntu again (yeah, genius, I know :(). I assume, that the OS has overwritten the file table, so that file and folder recovery is no longer possible now. Nevertheless, I have previously used a live USB stick with **testdisk  **on it with great success to recover files from a NTFS partition, so I decided to give it a try. I am able to see some of the deleted files and folders, but they are all colored in red. If I try to see the contents of such a folder, testdisk shows the following message: "No file found, filesystem may be damaged". I tried copying some of the data, but both the folder and the textfile i tried to undelete were empty. The Documents, Pictures and Downloads folders, where most of my data was, appear normal, but empty (meaning that there are no files at all, regular or deleted), according to testdisk. Also, I am not sure that file recovery works for ext4 partitions, as the wiki page lists FAT, NTFS and ext2 filesystems in the section about file recovery. So my question to you is: have I overwritten the file table beyond the point of no return, so that file recovery is impossible, or there is some hope for my data?

Thank you very much!

---

### Post by TheFu on 2016-10-19
If you had some backups, then restoring the data should be relatively easy. Much easier than any other solution.
Besides that, I got nuthin' to suggest.

---

### Post by colmax on 2016-10-19
Maybe try nortons undelete if you have access to windows-think it's part of norton utilities
Normal delete isn't over-written just the first character becomes a tilde ~
Partition-table is a big deal tho which gparted may solve
Cheers

---

### Post by usernamenottaken on 2016-10-20
Thanks for the replies. I do have backups, but the most recent data, not  included in these backups, is the one that I am actually going after. Does this Norton utility recover data from an ext4 partion from its Windows environment, because I am somewhat sceptical? I  will look around and report back in several hours, but in the meantime,  if someone has a suggestion, please let me know :smile:

---

### Post by dragonfly41 on 2016-10-20
I would initially stick with using testdisk and possibly photorec on ext4 partition.  Norton is for Windows.

Yes, there is hope.  Just persevere.

---

### Post by TheFu on 2016-10-20
> **usernamenottaken said:**
>  I do have backups, but the most recent data, not  included in these backups, is the one that I am actually going after. 

Partial backups are better than none.  

Back in 2002, I lost 80% of my data because I hadn't got backup religion yet.  Had merged 3 disks into a single file system and 1 of the disks failed. That took all the data on the other 2 disks with it. Gone.  For about a week, I freaked out.

Soon after that, I've had daily, automatic, versioned, backups. I sleep really well.  Had a disk failure recently. Swapped in a new disk, restored from the backup made early that morning, all was good. It was a minor inconvenience and the cost of the replacement disk, nothing more.  When I purchase storage now, I get backup storage too. Have about 30 systems, all setup for daily, automatic, versioned backups.  Media files don't get multiple versions, just a simple rsync to other storage, but the apps, settings, DBs, blogs, and personal documents are all versioned (60-120 days).

I've used testdisk just to learn about it. Never really **needed** it. Can't imagine trying to use it for thousands and thousands of files.

When problems like this happen, we just need to learn and handled it better next time.

---

### Post by dragonfly41 on 2016-10-20
Undoubtedly a backup strategy is the best and safest way.
But there is always a chance of data loss between backups. Users become careless.

This paper [http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel](http://www.linux-magazine.com/Online/Features/Recovering-Deleted-Files-with-Scalpel)

under "Save my LaTeX" .. suggests

> However, you took the business of writing this paper seriously and tagged each file at the beginning and end with %filename.tex and %filename.tex End. This practice hugely increases your chances of seeing the contents again.
 
 In other words you can reduce the search profile from thousands and thousands of files to just the file(s) with your injected metadata.
 
 photorec and scalpel tools search for such signatures.
 
 If there are no signatures the tools will spew out thousands of files.

---

### Post by usernamenottaken on 2016-10-30
Last week, surprisingly to me, I was able to recover some of the data, so I would like to share my experience with you, maybe it could help someone else. I created a Live Ubuntu USB stick and installed **ext4magic** on it, as **testdisk **would not be of any help for ext4 and **photorec **would recover *every single deleted file it sees*. Besides that **photorec **does not recover the directory structure, so everything gets restored with a random name in a random folder. 

So this was my situation: I had some folders in the /home/$USER directory and some data in Documents, Pictures and so on. After the screw up I saw that my folders were gone and Documents and Downloads were unaccessible. I did a reboot, after which I saw the directory structure in /home rebuilt, but without my data. Testdisk did see some deleted files and folders in /home, but it was not able to recover them. Documents and Pictures were however empty. 

This is what I tried with ext4magic:

[FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] ext4magic [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]sda5 [COLOR=#660033]-a[/COLOR] $[COLOR=#7a0874]**(**[/COLOR][COLOR=#c20cb9]**date**[/COLOR] [COLOR=#660033]-d[/COLOR] [COLOR=#ff0000]"-24hours"[/COLOR] +[COLOR=#000000]**%**[/COLOR]s[COLOR=#7a0874]**)**[/COLOR] [COLOR=#660033]-f[/COLOR] home[COLOR=#000000]**/**[/COLOR]$USER[COLOR=#000000][B]/ -l
[/B][/COLOR][/FONT]
You provide the path to the unmounted partition (/dev/sda5), a switch to indicate deleted before or after (in my case -a for after) and a directory to look in (-f /home/$USER). The -l option "prints a list of all filenames which have not allocated data blocks. At  the beginning of the line are the percentage of unallocated data  blocks. After deletion you find here all the file names you can recover  with the Journal data." This is according to ext4magic man page. The output was more or less the same as testdisk - I saw some deleted folders, but not all. However, it showed a deleted file and some folders to be "recoverable". So I gave it a shot. I mounted an SD card and ran:

[FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] ext4magic [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]sda5 [COLOR=#660033]-f[/COLOR] home[COLOR=#000000]**/**[/COLOR]$USER/deleted_folder [COLOR=#660033]-r[/COLOR] [COLOR=#660033]-d[/COLOR] /path_to_SD_card
[/FONT]
And it worked almost perfectly. Files and directory structure were recovered, only several non-critical files were missing. 

So far nothing special, you would say. I still had some files totally missing. Here is where it became interesting for me. Running the first command without -l gave me a full list of everything in /home. So in my desperation in tried to grep for a specific folder, previously existing in /home/$USER. And I did get results! Although I pointed Android Studio to /home/$USER and it wiped out the data, it did not destroy everything. The folder I was looking for now resided in some strangely named __temp directory, inside the /home$USER/Android Studio folder. Even more surprising - this data could also be recovered! Again, not everything was there, but most of the things were.

I know, that at least in NTFS and FAT, if you delete something, it does not get physically removed from the harddrive. The location is simply marked as free, or writable (in layman terms). This is why file recovery is possible in first place - if the OS does not write anything new on that memory location, chances are, that your data is still there. What I found peculiar is, that even though there was a write operation, which should make file recovery impossible, the old data was not completely overwritten. 

I hope that someone else could benefit from my experience. There is some lost data, which I suppose is beyond recovery, but I did not have time to test everything. If I come up with some new results, I will let you know!

---

### Post by TheFu on 2016-10-30
Thanks for posting the update. 

Did you get backup religion yet?

---

### Post by usernamenottaken on 2016-10-31
Nah, not yet. I guess I first need to get myself an external HDD, and soon after I will be baptized :)

---

