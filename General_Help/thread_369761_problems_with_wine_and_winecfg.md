---
title: "problems with wine and winecfg"
date: 2007-02-24
forum: General Help
---

### Post by Mets on 2007-02-24
hey guys,

I recently tried to install wine on my computer, and I seem to be having a lot of configuration problems.  I can download it from the repository, and it seems to install without a problem, but nothing really works after that.

After installing, I tried to type "sudo winecfg" in the terminal, and this is what I get:

```
sudo winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/mets', starting in the Windows directory.
libGL warning: 3D driver claims to not support visual 0x4b
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.
libGL warning: 3D driver claims to not support visual 0x4b

```

A settings screen then comes up.  I click on the Drives tab and it says "You don't have a drive C.  That's not so great.  Remember to add one."  I click on the Add button and then on Ok, and it echo's in the terminal
```
err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '../drive_c'

```

The same is true if I try to change any settings.  Can anybody help me get this up and running?  Thanks a lot.

---

### Post by cisforcojo on 2007-02-25
First, if you can help it, DON'T run wine as root.
I suggest doing:

sudo apt-get remove --purge wine

and delete /home/mets/.wine (or any variation... like .wine-A7DNnd)

Then reinstall it, make sure you're getting 0.9.31 and run 'wineprefixcreate'
then 'winecfg'

don't use the sudo command with wine.

---

### Post by Mets on 2007-02-25
thanks a lot it seems like the wineprefixcreate fixed the add drives problem.  We'll see how it goes!

---

