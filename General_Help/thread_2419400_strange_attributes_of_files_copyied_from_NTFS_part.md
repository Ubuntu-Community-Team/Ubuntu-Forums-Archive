---
title: "strange attributes of files copyied from NTFS partition"
date: 2019-05-21
forum: General Help
---

### Post by antib on 2019-05-21
I have PC with recently installed Ubuntu MATE and 2Tb removable drive (NTFS formatted) with data files, backed up from previous OS installations (Linux Mint mostly).

There is no executable files - only media and data files.

I tried to mount this drive and copy those backups onto PC's hard drive. First thing I noticed - all files on mounted NTFS poartition have executable attribute. If I try to change it - it doesn't happen. Searching brought tons of discussions about how to set executable attribute for files on NTFS partition, which is opposite to what I need and were not useful anyway. 
I probably could remount it with noexec option specified, but I do not want to mount this drive manually all the time and decided to search for default NTFS mount options later.

After I copied some files to PCs hard drive (ext3 formatted) I tried to remove executable attribute from copied files.

```
sudo chmod -x -R folder_name
```

Result of this operation was somewhat strange. All sub-folders became inaccessible unknown objects (executing type command chowed them as unknown type files) with zero size, all files in  folder still accounted as files, but are unreadable even under sudo. 
In caja I can enter this folder, rename it or see it's properties.
The folder itself contains 23 items but has size 0 and after being removed into recycle bin can not be deleted permanently.

Trying to enter this folder in console failes: if I try to cd into it access is denied.

What is going on? I never ever expirienced anything similiar to this in Linux Mint or Debian.
I didn't copypasted actual console log because it is not in English locale.

---

### Post by TheFu on 2019-05-21
NTFS doesn't support Unix permissions.

The only way to control the owner, group, permissions or ACLs is through mount options. That only works at mount time.  Trying to do anything else later will be frustrating.

Well, that last paragraph isn't 100% truthful, but for a home user, it is.

As for what happens when you remove eXecute permissions from a directory, that is just normal Unix file/directory permissions. Work through a tutorial, then after you do that, create 3 userids, 2 groups, and mix/match which users are in which groups.  Open 3 terminals, su - into each userid in the different terminals, change the PWD to somewhere under /tmp/ and make about 10 sub-sub-sub directories. Play with the owner, group, and permissions bits.  Do all this in shells, forget GUIs.  Play around with files and directories. Mix and match everything and work through every possible combination of permissions with group membership  and specifically test using the userid outside the group.  See what is possible and what is impossible.
Try 4775, 775, 764, 711 permissions on directories. Notice what works and what doesn't.  The 711 permissions are really cool and very useful in a multi-user environment where you can't trust other users.
Also learn about the setgroupid permission bit. This is what makes working with others on the same files possible.

---

### Post by antib on 2019-05-21
This is quite interesting idea for general training, thand you, but it is not in direct relation to main questions:
1)where ubuntu keeps options, to mount every NTFS with eXecutable attribute on?
2)what exactly happened with my files?

upd: Surprisingly, I can not execute 'sudo cd' to enter this folder, but 'sudo mc' worked well, it shows same attributes are applied to files inside. Actually I managed to get my files back. But question 1 still remains.

upd: This worked as somewhat automated solution:
```

alias lsd="ls -d */" 
lsd > dir.txt 
for DIR in dir.txt ; do sudo chmod +x $DIR; done

```

---

### Post by TheFu on 2019-05-21
It is your storage, but I think you are doing things the hard way.

It might be surprising to you, but it isn't to anyone else familiar with Unix permissions.

```
drw-rw-r-- owner group  14:24 to_sort/
```

Directories must have execute permissions to be seen inside.  So, let's consider some permissions:

```
A - drw[COLOR="#FF0000"]x[/COLOR]rw-r-- owner group  14:24 to_sort/
B - drw-rw[COLOR="#FF0000"]x[/COLOR]r-- owner group  14:24 to_sort/
C - drw-rw-r-[COLOR="#FF0000"]x[/COLOR] owner group  14:24 to_sort/

```
Each of these permissions will allow 
A - only the "owner" has access inside the directory
B - only members of the group "group" have access inside the directory
C - only people who are NOT either the owner or in the group have access inside the directory.

"Access" doesn't mean they can list the contents.  That requires read on the directory.

There's another complication. If the 'r' bit is removed from any of the octal values (owner, group, other), but the 'x' is left, then scripts cannot be viewed or run, but compiled programs can.  For a userid to be able to actually run a script inside a directory, they must have both read on the file and execute on the directory.  This assumes that the filename is known without getting a list from the directory.

A GUI file manager will fail since they need to have access to list the files inside a directory in order to click.

Anyway, hope this clears something up. I assure you it isn't surprising to people who understand Unix permissions.

The simple way to handle this stuff is to ensure the userids that need access are either the owner or in the group and execute permissions is provided on the directory.  For NTFS, use the mount options to set dmask and fmask as you need them. 

Clear as mud?  If you have more things you believe to be odd, please post the ls -al for the parent directory and files. Seeing facts makes things easier.

---

### Post by antib on 2019-05-21
But it doesn't work if space is in sub-folder name.
I tried some variations of this
```
ls -d */ --quoting-style=escape --quote-name 
```
But it did not worked. What do I miss?

---

### Post by TheFu on 2019-05-21
> **TheFu said:**
>  
Clear as mud?  If you have more things you believe to be odd, please post the ls -al for the parent directory and files. Seeing facts makes things easier.

And ...

---

### Post by TheFu on 2019-05-21
> 1)where ubuntu keeps options, to mount every NTFS with eXecutable attribute on?
2)what exactly happened with my files?

