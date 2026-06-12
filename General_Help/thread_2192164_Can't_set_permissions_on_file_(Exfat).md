---
title: "Can't set permissions on file (Exfat)"
date: 2013-12-06
forum: General Help
---

### Post by marcovo on 2013-12-06
Hi all,

This week I formatted an external harddrive with Exfat, and mounted it on kubuntu, with FUSE exfat 1.0.1. Now I have a directory I want to patch with a .patch file, but if I try to do that, the patch-command gives me the error:
patch: **** Can't set permissions on file imageset/imageset.cfg : Function not implemented

I do know that exfat does not support chown/chmod, but I do not know how I can get patch to not try to set those permissions? The patcher now only patches the first file and then stops... Anyone knows what to do?

---

### Post by codenine75a on 2013-12-06
That is new to me.  I did not know linux supports the exFAT file system yet.  Umm did you use 'sudo' first?

---

### Post by marcovo on 2013-12-06
For which action should I use sudo? For the patch it does not seem natural, I'll try that however. I did use sudo for mounting/unmounting.

exFAT is as far as I know not officially supported, but FUSE exfat gives a way to make use of exFAT. As I want to share my external hard-drive between linux & windows, exFAT was one of the very few options I had. I does work, but it has some flaws, including my current problem.

---

### Post by marcovo on 2013-12-09
Aren't there any other suggestions? Sudo did not produce anything else than the same error. Can't believe I'm the only one having problems with this?

---

### Post by oldfred on 2013-12-09
If using with Windows & Linux the normal suggestion is NTFS. But any fuse mount would need permissions set as part of mounting. But external drives are not normally mounted with fstab as the external may not be plugged in when you boot and should then not be removed while booted.

 Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by mc4man on 2013-12-09
I suggest you either manually patch using a text editor, (if that's the nature of your 'patch')  or do such activities on a filesystem that supports permissions

---

### Post by marcovo on 2013-12-10
Thanks guys! I got the suggestion from someone that exfat would work better than NTFS. That was because I had another problem with NTFS: when I try to set permissions in ubuntu, it works fine, but windows 7 gets confused with the files. And vice versa: when setting the rights ok for windows, ubuntu has problems with the files. (See this post: [http://ubuntuforums.org/showthread.php?t=2188055](http://ubuntuforums.org/showthread.php?t=2188055) ) Do you have any suggestions for this?

---

