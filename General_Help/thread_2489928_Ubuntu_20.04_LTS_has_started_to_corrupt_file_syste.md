---
title: "Ubuntu 20.04 LTS has started to corrupt file systems on 3 different computers"
date: 2023-08-15
forum: General Help
---

### Post by john-mcauley on 2023-08-15
This is Ubuntu 20.04 LTS.

They are all Dells, 2 desktops and one laptop. The laptop was running Yocto crops on Windows, the other machines were plain Linux. not using docker.

I see checksum errors on files fetched by Yocto bitbake. Unexpected EOFs in downloaded compressed files and in C++ source files during compilation.

Folders with strange names.

rm -rf failing, the error being that I don't have permission to delete a sub folder that I own.

ls -l on the offending folder returns: ': bad message'.

In the end I reformatted the disk.

I tried a fresh install over a Windows desktop and the system was born broken. I could run Bitbake builds but saw file issues and then Ubuntu failed to shutdown.

Had similar problems on my Windows laptop.

Thinks had been fine on my Ubuntu 20.04 LTS build machine for years. I started noticing problems maybe 2-3 weeks ago. I saw intermittent checksum problems about then but didn't pay too much attention to them as builds would retry and it would work.

Is anyone else seeing filesystem problems after updating a 20.04 machine or on fresh installs?

Is this a regression? I've had years with no issues.

---

### Post by john-mcauley on 2023-08-15
This could have been caused by a memory stick transferred from one desktop to the other.

The laptop problems are harder to explain but, for now, I have removed the bad stick and things are building OK.

---

### Post by MAFoElffen on 2023-08-16
I am glad that you found the problem.

I would have done chkdsk on the Windows machine and fsck on the ext4 of Ubuntu, plus checked the filesystem on the USB flash drive...

This is why I use ZFS as a file manager, which is COW, meant to be self healing, and run scrubs weekly on all my pools, as part of my maintenance. Not saying you should convert, but I would look at the routine maintenance of your filesystems, along with your backup strategy... Especially when you are running something that process things bit-wise, bitrot can happen. This is why we do routine filesystem checks.

---

