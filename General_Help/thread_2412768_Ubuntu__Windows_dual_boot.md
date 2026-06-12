---
title: "Ubuntu / Windows dual boot"
date: 2019-02-17
forum: General Help
---

### Post by PeterB1945 on 2019-02-17
I have had Ubuntu 18.04 LTS running in a dual boot setup with Windows 10 for a few months - Windows 10 was installed on the Acer Aspire 5 laptop I bought.

Yesterday in shutting down Windows it said it was installing an update and would then shut down, so I left it run to do so. I restarted the computer not paying much attention to the screen and expecting Ubuntu to load as usual, but I got Windows instead, which runs OK (version 10.0.17134 now). On investigation it appears the dual boot is no longer available, only the Windows boot.

Restarted Ubuntu from the thumb drive I originally used to install it, hoping that the dual boot would be restored when the existing Ubuntu was found. Instead I was given the options of
[LIST]
[*]erasing the existing Ubuntu including all data, files, programs etc
[*]erasing the whole disk and installing Ubuntu
[*]trying my hand at reallocating disk partitions, presumably losing everything in the process
[/LIST]

I far prefer Ubuntu to Windows, but unfortunately there are some Windows only programs I need to use for the moment.
So to save having to reinstall and customize programs, get back files form archives, etc, etc is there any way of restoring the dual boot without losing all my Ubuntu stuff? Or Windows stuff for that matter.

---

### Post by Impavidus on 2019-02-17
Assuming this is a UEFI system (preinstalled Windows 10 should be), have you tried to boot Ubuntu from the UEFI menu? If that doesn't work, try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). First create the summary and show us the link, so we can see what's going on. Although I think the default repair will probably fix this.

---

### Post by westie457 on 2019-02-17
Check the options inside Windows, make sure fast startup is definitely off.
If that does not fix it follow the advice in post 2.

---

### Post by yancek on 2019-02-17
> 
Yesterday in shutting down Windows it said it was installing an update and would then shut down,

Most or at least some windows updates will turn on hibernation/fastboot so be aware of this in the future and check it after the update finishes.

---

### Post by ajgreeny on 2019-02-17
It is also possible that the partition table has been rewritten by Windows, but the Linux partitions ignored; they are probably still on disk but not found when you boot.

See the thread at [https://ubuntuforums.org/showthread.php?t=2382034](https://ubuntuforums.org/showthread.php?t=2382034) for some more info, and hopefully a solution for you.

---

