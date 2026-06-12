---
title: "windows xp wont boot"
date: 2008-04-26
forum: General Help
---

### Post by mataal on 2008-04-26
hi,

i installed ubuntu 8.04 using wubi on my system, which was like follows,
thinkpad t60, 1 HDD single partition, windows XP SP2.
after an initial hiccup w.r.t. defragmented swap disk, the installation went through fine. 
i spent the day in kubuntu, playing around and apt-getting some stuff.

but, now, i cannot boot my machine back in windows xp! in the boot menu i get options for both but after i select the windows xp option the boot starts and immediately restarts. i've tried 'last known good config' and 'safe mode' but without success. 

Any ideas?

-ashish

---

### Post by ago on 2008-04-26
If you hard-rebooted the machine, that might corrupt the filesystem. It is possible to recover that by running chkdsk /r from the recovery console available on Windows CD or on other rescue CDs available on the web.

---

### Post by Andross707 on 2008-06-05
What if you can't burn a CD? Is there any other way?

---

### Post by duchovny on 2008-06-07
If you can't burn a cd, your options are ... borrow a windows cd from someone or go to the Lenovo site and buy the recovery cd from them.

---

### Post by carolus on 2008-06-08
> **ago said:**
> If you hard-rebooted the machine, that might corrupt the filesystem. It is possible to recover that by running chkdsk /r from the recovery console available on Windows CD or on other rescue CDs available on the web.

Can one completely avoid all risk of corrupting any windows files by using WUBI to install to an external USB hard disk drive instead of to the primary hard disk drive?  Are there obvious installer menu options to do this?

---

### Post by ago on 2008-06-09
The issue is with hard reboot, not with wubi. You can corrput the windows filesystem by hard rebooting even when wubi is not installed. Anyway to install into a usb drive, simply select that from the installation drive listbox.

---

### Post by carolus on 2008-06-09
> **ago said:**
>  You can corrupt the windows filesystem by hard rebooting even when wubi is not installed. listbox.

But not, to my knowledge or in my experience, in such a way as to render Windows unbootable (so that you can't simply run chkdsk /f). Nor have I ever lost files that had been written prior to the hard reboot.  WUBI seems to raise the risk level, at least if writing to the drive that contains Windows. Perhaps installing to an external drive eliminates this risk.

I recognize that files in WUBI are at greater risk than in NTFS or a linux filesystem, but those files can easily be backed up.  Trying to reinstall an OEM version of Windows is a bigger problem.

---

### Post by ago on 2008-06-09
> **carolus said:**
> But not, to my knowledge or in my experience, in such a way as to render Windows unbootable (so that you can't simply run chkdsk /f).
That can happen too. There is a healthy industry thriving on ntfs corruptions out there...

> I recognize that files in WUBI are at greater risk than in NTFS or a linux filesystem, but those files can easily be backed up.  Trying to reinstall an OEM version of Windows is a bigger problem.
I certainly agree but there is not much I can do if people hard reboot or kick their machines...

---

### Post by carolus on 2008-06-09
> **ago said:**
> there is not much I can do if people hard reboot or kick their machines...

Only a few hours ago both of my Windows computers died abruptly.  An air conditioner repairman had flipped the wrong breaker switch. Worse, my Sony laptop has a chronic lockup problem (bad driver perhaps, but no upgrades mentioned on Sony website) that I can fix only by hard reboot.  I have to hard reboot that XP machine as often as I used to with Windows 98, so I have a good sense of what to expect from a hard reboot and NTFS when Linux is not installed. A redeeming feature of that laptop is that it works fine with Linux.

Am I correct in supposing that all risk of Ubuntu-related Windows corruption can be avoided by installing WUBI to an external USB hard drive? In the case of Puppy Linux, I can dual-boot to a USB hard drive without writing anything to the primary hard drive except for using Windows to copy a few files and a Windows editor to edit boot.ini (so that my primary NTFS hard drive is untouched by any Linux program}.  I don't yet understand WUBI or its installer well enough to feel safe with it.

---

### Post by ago on 2008-06-10
> **carolus said:**
> Only a few hours ago both of my Windows computers died abruptly.  An air conditioner repairman had flipped the wrong breaker switch. Worse, my Sony laptop has a chronic lockup problem (bad driver perhaps, but no upgrades mentioned on Sony website) that I can fix only by hard reboot.  I have to hard reboot that XP machine as often as I used to with Windows 98, so I have a good sense of what to expect from a hard reboot and NTFS when Linux is not installed. A redeeming feature of that laptop is that it works fine with Linux.
That simply depends on what file gets corrupted. If it is a file required in the boot process then you cannot boot. 

> Am I correct in supposing that all risk of Ubuntu-related Windows corruption can be avoided by installing WUBI to an external USB hard drive?
When you hard reboot any partition which is mounted is at risk, any partition that is not mounted is safe. So if you install wubi in a different partition where you have no windows or other file then you can hard reboot at will and only risk wubi itself.

---

### Post by carolus on 2008-06-10
> **ago said:**
> 
When you hard reboot any partition which is mounted is at risk.

Even if mounted read-only?

---

### Post by mhousel on 2008-06-17
This is the exact problem I have had except there was no "hard Reboot", I shut down Ubuntu and re-booted XP only to have it wake up dead as described in the first post.

My windoze installation is trashed and un-recoverable without also removing my WUBI installed Ubuntu 8.04 using the recovery CD that came with my laptop.

SO, my question is, can I in any way **move** or otherwise get my **current** WUBI installed Ubuntu 8.04 to another partition?

And can I create that partition without wiping out my current Ubuntu installation?

Thanks

---

### Post by ago on 2008-06-18
> **mhousel said:**
> This is the exact problem I have had except there was no "hard Reboot", I shut down Ubuntu and re-booted XP only to have it wake up dead as described in the first post.

My windoze installation is trashed and un-recoverable without also removing my WUBI installed Ubuntu 8.04 using the recovery CD that came with my laptop.

SO, my question is, can I in any way **move** or otherwise get my **current** WUBI installed Ubuntu 8.04 to another partition?

And can I create that partition without wiping out my current Ubuntu installation?

Thanks


Yes but you will have to edit manually C:\ubuntu\disks\boot\grub\menu.lst so that root/groot points to the right partition and you should be aware that the uninstaller in add/remove software will not work. You will have to use uninstall.exe in ubuntu folder

As for creating a partition the same rules apply as resizing any other windows partition.

You might also consider a full installation to a dedicated partition, as this is the preferred long term solution.

---

