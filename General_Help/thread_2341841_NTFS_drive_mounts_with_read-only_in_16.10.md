---
title: "NTFS drive mounts with read-only in 16.10"
date: 2016-11-01
forum: General Help
---

### Post by joakimvr on 2016-11-01
Hi everyone,

I recently installed Ubuntu 16.10 and I'm very happy with everything, but I encountered a problem I've not had before.

I have a 1TB NTFS drive that appears to be mounted with read-only access. I cannot create folders, nor save files to this drive. I did not have this issue when I ran Ubuntu 16.04 or previous versions, so would appreciate any input or help getting it back to normal. The drive is listed as "sdb1". I have not had much experience mounting drives or changing permissions, so please take this into consideration when trying to point me in the right direction :)

Thanks in advance.
J

---

### Post by yancek on 2016-11-01
Is it auto-mounting under /media/username?  If so, check the owner:group and permissions from a terminal with:  ls -l /media and ls -l /media/username.  Chane 'username' to your actual username.  If you don't understand the output, post it here.

---

### Post by oldfred on 2016-11-01
it should all be mounted automatically as an external drive.
And Windows formats like NTFS & FAT32 cannot set ownership & permissions, other than defaults when mounted.

But Windows 8 or 10, now uses fast start up or always on hibernation. If not unmounted in Windows it still is hibernated.
It used to be that it would not auto mount hibernated NTFS at all, but you could manually mount read only. Perhaps they now mount read only?
Cannot mount read/write as that damages hibernation.

It also can be chkdsk is required & that can only be done from Windows or a Windows repair flash drive.

---

### Post by joakimvr on 2016-11-03
> **yancek said:**
> Is it auto-mounting under /media/username?  If so, check the owner:group and permissions from a terminal with:  ls -l /media and ls -l /media/username.  Chane 'username' to your actual username.  If you don't understand the output, post it here.

Thank you for your reply. Here is the output I get from the two commands in terminal;

joakim@joakim-G501JW:~$ ls -l /media
total 8
drwxr-xr-x  2 root root 4096 nov.   1 12:40 DATA
drwxr-x---+ 3 root root 4096 nov.   3 09:06 joakim

joakim@joakim-G501JW:~$ ls -l /media/joakim
total 4
drwxrwxrwx 1 joakim joakim 4096 okt.  25 13:00 DATA

Do you see anything that could be causing this? Any help is greatly appreciated.

J

---

### Post by joakimvr on 2016-11-03
I figured it out! Turns out fast-startup was re-enabled in Windows somehow when I re-installed Ubuntu 16.10.

Thank you to both @yancek and @oldfred for your help. You pointed me in the right direction. I will update the thread to solved. This is why I love Ubuntu. So many friendly and knowledgeable people on the forums.

---

