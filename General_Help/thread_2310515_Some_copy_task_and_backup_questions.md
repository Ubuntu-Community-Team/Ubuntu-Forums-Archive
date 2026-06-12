---
title: "Some copy task and backup questions"
date: 2016-01-19
forum: General Help
---

### Post by felix39 on 2016-01-19
Hi,

I'm about to setup some backups and I'm not sure how to do them right. I hope there is some help out there for a Linux novice! :)

**Windows Machine NTFS Backup:**

I have 3 directories on an extranal NTFS drive which contain:

  - a Windows 7 VM
  - a Windows 7 Recovery 
  - all the data (images, docs, etc) from that Windows machine.

The three folders are pretty much the state of my old Windows Machine. I like to keep it in case I have to review something.

Now, how do I make identical copies of each folder onto another external NTFS hard drive, without loosing any of it's permissions, specials etc. - using Linux? 
If possible I'd like to use rsync for that task, but I'm not sure how it will behave with NTFS filesystems and Windows files. I'm afraid rsync changes the attributes or something so that I run into conflicts using the files with the Windows VM.
Can I just use the following command or will it cripple the new backup?

[COLOR=#8b4513]rsync -a --stats --progress[/COLOR]

-a includes: 

        - recursiv
    - symlinks
    - preserve perm.
    - preserve mod times
    - preserve group
    - preserve owner
    - preserve device files 
    - preserve special files

I think the -a command looks fine for the task, but does it apply correctly on NTFS filesystems with Windows files?
And what about "device files"? Do I need them on the new drive?
How would you copy the folders?

[COLOR=#ff8c00]Update:[/COLOR]
I'm using a Windows VM now to do the copying from NTFS to NTFS. I thought this way the least could go wrong. Still I would be excited to hear how one would do it in Linux (if it is possible at all).


[B]Data Backup with Linux:

[/B]I would like to prepare an new external drive as a backup drive for the data of my Linux Machine. Should I just use ext4 as a filesystem or is there a special one for the purpose of backups?
Can I just go with "[COLOR=#8B4513]rsync -a --delete [/COLOR][COLOR=#8B4513]--stats --progress" [/COLOR][COLOR=#000000]here as well? Or should I keep something in mind that I'm forgetting? The backup shall be run every week and it just contains common user data, like doc, images, project files etc..


[B]Linux Recover and Restore:

[/B][/COLOR]I would like to make a whole system recovery image of the Linux that is running on the internal SSD drive. So in case the SSD dies I can replace it with the new one, restore the image and continue where I was left immediately.
Can I just open "gnome-disk-utility" and use "create disk image" to make a recovery image? What about the other partitions on that drive? There is "Linux (Bootable) 239GB", there is "Linux Swap 17GB" and "Extended 17GB". Are there any limitation or other thinks I should know of?

Thanks in advance! :)

---

