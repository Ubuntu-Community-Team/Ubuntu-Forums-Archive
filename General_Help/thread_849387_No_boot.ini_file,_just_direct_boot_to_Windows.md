---
title: "No boot.ini file, just direct boot to Windows"
date: 2008-07-04
forum: General Help
---

### Post by andyharrington on 2008-07-04
I ran wubi today.  No errors indicated.  When I rebooted, no OS loader options appeared: it just started Windows.  I have read many references to boot.ini.  I have no such file at all.  I do not have a windows XP Pro CD.  I have also read stuff saying boot.ini is no longer used by Windows.  

I uninstalled ubuntu and ran wubi again with the same results.

---

### Post by ago on 2008-07-04
boot.ini is often hidden, you have to make sure you can see hidden files in Explorer>Tools>Folder Options

---

### Post by andyharrington on 2008-07-04
> **ago said:**
> boot.ini is often hidden, you have to make sure you can see hidden files in Explorer>Tools>Folder Options

I have looked at the hidden files, and boot.ini is missing.

When I go in tot he control panel, system, advanced, startup and Recovery, Settings, I get a message window:

The C:\boot.ini file can not be opened.  Operating System and Timeout settings can not be changed.


That would explain wubi failing, I think.

On my recovery drive the boot.ini file is readable

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional"
/noexecute=optin /fastdetect


That would need to be changed to refer to my C: drive 39GB partition

DISKPART> list partition

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  Partition 1    Extended            84 GB  8033 KB
  Partition 2    Logical             39 GB  8064 KB
  Partition 3    Primary              8 GB    84 GB
  Partition 4    Unknown           1028 MB    92 GB

I would guess that is partition 2.

I do not want to put in a boot.ini that kills things.  Could I recover at this point booting from a live CD, mounting the windows partition, and deleting a bad boot.ini?

Help appreciated.

---

