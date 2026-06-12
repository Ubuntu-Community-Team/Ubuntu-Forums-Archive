---
title: "Does Feisty have NTFS out of the box?"
date: 2007-05-09
forum: General Help
---

### Post by Hydroxyl on 2007-05-09
Basically, the subject line.

Dad's laptop just ate it.

Well, some Windows 2000 Logon Process.

It'll blue screen after it "loads."

He just needs to backup some stuff and I was wondering the obvious.

**EDIT:** I mean, will it mount the filesystem on the live CD?

---

### Post by strabes on 2007-05-10
ubuntu READS ntfs out of the box but doesn't write to it, which shouldn't be a problem in your case. What you should do is boot into the live cd and run these two commands (assuming the partition where your dad's data resides is /dev/sda1)

```
mkdir windows
sudo mount /dev/sda1 windows
```

Then you'll be able to copy files from the windows directory onto an external hard disk or flash drive.

---

