---
title: "Backup &amp; Deja Dup"
date: 2012-10-17
forum: General Help
---

### Post by unibroker on 2012-10-17
I am testing out the above before I install the 64 bit of 12.04.  When I hit "restore" of Backup the computer does nothing.  When I go to my Home folder and try to see the contents of my external drive that I backed up to I can't access it.  When I try to "Safely Remove" I am told I can't.  Finally just rebooted and everything was back to normal.  Any ideas?

---

### Post by cryptotheslow on 2012-10-17
It sounds like a permissions problem on the mount point of the external drive.

What is the actual message you are given when you try to "Safely Remove"?

What format is the external drive? (FAT, NTFS, Ext3 etc.)

With the external drive plugged in, take a look in /media - who shows as the owner of the directory the hard drive is mounted and what are the permissions on that directory? (You may have to use the file explorer options to display those as additional columns.)

---

### Post by unibroker on 2012-10-17
> **cryptotheslow said:**
> It sounds like a permissions problem on the mount point of the external drive.

What is the actual message you are given when you try to "Safely Remove"?

What format is the external drive? (FAT, NTFS, Ext3 etc.)

With the external drive plugged in, take a look in /media - who shows as the owner of the directory the hard drive is mounted and what are the permissions on that directory? (You may have to use the file explorer options to display those as additional columns.)

It must have been a permissions thing because it restored once I set the Owners permissions.

The external drive folder that I was trying to restore is Type folder (inode/directory).  The computer started with WinXP and I backed up my database from there.  Then I dual booted Ubuntu and began backing it up to the same external drive.  It never gave me warning when I backed up.  In fact, I just checked and even the Windows database is Type folder (inode/directory). Is this going to be problematic?

---

### Post by cryptotheslow on 2012-10-17
A "folder" is always going to show as inode/directory - that's fine. It's just two different terms for the same thing (Microsoft call them folders, *nix call them directories). Although that said - Nautilus the file explorer that Ubuntu use seems to have adopted "folder" now I look.

If a single file is showing as inode/directory then yes there may be a problem. If it's just the folder (or directory) that the database files are in that are showing as that type then fine.

I'm not sure I follow what you are trying to achieve at the moment. You say you are testing a restore of a Dejadup backup - are you restoring something back over itself or in some test environment e.g. LiveCD boot?

---

### Post by unibroker on 2012-10-17
> **cryptotheslow said:**
> A "folder" is always going to show as inode/directory - that's fine. It's just two different terms for the same thing (Microsoft call them folders, *nix call them directories). Although that said - Nautilus the file explorer that Ubuntu use seems to have adopted "folder" now I look.

If a single file is showing as inode/directory then yes there may be a problem. If it's just the folder (or directory) that the database files are in that are showing as that type then fine.

I'm not sure I follow what you are trying to achieve at the moment. You say you are testing a restore of a Dejadup backup - are you restoring something back over itself or in some test environment e.g. LiveCD boot?

BTW, thanks for the help.

I just checked gparted and everything is saved in filetype ntfs.  In answer to your other question; I have never had the need to restore a backup.  I wanted to backup /home folder and then restore it back to another folder on the same partition just to satisfy myself that it worked.  I couldn't verify anything if I just restored it to the folder I had just backed up right?

I tried to take out my external hard drive but when I right clicked that drive to "Safely Remove" I again get the message: ```
unable to unmount hard drive name unmount: /media/hard drive name is not in the fstab (and you are not root)
```

I'm reading up on fstab.

---

### Post by cryptotheslow on 2012-10-17
You are right. If you backed up then immediately restored to the same place it would be hard to determine if it had been successful.

I've never had a problem restoring a Dejadup backup after doing a fresh install to a new Ubuntu version, but I still take a second plain copy of /home just in case (don't forget the obscured folders with names beginning with a dot).

