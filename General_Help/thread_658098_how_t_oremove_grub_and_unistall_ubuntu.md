---
title: "how t oremove grub and unistall ubuntu"
date: 2008-01-04
forum: General Help
---

### Post by animetauren on 2008-01-04
i just recently installed ubuntu on an external hard drive so i can have both windows  and ubuntu at my will to use when i choose. a day after i installed it i turned my computer on and would load xp it said grub error but when i connected the external hdd it booted up ubuntu from ther but my files are still in my comp's hard rive how do i fix this problem and my xp came pre-installed in my computer so no i can't load the cd to bot from it and i still want to keep my files becauase i have a couple of gig's of music and videos there which i cannot afford to lose at no cost

---

### Post by jespdj on 2008-01-04
Aha. So you installed Ubuntu on an external harddisk. Well, GRUB, the bootloader, was installed on your internal harddisk, and when you don't have the external disk connected to your computer, GRUB will complain because it can't find its configuration files etc.

Have a look at this: [Windows Recovery Console](http://support.microsoft.com/kb/314058)
You need to boot into the Windows recovery console and then use the **fixmbr** command to restore the Windowsd Master Boot Record on your internal harddisk.

Also, try searching the forums here for "remove grub" or "fixmbr" and you'll find more info.

---

