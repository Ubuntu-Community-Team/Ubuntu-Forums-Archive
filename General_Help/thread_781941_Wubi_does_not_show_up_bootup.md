---
title: "Wubi does not show up bootup"
date: 2008-05-04
forum: General Help
---

### Post by joe056 on 2008-05-04
I have successfully installed ubuntu using the wubi installer, but my computer goes straight to vista whenever I turn it on.  I am running Vista on a Fujitsu Lifebook A series laptop.  Everything worked fine on the LiveCD, so I don't know what the problem is.

Thanks.

---

### Post by ago on 2008-05-04
Use EasyBCD to check the Vista boot menu.

---

### Post by joe056 on 2008-05-04
I checked out EasyBCD, and there was only one option listed in the Vista Bootloader: Windows Vista.  Was the Wubi installer supposed to add the second option automatically?  

My laptop came with a second partition (~1GB) that is mostly empty.  Would this cause an issue?  Do you know why they would add this extra partition in the first place?

Thanks so much.

---

### Post by ago on 2008-05-05
> **joe056 said:**
> I checked out EasyBCD, and there was only one option listed in the Vista Bootloader: Windows Vista.  Was the Wubi installer supposed to add the second option automatically?
Yes, normally a Ubuntu entry should be there to. There are some cases where in Vista this does not happen (being addressed). 

You can still use easybcd to add a Wubi entry

---

### Post by joe056 on 2008-05-06
I added the Wubi option using EasyBCD like you said, and now when I reboot the computer, I have the option to go to Wubi.  However, when I select the option, the computer takes me to the Grub4DOS command line.  Do you know what I should do from there?

---

### Post by ago on 2008-05-06
Do you see any error message? Please post it here as it is written (or take a screenshot).

You can also press INSERT immediately after selecting "Ubuntu" to get a more verbose output

---

### Post by joe056 on 2008-05-06
The error message flashes up so quickly that I can't even read what it says.  I select "Wubi 8.04" from the text based boot manager.  Then the error message flashes for less than a second.  Then the computer enters grub4DOS.

Do you know how I can get the error message to hold so I have time to write it down?

This is what Easy BCD has for my boot file.

```

Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=C:
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {833a75b4-83ef-11db-aeb9-00174215ea2b}
resumeobject            {833a75b5-83ef-11db-aeb9-00174215ea2b}
displayorder            {833a75b4-83ef-11db-aeb9-00174215ea2b}
                        {8d2d42e7-8315-11dc-8d1a-001742633367}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 30

Windows Boot Loader
-------------------
identifier              {833a75b4-83ef-11db-aeb9-00174215ea2b}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
recoverysequence        {572bcd56-ffa7-11d9-aae0-0007e994107d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {833a75b5-83ef-11db-aeb9-00174215ea2b}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {8d2d42e7-8315-11dc-8d1a-001742633367}
device                  partition=C:
path                    \NST\NeoGrub.mbr
description             Wubi 8.04

```

Thanks again.

---

### Post by joe056 on 2008-05-07
I tried reinstalling it, and the same thing happened.  Do any of you guys have ideas as to what the problem might be?

---

### Post by ago on 2008-05-08
A new wubi build will be out in the coming days which might address the above

---

