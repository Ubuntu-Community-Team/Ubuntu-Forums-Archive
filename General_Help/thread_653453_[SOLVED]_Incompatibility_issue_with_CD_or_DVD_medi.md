---
title: "[SOLVED] Incompatibility issue with CD or DVD media produced on Mac Os."
date: 2007-12-29
forum: General Help
---

### Post by jesushero on 2007-12-29
I am having problems accessing files on DVD's burned on Mac OsX. When I insert such DVD's, I can see the folders with an X on them and I can not list the files or access them in any way. The permissions set the owner as 501. As I am not the owner, I can not access the files and as it is a DVD the owner can not be changed unless the entire content is copied on my hard drive, which may not work as other users with the same problem have suggested. 

An existing thread is this: [http://ubuntuforums.org/showthread.php?t=342815]("http://ubuntuforums.org/showthread.php?t=342815")

I am not sure if it is the same problem or not, it looks very similar.

What needs to be done is the permissions of files on Cd's and DVD's to be overridden, and replaced with the permissions given to the users by the system administrator. Since DVD's and CD's are meant to be used with many different systems, it is no use sticking to permissions given to files on them. This only adds to incompatibility, from which Linux already suffers a lot. From what I understand, Os X has a way of writing DVD's and CD's with weird permissions that make them normally unusable to Linux users. Apparently they will not bother making their operating system compatible with linux, so let's find a way around this! 

It also happens to movie DVD's that are burned on Os X. When I insert the movie DVD, the DVD player starts and tries to play it but returns a permission error. 

What is EXTREMELY strange about this is that it has started happening with some DVD's that I had previously accessed with no problem on the same Linux machine, with absolutely no hardware or software changes other than the updates. I am running Gutsy 7.10.

The syslog says that the DVD has been mounted as readonly. Why is that?

```
Dec 30 03:31:40 Levendis kernel: [  619.403894] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'i knew them', timestamp 2007/10/12 16:38 (1000)
Dec 30 03:33:09 Levendis kernel: [  707.983013] UDF-fs: Partition marked readonly; forcing readonly mount
```

What could have caused a partition that was not normally mounted as readonly to suddently start mounting as such?

The proposed solutions by meb495 have not solved my problem in any way.

> I found an easy fix that worked from someone on the LinuxQuestions forums. The fix is adding my UID and GID (user ID and group ID) to the dvd-drive entry in my fstab. This overrides whatever is written on the individual disks and makes me the owner of every file on any disk in the drive.

As you'll see, the following is that portion of my fstab.

/dev/hda /media/cdrom0 udf,iso9660 user,noauto,nosuid,uid=michael,gid=100 0 0

Other options that were suggested included 1) manually adding a UID of 501(the owner of the burned files) to my passwd file and logging in as 501, which i didn't try and 2) copying the files as root from the command line, which I unsuccessfully tried but for all I know I may have done incorrectly because people say it is supposed to work - I'm not sure.

The thread on the linuxquestions forum is at:

[http://www.linuxquestions.org/questi...=1#post2614856](http://www.linuxquestions.org/questi...=1#post2614856)

---

### Post by jesushero on 2008-01-02
> Originally posted by [thelatinist]("http://ubuntuforums.org/member.php?u=422818") on [this thread]("http://ubuntuforums.org/showthread.php?p=4060957").

Glad it works. To explain, both of these override the file permissions on the CD. The way user modes work under *nix, permissions are set by a three-digit number. The first digit represents the permissions for owner, the second for group, and the third for other. The digits are determined as follows: Execute = 1, Write = 2, Read = 4. If you want to set more than one permission, you add these numbers together to get the correct digit. Thus:

Execute = 1
Write = 2
Execute + Write = 1 + 2 = 3
Read = 4
Execute + Read = 1 + 4 = 5
Write + Read = 2 + 4 = 6
Execute + Read + Write = 1 + 2 + 4 = 7

When using the mode option you are setting who should have permissions for all files. You have to add a 0 before the three-digit mode. Therefore mode=0555 grants read and execute permissions to user, group, and other. Since it is read-only, you don't need write permissions.

When using the umask option, you are setting who should NOT have permissions (anything not specifically denied is allowed). Since nobody needs write, you use 222. You do not add 0 before a umask value.

Please note that the mode is umask (user file creation mode mask), not unmask.

This works for me.

---

