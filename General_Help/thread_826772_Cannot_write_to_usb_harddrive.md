---
title: "Cannot write to usb harddrive"
date: 2008-06-12
forum: General Help
---

### Post by Teronap on 2008-06-12
Hi all,

I want to back up my Xubuntu install onto an 500GB external HD.

Xubuntu sees it, lets me open files from it, but when I try to write to it it says that it is a read-only filesystem.

I've checked it is mounted, and it says:

```

david@david-desktop:~$ mount
...
/dev/sdg1 on /media/My Book type vfat (rw,nosuid,nodev,uhelper=hal,utf8,shortname=winnt,uid=1000)

```

so it looks like it should be able to write to it.

I have tried acessing it in my XP install and it's fine, i can read and write it easily.

Any ideas?

---

### Post by Pjotr123 on 2008-06-12
First "safely remove"(unmount) it in *Windows*. Windows then writes a stop code that Linux needs.

---

### Post by Teronap on 2008-06-12
I have just tried that, booted back into Linux, and I have the same problem. The result of mount is the same.

---

