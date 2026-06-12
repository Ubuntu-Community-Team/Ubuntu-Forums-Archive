---
title: "Vista doesn't show boot menu"
date: 2008-05-02
forum: General Help
---

### Post by mwiseley on 2008-05-02
I installed Wubi and everything went fine. I see the boot entry in EasyBCD, but when I boot the menu is never shown - it just goes straight to Vista. BCD details below. Any thoughts?

Matt


Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {23b8de6b-aef4-11dc-a4ce-96509b557824}
resumeobject            {23b8de6c-aef4-11dc-a4ce-96509b557824}
displayorder            {23b8de6b-aef4-11dc-a4ce-96509b557824}
                        {7b6febe0-1847-11dd-a64f-0016cfcf51a6}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 30

Windows Boot Loader
-------------------
identifier              {23b8de6b-aef4-11dc-a4ce-96509b557824}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
osdevice                partition=C:
systemroot              \Windows
resumeobject            {23b8de6c-aef4-11dc-a4ce-96509b557824}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {7b6febe0-1847-11dd-a64f-0016cfcf51a6}
device                  partition=C:
description             Ubuntu

---

### Post by ago on 2008-05-02
There should be an entry pointing to wubildr.mbr

---

### Post by LDobie on 2008-05-02
I have the exact same problem.  I am completely new to Ubuntu and decided to try the install on my HP Laptop with Windows Vista as the OS.  The install went without a hitch with Wubi, but when I rebooted, nothing, or nothing had changed.  I did not get a boot menu to choose from.  My laptop just goes reight into Vista.  I can see the Ubuntu install, but I cannot launch it.

---

### Post by ago on 2008-05-02
You can use EasyBCD to check the bootloader entry and/or add new items such as Wubi.

We are aware that in some cases BCD editing does not work, but have been unable to track down the issue so far.

---

### Post by ago on 2008-05-02
[https://bugs.launchpad.net/wubi/+bug/195618](https://bugs.launchpad.net/wubi/+bug/195618)

---

### Post by LDobie on 2008-05-06
> **ago said:**
> You can use EasyBCD to check the bootloader entry and/or add new items such as Wubi.

We are aware that in some cases BCD editing does not work, but have been unable to track down the issue so far.
Using EasyBCD, I was able to determine I had two items listed in the Boot Loader, one for Vista and one for Ubuntu.  However, in re-booting the machine, my laptop always by-passed the boot loader and went right into Vista.  I solved the problem by installing EasyBCD's IReboot utility, which can be found under the "Useful Utilities" menu in EasyBCD.  Once installed, the Vista Boot Loader appeared on start up, and I was able to choose and load Ubuntu.

---

