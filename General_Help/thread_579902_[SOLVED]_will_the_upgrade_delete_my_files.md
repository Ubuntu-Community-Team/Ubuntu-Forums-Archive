---
title: "[SOLVED] will the upgrade delete my files?"
date: 2007-10-18
forum: General Help
---

### Post by elidoperezmd on 2007-10-18
hi all. im want to upgrqqade to 7,10... if i update will i loose my files?
o any program that i have installed?

---

### Post by p_quarles on 2007-10-18
If you use the upgrade wizard to do it, no, you won't lose any files. The only things that will be removed are obsolete packages, and those will be replaced. 

It will also disable any third-party repos, but you can re-enable them after the upgrade.

---

### Post by banewman on 2007-10-18
It is always wise to backup important files before doing anything to the system - I have upgraded twice with no ill effects so didn't need the backups but I was glad I had them there just in case... :)

---

### Post by por100pre1 on 2007-10-18
Your files won't be lost. However, not all upgrades are perfect; please backup your whole user folder to removable media or external hard disk drive before proceeding.

---

### Post by g_hol on 2007-11-20
Yesterday, I finally decided to upgrade to Gusty.   All the process was OK except for the fact that I lost completely the files in one of my partitions.

I realize it, couple of hours after the upgrade, when I decided to empty trash, and I saw in the dialog windows the names of my files ...

Mounting point for that partition is /myPart , Permissions are 700, and owner is my account, not root. only personal stuff there, nothing system related...

I have a backup, so it wasn't a big deal for me .... But, I really want to know why those file were placed in the trash during the upgrade..  Any ideas ?

---

### Post by az on 2007-11-20
> **g_hol said:**
> Yesterday, I finally decided to upgrade to Gusty.   All the process was OK except for the fact that I lost completely the files in one of my partitions.

I realize it, couple of hours after the upgrade, when I decided to empty trash, and I saw in the dialog windows the names of my files ...

Mounting point for that partition is /myPart , Permissions are 700, and owner is my account, not root. only personal stuff there, nothing system related...

I have a backup, so it wasn't a big deal for me .... But, I really want to know why those file were placed in the trash during the upgrade..  Any ideas ?

The upgrade process does not put any files in the trash.

The package manager will only overwrite a file if that file is part of an incoming package.  The package manager will not touch any other part of your system.

---

