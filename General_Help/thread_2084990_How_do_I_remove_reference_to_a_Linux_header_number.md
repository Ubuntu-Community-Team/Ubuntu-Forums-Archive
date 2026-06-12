---
title: "How do I remove reference to a Linux header number"
date: 2012-11-17
forum: General Help
---

### Post by chipppy on 2012-11-17
Good afternoon

 I am getting the following error
Quote:
Package in inconsistent state

The package 'linux-headers-3.0.0-20' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.

I cannot find a copy of 30.0.0-20 anywhere.  I can start my system via previous version of linux, 30.0.0-17

I would like to  know how to make the system start automatically via 30.0.0-17, and delete references to 30.0.0-20.  I can the upgrade to 12.10, currently 11.04.

Does any know where I can find a good guide on how to do this please

Cheers
Chipppy

---

### Post by claracc on 2012-11-17
This tutorial [http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462) can help you about different ways to remove the not desired kernel and using the 3.0.0-17 one.

You must be carefull to proceed in order to have always a kernel your system can boot.

---

### Post by chipppy on 2012-11-19
Good Morning

This seems like a good answer.  I tried to install variuous version from latest back to 10.04 version.  All came up with the same issue

> Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 972, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1096, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the linux-headers-3.0.0-20 package. This might mean you need to manually fix this package.


The top 3 FILE: lines changes slightly but always the last line (manual fix missing linux header......).

I tried installing via package manager, CLI, etc various version and always the same issue I need to fix the missing linux header


Anyone got a idea of hoe to fix or remove the reference so that I can upgrade system.  I log in via 3.0.0.17 so deleting it's reference (I dont know where) is a possible option.  The file is definatly missing I know that much

Cheers
chipppy

---