I tend to restore back my older version home dir somewhere else, then manually copy over the various folders I need for my applications. If you are jumping to 12.04 from an Ubuntu version older than 11.10 then this may be a wise approach as there is a step change from Gnome2 to Gnome3, not dragging in all the cruft from your Gnome2 configuration seems sensible for example.

It's a little longer winded this way, but I think it results in a more stable environment than just blindly dumping the whole of /home into the new install.

---

### Post by unibroker on 2012-10-17
> **cryptotheslow said:**
> You are right. If you backed up then immediately restored to the same place it would be hard to determine if it had been successful.

I've never had a problem restoring a Dejadup backup after doing a fresh install to a new Ubuntu version, but I still take a second plain copy of /home just in case (don't forget the obscured folders with names beginning with a dot).

I tend to restore back my older version home dir somewhere else, then manually copy over the various folders I need for my applications. If you are jumping to 12.04 from an Ubuntu version older than 11.10 then this may be a wise approach as there is a step change from Gnome2 to Gnome3, not dragging in all the cruft from your Gnome2 configuration seems sensible for example.

It's a little longer winded this way, but I think it results in a more stable environment than just blindly dumping the whole of /home into the new install.

I'm staying with 12.04 just moving from 32 bit to 64.  I was advised not to do an upgrade but rather a fresh install.

---

### Post by cryptotheslow on 2012-10-17
Ah OK. I don't think there is even such a thing as 32 to 64 bit upgrade path.

Definitely a clean install scenario as every binary will need to be replaced.

So as you are staying on the same version, Dejadup your /home/x and just restore it once you have 64bit installed. It should just work, there shouldn't be anything xBit specific in the config files in your home dir. But take a plain file copy just in case you need to selectively restore. (Or not - maybe just me being a belt n braces type).

There are of course a thousand other ways to skin this cat, e.g. if you have the disk space to resize a partition and do the new install of 64bit to a different partition then copy across your old home. Still needs a backup of course :)

I think this was solved at post #3 although the  detour into databases and WinXP leaves me with an uneasy feeling that something in unanswered.

---

### Post by unibroker on 2012-10-18
I decided to reopen this because still having the same issue which I know is user error.  I need to change all user permissions for the ext hard drive.  Thanks.

---

### Post by PaulInBHC on 2012-10-18
While we are on the subject, I have a usb enclosure with an old HDD that has a XP install on it. I am planning on installing 12.10 64 on a partition. I have 12.04 32 now.

Should I backup 12.04 home to the ext drive and restore to 12.10 or is there a copy and paste type method?

---

### Post by unibroker on 2012-10-18
> **unibroker said:**
> I decided to reopen this because still having the same issue which I know is user error.  I need to change all user permissions for the ext hard drive.  Thanks.

I am command line and filesystem challenged.  Thought the output of mount might be useful.  

```
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jim)
/dev/sdf5 on /media/HP Pocket Media Drive_ type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdf2 on /media/6e9ac323-45f6-4cb0-acca-8277530a3584 type ext4 (rw,nosuid,nodev,uhelper=udisks)
```

The folder I'm trying to restore, and this is where the problem began, is on HP Pocket Media Drive.  I tried to ```
ls -la /media/HP Pocket Media Drive_
``` but returned not found even though that filename was suggested when I hit tab. 

I have been researching this but when my brain turns to mush when I'm reading things like this, "Your sdb3 HFS+ partition has been mounted read-write - at least that is what mount is telling us. This means that it is probably the non-journalled version of HFS+, so you *should* be able to chmod it from Ubuntu to sort out your permissions problems."

---

### Post by ajgreeny on 2012-10-19
Try ```
ls -la "/media/HP Pocket Media Drive_"
```though you may not need the final underscore unless it really is in the name of the folder.  Linux will not allow spaces in file or folder names unless you "escape" the space, either with quotation marks or a backslash before the space, so **/media/HP\ Pocket\ Media\ Drive_** should work as will the quotation mark way I show above.

For this reason it's a good idea to always use a character in place of spaces in Linux file or folder names;  I use either an underscore or a hyphen ( _ or - ).

---

