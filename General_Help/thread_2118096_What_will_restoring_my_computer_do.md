---
title: "What will restoring my computer do?"
date: 2013-02-20
forum: General Help
---

### Post by Solunaka on 2013-02-20
first of all, i just made my forum account so hi ):P

but my point is: will linux be deleted if i restore my computer to factory settings?

---

### Post by Sylos on 2013-02-20
> **Solunaka said:**
> first of all, i just made my forum account so hi ):P

but my point is: will linux be deleted if i restore my computer to factory settings?

I assume you mean restoring it by using the menu entry just after you boot (before the operating system loads)?

If this is the case then yes - restoring will result in wiping of Ubuntu and any other changes you have made to the disk. I think it will resest the partition table to what it was originally.

Cheers

---

### Post by Solunaka on 2013-02-20
okay, and yes it is from the boot menu. so I am wondering if it will also reset partitions

---

### Post by fedine on 2013-02-20
I am not quite sure, cos never actually tried it, but boot menu options refer to the boot menu only, not the hard drives, their partitions or any other part of the pc. So, if you select factory settings, you deleted and restore settings that you changed at the boot menu, but do not affect anything else. Besides, to get to the boot menu, your pc has done nothing yet but only seeing he BIOS, checked (probably) basic functionality and give you the option to select some OS-independent things, like boot devices priority (cd, usb, hard drive, etc.). Hard drives are not supposed to have been read yet.

---

### Post by auxilium on 2013-02-20
Hi,

If the Restoration Process will wipe the whole disk and return back all the settings to factory default, then it would be lost.

Depending on the options the Restoration Process will give to you will give different result. I suggest you choose wisely, may it be your last decision. Better back up important things before giving a shot.



Cheers,

---

### Post by Paddy Landau on 2013-02-20
auxilium is right: we don't know, because each OEM (manufacturer) decides its own system.

Also, I am presuming that you have a Windows computer.

But, based on experience, a factory-level restore almost certainly will erase *everything* in your computer, and reset the partitions.

I suggest that you make a full backup; and make a second backup on a diffferent medium (in case the first backup fails &#8212; yes, it does happen!). Be sure to back up the data from both your Windows and your Ubuntu (and any other operating system that you may have).

After doing a factory-level restore, you will have to reinstall Ubuntu; run all the updates; and finally restore the data from your backups.

If you back up your entire home folder **including** the hidden files and folders, this will include all your settings. Restoring those hidden files and folders means that you won't have to go and fiddle with all your settings again. If you need help in backing up and restoring your hidden files and folders, just ask.

---

### Post by grahammechanical on 2013-02-20
Hi and welcome to the forums.

It would be best if you gave us the exact information that the computer is giving you. Perhaps you could read what the motherboard user guide says about this function. And put the information here.

I doubt very much if setting the motherboard back to factory defaults will delete what is on the hard disk. Do not take my word for it. I do not have your motherboard manual. Just disconnect the hard disk.

My motherboard BIOS (Basic Input Output System) has an option in its Exit menu - Load Setup Defaults. This is the explanation:

> This option allows you to load the default values for each of the parameters on the setup menus. When you select this option or if you press <F5>, a confirmation window appears. Select YES to load default values. Select Exit & Save Changes or make other changes before saving the values to non-volatile RAM.

My hard disk partitions are not set in my BIOS. I never had to set anything in my BIOS to set hard disk partitions. I built this machine myself. I just plugged in the hard disk and installed Ubuntu on - Use entire disk option.

what information have you been given by the motherboard user guide? Why do you need to do this? Perhaps the best place to ask this question is on a forum by the computer maker.

Regards.

---

### Post by Mark Phelps on 2013-02-20
As folks have already mentioned, we're all just guessing what a restore will do because every OEM's restore operation is a bit different.

Disrupting factors (stuff that prevents restore from working) include the presence of Ubuntu on the drive (being a filesystem that Windows does not understand) and/or the resizing of partitions to be different sizes from the original (as in, shrinking the Windows OS partition to leave room for Linux partitions).

There have been cases where either of these prevented the restore from working properly, or from even running!

So, in the cases that the restore works, the most common scenario is that Ubuntu is erased in the process.

---