a1) You did see above where the dmask and fmask need to be used on any mount commands if you want non-default values?
a2) Nothing. Removing execute on the directory just made them inaccessible.

More on a1 ... there are multiple different ways to control mount options, but how depends on the method used to mount the storage. This is only important for non-Unix file systems like exFAT, FAT32, vFAT and NTFS. Normal Linux file systems like EXT2/3/4, JFS, XFS, ZFS, or the other 50 choices, support using chmod and chown.

In general, if a script requires sudo to work, there's probably a better method.  Not always, but usually.

---

### Post by antib on 2019-05-22
> **TheFu said:**
> a1) You did see above where the dmask and fmask need to be used on any mount commands if you want non-default values?

What I asked for is where default options for mounting NTFS systems are stored. Location and name of config file, not where those options should be placed in shell command.

>  a2) Nothing. Removing execute on the directory just made them inaccessible.

And the command which made all of them accessible again was:

```
find -type d -exec sudo chmod +x '{}' ;
```

---

### Post by The Cog on 2019-05-22
> 1)where ubuntu keeps options, to mount every NTFS with eXecutable attribute on?
This is compiled into the NTFS driver, I think. It's not an option. If it emulated not having the executable bit set, then you would not be able to access the contents. So it **has** to set the executable bit.

If you want to remove the x on files once you have copied them back, you are almost there:
```
find -type f -exec sudo chmod -x '{}' \;
```

Better still, use tar when you back up to NTFS because this will retain the Linux file properties, or use a Linux compatible file system instead of NTFS.

---

### Post by TheFu on 2019-05-25
> **antib said:**
> What I asked for is where default options for mounting NTFS systems are stored. Location and name of config file, not where those options should be placed in shell command.

There isn't a central place, so there isn't 1 answer.  Mount options can be used in any of the places where mounts are supported, through a "real mount".  That isn't an official term. I use it do differentiate GVFS and GIO pseudo-mounts from all the others.

Where can real-mounts happen?
1) command line, using the **mount** command.
2) /etc/fstab ... which uses the **mount -a** at boot.
3) customized autofs files in /etc/ which are named by the admin, so there isn't any standard name, but ... they commonly begin with "auto."  If you didn't install and configure autofs, then none will be there.

Those are the places where mount options can be placed. You can specify "defaults", but for NTFS, those probably aren't good.  What are the "default" options, is spelled out in the manpage for the specific file system.  Manpages change with the installed version of any command, so the package on your system might have different defaults than on someone else's system.

> **antib said:**
> 
And the command which made all of them accessible again was:

```
find -type d -exec sudo chmod +x '{}' ;
```
You probably meant something like this:
```
find folder_name  -type d -exec chmod +x {} \;
```

Using **find** and **sudo** together might have detrimental impacts to a working system if any parameters aren't correct, but sometimes it is the best answer.  I've accidentally wiped an OS, at work, using those commands together in the mid-1990s. 'find' without a starting directory seems dangerous to me.  I'm unsure what the default value is, hopefully it uses $PWD if nothing is specified. Looked it up:
```
 If no starting-point is specified, `.' is assumed.
```
If the copy was done using your userid, then all the files in the target will be owned by your userid, so no need to use sudo on the find-chmod.  All good.

I'm showing the *{} \;* just as  a different way. Both ways are equally acceptable, but sometimes single-quoted things get ugly with more complex commands.  Really

This will have ZERO effect on NTFS file systems, but on Unix/Linux file systems, it will enabled the eXecute bit recursively.

If I were doing this, I'd use autofs for the NTFS disk. Setting the dmask, fmask, uid, and big_writes options at mount time so the owner is my userid, the directory and file masks are reasonable, and performance doesn't suck. Then when I used rsync to copy all the files over, the permissions would be reasonable on the target disk.  I'd use 
```
rsync -avz {source}/ {target}/
```, so if there is any issue along the way, restarting doesn't mean redoing all the copies again.  Also, since my userid is running rsync, all the data files in {target} will be owned by may userid.  A cause could be made to use mv instead, but recovering from any failure in that command is problematic since it could fail mid-copy.  A 'mv' across file systems is really a copy and a delete. I don't remember if the delete happens immediately after a file is copied or if the delete happens when an entire directory is copied successfully.  'mv' has some interesting options that might be useful.

Anyways, seems you've figured out what you needed to figure out. Sometimes, whatever works is the correct answer. Cheers.

---

### Post by mc4man on 2019-05-25
This is done via udisks2, specifically  this line in the ntfs section in the source code, i.e,  udiskslinuxfilesystem.c
> static const gchar *ntfs_defaults[] = { "uid=", "gid=", NULL };

Never could get any good reason why thru a bug report quite some time ago so for myself I patch udisks2 as such and rebuild - 
```
Description: remove x bit on files

--- udisks2-2.7.6.orig/src/udiskslinuxfilesystem.c
+++ udisks2-2.7.6/src/udiskslinuxfilesystem.c
@@ -339,7 +339,7 @@ static const gchar *vfat_allow_gid_self[
 /* ---------------------- ntfs -------------------- */
 /* this is assuming that ntfs-3g is used */
 
-static const gchar *ntfs_defaults[] = { "uid=", "gid=", NULL };
+static const gchar *ntfs_defaults[] = { "uid=", "gid=", "fmask=0111", NULL };
 static const gchar *ntfs_allow[] = { "umask", "dmask", "fmask", "locale", "norecover", "ignore_case", "windows_names", "compression", "nocompression", "big_writes", NULL };
 static const gchar *ntfs_allow_uid_self[] = { "uid", NULL };
 static const gchar *ntfs_allow_gid_self[] = { "gid", NULL };
```

---

