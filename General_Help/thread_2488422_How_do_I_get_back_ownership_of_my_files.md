---
title: "How do I get back ownership of my files?"
date: 2023-07-04
forum: General Help
---

### Post by dorasmith24 on 2023-07-04
I have a dual boot system, and a hard drive with various data files, like, documents.  I have used this drive and its folders in both Windows 10 and Ubuntu 20.04.

Now I'm trying to edit files with Libre Office, and it's telling me I don't have write permission.  When I check the permissions it says I can't change the permissions because I don't own the files/ folders.   

I tried sudo chown -R dora /mnt/966A029F6A027C6D, which is how properties tells me my hard drive is mounted, and it went through taking ownership of a whole lot of files, but nothing changed.  I still don't own my files.

How do I fix this.   

I'm figuring Windows messed with my permissions/ ownership.   It messed with the ability of some drives to even mount - but this one is mounted.  Grrrr.    I don't know who invented Windows - but I had to use it for a work from home job.

I have determined that the folders on the drive are currently owned by root.   That being so sudo chown should have worked.  

Yours,
Dora

---

### Post by TheFu on 2023-07-04
NTFS doesn't support chmod nor chown.  Only native Unix/Linux file systems support those tools.

Only through _mount options_ can the owner, group and permissions be set for non-native file systems. There are many threads in these forums about just that or you can find use [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by dorasmith24 on 2023-07-05
So if the drive has some ntfs files on it the whole drive shows as I don't own it?

---

### Post by TheFu on 2023-07-05
> **dorasmith24 said:**
> So if the drive has some ntfs files on it the whole drive shows as I don't own it?

Files aren't "ntfs" or not.  The "File System" is.  There are 50+ different file systems and Windows uses NTFS, FAT32, FAT16 and ExFAT.  None of those "file systems" support Unix permissions.  If you want to use Unix permissions (owners, groups, permissions, ACLs, and xattrs), then you need to use Unix file systems like ext2, ext3, ext4, f2fs, zfs, btrfs, xfs, jfs, .... the list goes on and on.

If you don't want to use Unix permissions, then you'll need to set those values with your mount options.  This is spelled out in the link already provided.  Until you mount the file system with the permissions, owner, and group you want, you won't have the desired access. It is a limitation of NTFS and how Linux can access NTFS.

As posted previously, there are lots of threads in these forums about this including example solutions. There are a few gotchas when dealing with NTFS, which is why I didn't just post 2 commands.  The links have those gotchas spelled out.  You can thank MSFT for a few of them, like not closing file systems at reboot.  MSFT started doing this with Win8 and later. Linux won't touch a file system that hasn't been properly "closed."  Gotcha. You'll have to change some settings inside MS-Windows to allow access. Best to find those settings on an MS-Windows forum.

In the end, for a permanently connected storage device that you want to access from Linux, you'll probably want to modify/add 1 line to the /etc/fstab to mount it. Something like:
```
LABEL=250G   /misc/250G  ntfs    nodev,windows_names,nosuid,noatime,async,big_writes,timeout=2,user,fmask=0002,dmask=0002   0     0
```
is what I'd use. There are caveats for the LABEL, mount location, but everything else is probably fine as is.  Use **sudoedit** to modify system files like the /etc/fstab.  After adding the line (with the stuff you need specific to your system and storage), run **sudo mount -a** to have the fstab processes and the new mount handled.  Then the storage would be under /misc/250G with my example.

Or you could run a mount command directly.  
```
sudo mount  -t auto -o big_writes,uid=1000,gid=1000 LABEL=250G   /misc/250G 
```
That will probably be good enough.  The /misc/250G directory must already exist before running the command above. Creating the directory is a 1-time thing, assuming you don't delete it later.

When done, use **sudo umount  /misc/250G** to close the mount and file system properly.  Or you can just power down the machine and the normal linux shutdown process will umount it for you.

As for setting the label, I'd use **gparted**. This is a 1-time thing. There are other ways/tools that can label a file system. Gparted is the easiest.

---

### Post by Rubi1200 on 2023-07-06
If you boot the system with a liveUSB and use Try Ubuntu mode you should be able to see and access ALL files on the relevant partition/drive.

If you can, I strongly recommend you backup them up to another location before trying to change permissions or anything else.

---

### Post by oldfred on 2023-07-06
Windows turns fast startup back on with updates. That sets hibernation flag.
When hibernation flag is set, Linux NTFS driver will not mount files in read/write mode to prevent loss of data. 

If you wrote into a hibernated filesystem, it would be lost when Windows restored the hibernation backup.

Check Windows fast startup setting, whenever you have issues.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)

---

### Post by dorasmith24 on 2023-07-07
I really think it's something that resulted from booting into Windows, not something that has to do with my files or changing permissions or the file system.

Of COURSE I'm not going to go changing the file system without backing up the files; it would destroy them!    I don't believe people are suggesting that for a solution.

I don't understand the last post.  If Windows did something to my data drive with fast start or hibernation, how exactly do I undo it?  I don't see any clear instructions, just a vague list of links.

With another data drive, Ubuntu lost the ability to automatically mount it, but then when I manually mount it it works fine.   
But with this drive, it's mounted, just no write permissions on the grounds that root owns it and I don't.

---

### Post by TheFu on 2023-07-07
> **dorasmith24 said:**
>  
I don't understand the last post.  If Windows did something to my data drive with fast start or hibernation, how exactly do I undo it?  I don't see any clear instructions, just a vague list of links.

You need to click the links. Read their contents. Follow the steps outlined.
> **dorasmith24 said:**
>  
But with this drive, it's mounted, just no write permissions on the grounds that root owns it and I don't. 


And post #4 has 2 options for resolving this specific issue. Because your system is different from everyone else's, you'll need to make some choices.  What label you want and which empty directory you'd like to mount the ntfs file system.  We can't do that for you.  I've shown what I do as a hint, but only you can make the decision.  And one of the caveats is that MS-Windows can't have left the file system _open_ between reboots.  Things can be simple, until they aren't, but we don't know which things are the issue on your system, so the simple stuff may not work.  We won't know until you try them AND report back that some problem happened.  We can't read minds. If you don't tell us the facts, then we are just guessing. Sometimes we guess wrong.

---

### Post by MAFoElffen on 2023-07-07
Going back a few posts... Let me clarify something. I have multi-OS shared storage.

Windows OS & NTFS doesn't understand Linux permissions and ownership, nor does Linux care about NTFS AD permissions (at least, not by default), but... 

If you have an NTFS filesystem mounted, you can add and change ownership and set permissions.

If this is a persistent mount via /etc/fstab, those will be persistent. You mount it, set ownership, set the permissions... Done.  That can be done manually or via the fstab options.

If removable media & removed (unmounted), it looses those, and resets back to root.

Did you try to mount it manually? If so, did you do 
```

ls -lah <mountpoint>

```
To see that you could see what was there and what the ownership and permissions were set to?

If it mounts... And you can see the above... Then the ntfs filesystem is not in a hibernation state. No sense in chasing ghosts if that isn't the case, right? If it doesn't mount, and it can't read it... Yes, fastboot should always be off... Even if this user was only using Windows... Keeping a filesystem "open" is never a wise choice.  

There are a lot of details of many other things in the what if and what may be... But lets simplify this a bit, please? Some things just make more sense to users who are not familiar with the many other things that might go wrong, if we break it down to logical steps...

Does it make sense to go from there?

---

