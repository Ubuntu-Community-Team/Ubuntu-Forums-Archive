---
title: "umask, file copy, file creation, directory creation - I'm confused, please help"
date: 2021-06-11
forum: General Help
---

### Post by GhX6GZMB on 2021-06-11
In a recent thread [https://ubuntuforums.org/showthread.php?t=2442799](https://ubuntuforums.org/showthread.php?t=2442799) this issue was partially discussed.

But I'm confused.
 
I've manually set all my private directories and files in $HOME to block "other" completely using the chmod command with appropriate variables. This works 100%.

But when I create a new file, or copy from an outside source (eg, USB-stick), "other" always gets an r flag for those files.

How can I stop this permanently?

I've read up on the umask command, but there's no permanency in that alone. In which configuration file can I set the umask so it's automatic? Or is it a completely different parameter I'm looking for?

Thank You.

---

### Post by TheFu on 2021-06-11
In another thread the last few days, it was pointed out that either systemd or gnome has a huge bug [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1685754](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1685754) mainly due to the fact that the Gnome session is started before reading our personalized startup files where a normal user should have control over their **umask**.  

Seems to get the desired behavior is to modify the settings systemwide in the login.def file.  The default in that file is:
```
UMASK           022
```
May want to look up the 
```
USERGROUPS_ENAB yes
```
setting as well.

These are definitely bugs.  They violate the expectation that users have control over their umask.  The changes above would be workarounds for the bug. In theory, the bug was fixed in March 2021.

---

### Post by scorp123 on 2021-06-11
> **ml9104 said:**
>  But when I create a new file, or copy from an outside source (eg, USB-stick), "other" always gets an r flag for those files.


Does that even matter? Because if your $HOME directory **/home/yourusername** has its permissions set to "rwx --- ---" (aka "chmod 700") then it does not matter what permissions a file inside that directory gets... others would still not be able to access it because the "700" permissions on the home directory would prevent them from even getting there and reading anything.

---

### Post by TheFu on 2021-06-11
> **scorp123 said:**
> Does that even matter? Because if your $HOME directory **/home/yourusername** has its permissions set to "rwx --- ---" (aka "chmod 700") then it does not matter what permissions a file inside that directory gets... others would still not be able to access it because the "700" permissions on the home directory would prevent them from even getting there and reading anything.

Technically correct, but it would drive me nuts wondering whether I'd accidentally resent ~/ permissions.

umask should work across all user processes if set in the ~/.profile. Anything less is a bug.

---

### Post by scorp123 on 2021-06-12
> **TheFu said:**
> Anything less is a bug.

No argument there.

---

### Post by Morbius1 on 2021-06-12
> I've manually set all my private directories and files in $HOME to block  "other" completely using the chmod command with appropriate variables.
More of an FYI but there was no need to remove "other" from every directory and file in $HOME. All you needed to do is issue a chmod 0770 on $HOME.

The file system is hierarchical so block it anywhere along the path and it blocks access to everything past it.

Ubuntu 21.04 changes the default permissions on a users home directory to 750 so users cannot see each others files. If a second user attempts it they get stopped:
```
smbuser@vub2104:~$ ls -al /home/tester
ls: cannot open directory '/home/tester': Permission denied
```

---

### Post by GhX6GZMB on 2021-06-12
Thank You for your answers.
I'm not looking for the radical 700 mode for my home directories. It's not as simple as that.
Rather, I like having user and group enabled, and controlling access through user/groups management. This fits best in my environment.

Also, the "700" scenario wouldn't work. Presently I have this:

```
macro@macro-pc:/home$ ls -la
tdrwxr-xr-x  6 root    root     4096 May 10 23:22 .
drwxr-xr-x 21 root    root     4096 Jun  5 22:09 ..
drwxr-x--x 15 abguest abguest  4096 Jun  5 21:42 abguest
drwx------  2 root    root    16384 May  4  2020 lost+found
drwxr-x--x 17 macro   macro    4096 Jun 12 22:36 macro
drwxr-x--x  9 root    root     4096 Jun 10 22:09 timeshiftotal 36
```
As you see, /home has the x flags set for $HOME. There are reasons for this.
An example $HOME directory looks like this:
```
macro@macro-pc:/home/abguest$ ls -la
total 676
drwxr-x--x 15 abguest abguest   4096 Jun  5 21:42 .
drwxr-xr-x  6 root    root      4096 May 10 23:22 ..
-rw-------  1 abguest abguest    143 Jun  3 01:07 .bash_history
-rw-r-----  1 abguest abguest    220 Feb 25  2020 .bash_logout
-rw-r-----  1 abguest abguest   3771 Feb 25  2020 .bashrc
drwxrwx---  8 abguest abguest   4096 Jun  3 01:06 .cache
drwxrwx--- 17 abguest abguest   4096 Oct  2  2020 .config
drwxrwx---  2 abguest abguest   4096 Jun  5 21:42 Desktop
drwxr-x---  2 abguest abguest   4096 Apr 26 22:29 Documents
drwxr-x---  2 abguest abguest   4096 Apr 26 22:29 Downloads
-rw-r--r--  1 abguest abguest 108191 Jan 14  2020 .face.icon
drwx------  3 abguest abguest   4096 May  9  2020 .gnupg
drwxrwx---  3 abguest abguest   4096 May  9  2020 .local
drwxr-x---  2 abguest abguest   4096 Apr 26 22:29 Music
drwxr-x---  2 abguest abguest   4096 Apr 26 22:29 Pictures
drwx------  3 abguest abguest   4096 May 13  2020 .pki
-rw-r-----  1 abguest abguest    807 Feb 25  2020 .profile
drwxr-x---  2 abguest abguest   4096 Apr 26 22:29 Public
drwxr-x---  2 abguest abguest   4096 May 13 23:30 Templates
drwxr-x---  2 abguest abguest   4096 Apr 26 22:29 Videos
-rw-------  1 abguest abguest     53 Jun  5 21:42 .Xauthority
-rw-rw----  1 abguest abguest   9120 Oct 11  2020 .xscreensaver
-rw-------  1 abguest abguest 483913 Jun  5 21:44 .xsession-errors

```
The odd man out is .face.icon which needs r rights, as it is needed before logging in (SDDM).

Everything else under $HOME should have no rights for "other" at all.

My remaining question is: is /etc/login.defs the right place to change the umask value, or are there other files that need to be changed?

---

### Post by GhX6GZMB on 2021-06-12
OK, I've now tested this.
The desired result when creating new files or directories is achived by editing /etc/login.defs:
```
# UMASK is the default umask value for pam_umask and is used by
# useradd and newusers to set the mode of the new home directories.
# 022 is the "historical" value in Debian for UMASK
# 027, or even 077, could be considered better for privacy
# There is no One True Answer here : each sysadmin must make up his/her
# mind.
#
# If USERGROUPS_ENAB is set to "yes", that will modify this UMASK default value
# for private user groups, i. e. the uid is the same as gid, and username is
# the same as the primary group name: for these, the user permissions will be
# used as group permissions, e. g. 022 will become 002.
#
# Prefix these values with "0" to get octal, "0x" to get hexadecimal.
#
ERASECHAR    0177
KILLCHAR    025
**UMASK        027**
```
and
```
# Enable setting of the umask group bits to be the same as owner bits
# (examples: 022 -> 002, 077 -> 007) for non-root users, if the uid is
# the same as gid, and username is the same as the primary group name.
#
# If set to yes, userdel will remove the user's group if it contains no
# more members, and useradd will create by default a group with the name
# of the user.
#
**USERGROUPS_ENAB no**

```

BUT!! this only works for newly created files and directories.
If I copy files from outside, like a USB-stick, the permissions are completely uncontrolled.

There must be an additional setting/filter somewhere. Please help!

---

### Post by TheFu on 2021-06-12
What file system is used?  That's always relevant.  If they have a native Linux/POSIX compliant file system, then the permissions should carry over.  With FAT32/exFAT/NTFS, then all bets are off. You get what the mount options say.

umask is only for new files and only onto POSIX standard storage.

---

### Post by GhX6GZMB on 2021-06-12
> **TheFu said:**
> What file system is used?  That's always relevant.  If they have a native Linux/POSIX compliant file system, then the permissions should carry over.  With FAT32/exFAT/NTFS, then all bets are off. You get what the mount options say.

umask is only for new files and only onto POSIX standard storage.

I feared that answer.
External storage can be anything, but mostly files from FAT/NTFS systems. My hope was that it's possible to force permissions when copying from external sources. Why not? M$ files don't even have those attributes.
Another source is downloads from the Web. Resulting permissions are also no good.

---

### Post by TheFu on 2021-06-12
> **ml9104 said:**
> I feared that answer.
External storage can be anything, but mostly files from FAT/NTFS systems. My hope was that it's possible to force permissions when copying from external sources. Why not? M$ files don't even have those attributes.
Another source is downloads from the Web. Resulting permissions are also no good.

You can force the permissions used on Unix systems .... via the mount options.  This is well traveled and well answered in the different mount manpages AND in hundreds of forum posts here.

Whenever there are permissions issues, the first question must be - what file system is involved.
The 2nd question is local or network access - if networked, which protocol is being used?  NFS supports POSIX permissions to POSIX file systems. CIFS works like all non-POSIX solutions - the permissions are forced through the mount/share options.

That is just the way it is with non-POSIX stuff.

---

### Post by Morbius1 on 2021-06-13
> External storage can be anything, but mostly files from FAT/NTFS  systems. My hope was that it's possible to force permissions when  copying from external sources.
Try the following experiment: Eveything you do here can be unmounted and un-done so it's not permamant.

Install bindfs:
```
sudo apt install bindfs
```

Create a mount point in say your home directory - can be anywhere:
```
mkdir /home/tester/MyMedia
```

Temporarily mount your /media/$USER directory to MyMedia using bindfs specifying a different set of permissions:
```
sudo bindfs -o perms=0660:+D,force-user=tester,force-group=tester,nonempty /media/tester /home/tester/MyMedia
```

I have a file labeled ntfs-test.txt located at /media/tester/DataN. Since it's formatted ntfs it will exhibit the default ntfs permissions:
> tester@vxub2004:~$ ls -l /media/tester/DataN/ntfs-test.txt
-rwxrwxrwx 1 tester tester 0 Jun 13 08:07 /media/tester/DataN/ntfs-test.txt
If I look at the bindfs remount it will exhibit the permissions I specified:
> tester@vxub2004:~$ ls -l /home/tester/MyMedia/DataN/ntfs-test.txt
-rw-rw---- 1 tester tester 0 Jun 13 08:07 /home/tester/MyMedia/DataN/ntfs-test.txt
If I were to copy that file from MyMedia/DataN to my Public folder it will retain the permissions set by bindfs:
> tester@vxub2004:~$ cp /home/tester/MyMedia/DataN/ntfs-test.txt Public
tester@vxub2004:~$ ls -l Public/ntfs-test.txt
-rw-rw---- 1 tester tester 0 Jun 13 08:15 Public/ntfs-test.txt

To stop all this unmount it:
```
sudo umount /home/tester/MyMedia
```

You can set this up in fstab with a syntax change to have this "remount" happen at boot.

Bindfs creates an immutable "view" of something with a set of permissions that may differ from the source.

---

### Post by GhX6GZMB on 2021-06-13
OK, Thanks.
I'm in over my head here.
Binding and so on is out.
My file system is ext4, I've read through the complete "man mount" and am none the wiser.

I'll just stick to manually changing the permissions on copied files. But I thought it would be simpler.

---

### Post by TheFu on 2021-06-13
If the file system is ext4, that is a POSIX file system and normal chown, chmod, chgrp commands all work in the expected hierarchy and umask works as expected .. unless you use a GUI tool. If you do, then you'll need to make the changes to the logins.def file.

If you do file management in a shell, then all works as expected.  Avoid the GUI. That's my rule.  The GUI just makes simple things complex.

---

### Post by Morbius1 on 2021-06-14
> **ml9104 said:**
> OK, Thanks.
I'm in over my head here.
Binding and so on is out.
My file system is ext4, I've read through the complete "man mount" and am none the wiser.

I'll just stick to manually changing the permissions on copied files. But I thought it would be simpler.
My mistake. I thought this ...
> External storage can be anything, but mostly files from FAT/NTFS  systems.
... meant that for any random usb storage device you attach to your system you want to see a specific set of permissions.

---

### Post by GhX6GZMB on 2021-06-14
> **Morbius1 said:**
> My mistake. I thought this ...

... meant that for any random usb storage device you attach to your system you want to see a specific set of permissions.

Yes, sorry. The whole thing got a bit involved with different file systems, POSIX etc.

My goal was to:

1: Have newly created files and directories in $HOME have certain permissions, in my case no "other" rights. This works perfectly after modifying /etc/login.defs

2: When copying files _into_ my $HOME I want those permissions set as well. This does _not_ work. Either the existing permissions are kept (when copying from a Linux file system into $HOME), or random (it seems) permissions are applied when copying from FAT/NTFS/Web/etc. into $HOME.

This is where I thought a simple solution is possible. But apparently not.

---

### Post by TheFu on 2021-06-14
umask only applies when a file is created.  When I file is copied, the permissions from the original are copied too. It is a feature.

If you don't want "other" to have any read or write, just set the permissions that way.  There are recursive options for most of those commands (be extremely cautious doing this) or if those are too blunt, use '**find**' to be more selective about the file system objects to change the permissions on.  Don't forget that creating a script to create a script is perfectly valid for caution too.

---

### Post by GhX6GZMB on 2021-06-14
> **TheFu said:**
> umask only applies when a file is created.  When I file is copied, the permissions from the original are copied too. It is a feature.
 too.

@TheFu:

Thank You!
That was a clear answer that confirms my findings.
It seems I'm not an idiot after all. :)

I'll handle copied files manually.

Thank You all, this is from my point of view solved.

---

### Post by TheFu on 2021-06-14
> **ml9104 said:**
> @TheFu:

Thank You!
That was a clear answer that confirms my findings.
It seems I'm not an idiot after all. :)

I'll handle copied files manually.

Thank You all, this is from my point of view solved.

It only applies to file systems that support the POSIX standards  - i.e. not NTFS, not exFAT, not FAT32.  I don't know what happens with HPFS+.
Should work as expected for ext2/3/4 Reiserfs, zfs, btrfs, f2fs, and the 20 other non-Windows file systems with kernel support in Linux. It also works in NFS for mounts that aren't read-only.

---

