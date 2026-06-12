---
title: "BIT (backintime) has no config files"
date: 2022-05-18
forum: General Help
---

### Post by sofasurfer on 2022-05-18
I have BIT installed on drive #1. I not have drive #2 which I also installed BIT on. I want to restore drive #1 backup on drive #2. Trouble is that BIT will not launch on drive #2. There appears to be no config files. BIT man page says to run 'backintime check-config' to verify the configfile, create  the  snapshot  folder  and crontab entries.
Here is the result...
```
 $ backintime check-config
Traceback (most recent call last):
  File "/usr/share/backintime/common/backintime.py", line 27, in <module>
    import config
  File "/usr/share/backintime/common/config.py", line 32, in <module>
    import tools
  File "/usr/share/backintime/common/tools.py", line 1802, in <module>
    class OrderedSet(collections.MutableSet):
AttributeError: module 'collections' has no attribute 'MutableSet'

```
Can someone explain this? Is this my problem (whatever it means)?

---

### Post by TheFu on 2022-05-18
BIT does versioning with hardlinks.  That means you can just use rsync for the specific backup set to be restored.  This is a file/directory backup method and tool. Same for rsync.  Be certain to use **sudo rsync -avz** before the source and target locations, so permissions, owners, groups are maintained. That's very important.

In short, there's no need to use BIT for a restore.

---

### Post by sofasurfer on 2022-05-18
I don't understand a word you said. I am thinking you are talking about linking BIT to my previous backups. My issue is that BIT will not even open for the first time.
P.S. I am using GUI. I do still want BIT installed.

---

### Post by TheFu on 2022-05-18
> **sofasurfer said:**
> I don't understand a word you said. I am thinking you are talking about linking BIT to my previous backups. My issue is that BIT will not even open for the first time.
P.S. I am using GUI. I do still want BIT installed.

To restore backups created by BIT, you don't need BIT.  That is all. You can use rsync or any other command that can accomplish the same while retaining owner, group, permissions, ACLs, and xattrs.  rsync is probably the easiest to use.  It is what I do for restores 99% of the time. It works with BIT. I'm 100% certain. It works with a few other backup tools like rsnapshot, rbackup and for the last backup version created for rdiff-backup too.

But if you don't understand, I'm sorry. I don't know of a simpler solution to restoring backups for those specific tools.

---

### Post by sofasurfer on 2022-05-18
I understand how to restore backups. That does not solve my issue that BIT will not launch on my 2nd installation and that it has no backup files. BIT works fine on my 20.04 installation but will not launch on my 22.02 installation.

---

### Post by TheFu on 2022-05-18
> **sofasurfer said:**
> I understand how to restore backups. That does not solve my issue that BIT will not launch on my 2nd installation and that it has no backup files. BIT works fine on my 20.04 installation but will not launch on my 22.02 installation.

Ah ... I wasn't connecting Drive 1 and drive 2 as two different Linux installations. I assumed it was drive 1 was the source and drive 2 was the backup to be restored.
I wouldn't have responded to a BIT 22.04 question.
Sorry. It just wasn't clear to me.

---

### Post by sofasurfer on 2022-05-18
I have drive #1 and drive #2. #1 is my good functioning 20.04 with BIT installed. #2 is a fresh install of 22.04 with a non-functioning BIT.

---

### Post by TheFu on 2022-05-18
> **sofasurfer said:**
> I have drive #1 and drive #2. #1 is my good functioning 20.04 with BIT installed. #2 is a fresh install of 22.04 with a non-functioning BIT.

I'm not a python programmer, but it looks like a python module or 3 is missing
 or 
the newer version of the module doesn't contain the same functions that the older one did, so another module is needed?

Best to wait for a python person to respond.  Did the back-in-time project website have any similar bugs reported?  What type of a package was BIT installed - normal APT or snap or flatpak or appimage?

---

### Post by philhughes on 2022-05-19
This is an issue with the version of python in 22.04. You need to install the latest version (1.3.1) from the ppa:

[https://github.com/bit-team/backintime/issues/1223](https://github.com/bit-team/backintime/issues/1223)

---

### Post by TheFu on 2022-05-19
> **philhughes said:**
> This is an issue with the version of python in 22.04. You need to install the latest version (1.3.1) from the ppa:

[https://github.com/bit-team/backintime/issues/1223](https://github.com/bit-team/backintime/issues/1223)

So, just to be clear, this is a modification of the BIT program, not changing the version of python that is a core tool used to control all sorts of boot and other system scripts, correct?

---

