---
title: "Hard disk mounting issues. (corrupt???)"
date: 2007-07-27
forum: General Help
---

### Post by specail on 2007-07-27
I have converted from windows today and am having issues with a hard drive that refuses to mount, or be fixed by ntfsfix.

I have 4 hard drives:

36gb raptor - ubuntu
320gb maxtor - ntfs (no os) Mounts fine
320gb wd - fat32 (USB) Mounts fine
320gb wd - ntfs sata - internal - the one with the issues.

I tried to manually remount

```
sudo mount -a
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.
Or
   Run ntfsfix version 1.13.1 on Linux unless you have Vista.
Or
   Mount the NTFS volume with the 'ro' option in read-only mode.

```

My next step was to get ntfsfix:
sudo apt-get install ntfsprogs

now to run it:

```
ntfsfix /dev/sdb1
Mounting volume... Error opening partition device : Permission denied
Failed to startup volume : Permission denied
FAILED
Attempting to correct errors... Error opening partition device : Permission denied
FAILED
Failed to startup volume : Permission denied
Volume is corrupt. You should run chkdsk.

```

I'm lost. The drive worked fine in windows. 
I no longer have windows installed, i got fed up with the genuine advantage crap after I upgraded my system. (mb, ram, cpu, gpu)

That drive is rather important. I have a project that I need to get finished. :(

---

### Post by jyba on 2007-07-27
I think you need to be superuser to run ntfsfix. Try...
```
sudo ntfsfix /dev/sdb1
```
...and give it your password.

---

### Post by HermanAB on 2007-07-27
As long as you have ntfs drives, you should keep a copy of BartPE in your tool box:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Cheers,

Herman

---

### Post by logos34 on 2007-07-27
running ntfsfix only flags a drive 'dirty' and schedules CHKDSK on next windows boot...But if you no longer have windows installed do you at least have an XP install CD?  You could do chkdsk from the recovery console.

---

### Post by specail on 2007-07-27
thanks, I manually edited fstab and the somehow the drive now works in ro mode

The drive has ~1.3 million 4kb files with random names and extensions. My directories are there at least. ubuntu tells me it cannot list the contents of the root directory.

I want to delete the 1.3 million files and keep my directories.

I can navigate to the sub directories I have remembered. 

sudo ntfsfix /dev/sdb1 gives me the same error.

The windows livecd should be helpful.

---

### Post by HermanAB on 2007-07-28
Don't delete anything.

---

### Post by Aesir09 on 2007-07-28
dude, i just had huge problems with my HDD, try this in terminal, if oyu not admin 



[PHPsudo gparted(or su gparted not sure)][/PHP]


use gparted to fix you HDD problems

---

### Post by Wiebelhaus on 2007-07-28
the NTFS log file is flagged as dirty , you must either run a chkdsk /r with a windows system or boot into a windows system , then shut down properly and it'll work.

---

