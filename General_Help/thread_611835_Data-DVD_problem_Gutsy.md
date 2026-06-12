---
title: "Data-DVD problem Gutsy"
date: 2007-11-13
forum: General Help
---

### Post by bobulator on 2007-11-13
Quite a while back, I burnt some data onto a DVD (running Windows XP). I then opened up this DVD in Ubuntu gutsy. I clicked on one of the folders but instead of the file manager opening it up as if it were a directory, it treated it as if it was a file.

I have experienced this problem on two PCs running MythBuntu 7.10 (in Xfce) and a standard desktop install of Ubuntu 7.10.

How can I sort this out?

Thanks in advance

---

### Post by anaconda on 2007-11-13
I have had the same error in feisty.. with nautilus

If I tried to access tose folders from the terminal they always worked correctly.

So, what happens if you try to go to those directories using terminal?

---

### Post by bobulator on 2007-11-14
I try 'cd /media/cdrom0' and the terminal says 'Permission Denied'.
I then tried 'sudo cd /media/cdrom0' and the terminal outputs 'sudo: cd: command not 
found'

Hmm.

---

### Post by bobulator on 2007-11-15
UPDATE:
I found out that my two ubuntu PCS can read ISO DVDs but not udfs.

When I look in the file browser, it shows all of the folders as 'Unknown Type'.

I've been looking around the Ubuntu forums but I still don't know what to do.

:cry:

---

