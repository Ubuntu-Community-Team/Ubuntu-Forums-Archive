---
title: "Noob - trying to repair windows 8 boot error, ubuntu said fixed but isn't"
date: 2016-08-29
forum: General Help
---

### Post by bicsuk on 2016-08-29
Hi

I've done basic repairs over the years and only today came across Ubuntu when creating a system restore USB for Windows 8.

I had a battle to get in and flashed the BIOS, discovered that UEFI is the new standard, shorted nodes to bypass the password, and finally got to boot to the Ubuntu interface which apparently repaired the boot problem, but sadly did not -

[http://paste.ubuntu.com/23107734/](http://paste.ubuntu.com/23107734/)

Could anybody help or advise please? (The original Windows error was winload.efi / 0xc00000f)

Apologies if I have posted in the wrong section, and thanks in advance for any assistance :)

---

### Post by yancek on 2016-08-29
If you read the the boot repair output, you will see mention of your windows system being in an 'inconsistent' state which means you left it hibernated or left fastboot on or both so I doubt the boot repair will be able to do anything until you change that.   Try turning that off and running it again.  If you can't boot windows, use the installation DVD and the repair option on it to run chkdsk as suggested in the boot repair.

There is no sign of anything Linux related in your boot repair output  so I would suggest that you try posting at a windows forum or the  microsoft support site with the original error you reported.  Additionally, you might post more details on any changes that occurred immediately prior to this problem.  If it was booting previously, it is not likely to fail without some change being made unless it is a hardware problem.

---

### Post by bicsuk on 2016-08-29
Thank you very much yancek

---

### Post by Jimysbil on 2016-08-29
Make sure your Bios\UEFI has not enabled a 'Secure Boot' option.
Also make sure you are using bios boot (not UEFI) in case your partition table is (msdos).
If your system is hibernated you have to start it up somehow or you find an other (boot) solution in order to fix it.

---

