---
title: "Using Time-shift to create 'a custom image' of ubuntu install"
date: 2022-10-07
forum: General Help
---

### Post by mikber18 on 2022-10-07
Hi All, 

I have been using Ubuntu for a number of months now and its been an amazing experience - mostly because I've finally learnt about timeshift and the regular backup. Timeshift has saved my butt a number of times now and its been great. 

The other question I had, is there a way where by I create a fresh ubuntu install on another PC, but could I use timeshift then to 'restore the image' of my current daily ubuntu leading me to the same user experience as my main daily rig without all the fuss of having to install all the software again and again? 

Is this something that is possible with time shift and if so, how do I do it? A little bit like windows users might create a customer ISO with their windows install to save them the fuss of installing all the updates time and time again.

Many Thanks,

---

### Post by yancek on 2022-10-07
I'm not familiar with timeshift but what you describe should be doable with systemback, see the link below.

[https://www.alibabacloud.com/blog/a-quick-guide-to-using-systemback-for-ubuntu-backup_595818](https://www.alibabacloud.com/blog/a-quick-guide-to-using-systemback-for-ubuntu-backup_595818)

Thee link below explains the options available with timeshift.

[https://www.makeuseof.com/use-timeshift-backup-and-restore-linux-snapshots/](https://www.makeuseof.com/use-timeshift-backup-and-restore-linux-snapshots/)

---

### Post by #&amp;thj^% on 2022-10-07
> **mikber18 said:**
> Hi All, 


The other question I had, is there a way where by I create a fresh ubuntu install on another PC, but could I use timeshift then to 'restore the image' of my current daily ubuntu leading me to the same user experience as my main daily rig without all the fuss of having to install all the software again and again? 

Is this something that is possible with time shift and if so, how do I do it? A little bit like windows users might create a customer ISO with their windows install to save them the fuss of installing all the updates time and time again.

Many Thanks,
If I understand you correctly, then yes you can do that.
In fact if you install "Timeshift" on the Live Installer, you can restore from your back-ups created by Timeshift
So you would want to make an image of the desired OS before hand.

---

### Post by mikber18 on 2022-10-07
> **1fallen said:**
> If I understand you correctly, then yes you can do that.
In fact if you install "Timeshift" on the Live Installer, you can restore from your back-ups created by Timeshift

Thanks for that I will take a look. 

What I have just learnt - through messing around with Linux, like you usually do - is that I can revert a version of Linux install with Timeshift. I upgraded to the the 22.10 Beta install which has changed so much of the way in which my Ubuntu looks that I didn't like it, but I was able to use timeshift to revert back to the pre-beta installation image and my linux looks exactly as I like it again.

---

### Post by ne29914 on 2022-10-07
> **mikber18 said:**
> Hi All, 
The other question I had, is there a way where by I create a fresh ubuntu install on another PC, but could I use timeshift then to 'restore the image' of my current daily ubuntu leading me to the same user experience as my main daily rig without all the fuss of having to install all the software again and again? 

You can, but it's not straightforward.

The issue is, that the Timeshift image contains references to the partition UUIDs in some files, and if you just do a Timeshift restore on the new machine it will refuse to boot.

You have two options:

1: change the UUIDs on the new machine to the old ones from the backup. Then you'll have a clone. Not the nicest option.

2: either A: exclude restore of the relevant files on the new machine, or B: modify them to the new UUIDs. Both have the problem that you don't know exactlywhich system files contain the UUID. One file is certain: /etc/fstab. but also /etc/default/grub and etc/initrams-tools/conf.d/resume may be affected, plus other files depending on what you've installed/configured.

2A is the easiest, but will remove all system functions needing UUID, eg, hibernate. 2B demands a second live boot after restore to sudo edit the mentioned files. Best option, but more involved.

It's a bit of a Catch-22.

Good Luck.

---

### Post by vanadium on 2022-10-08
Installing an operating system to a computer is not just copying files. There is also system specific configuration involved, although allegedly, the kernel does a lot of auto configuration. Pointers are also created:  ne29914 referred to the system of UUIDS, universely unique identifiers. You read that righ: "unique". Each partition is assigned a long random string that serves as a unique reference for that individual partition on disk.

So no, copying files, what Timeshift does, will not cut it ( would say - at all). Directly restoring a full diskimage to another system (this also transers UIDS) has some chance to work, but that will also come with complications unless the computers are very similar.

There are official ways to create custom installation media. You tweak a system, create an installation medium and that can then be used to install a system on another computer that will look and behave the same. This is the only way you should pursue.

Alternatively, a lot of configuration transfer can be achieved by taking note of the programs you added so these can quickly be installed on the newly installed system. Tweaking of a desktop happens on a per-account basis, and is stored in user configuration, i.e., the hidden files and directories in the user's home directory. These can be transferred without issues to a new computer if that computer runs the same software versions. If the software versions are different, there is a (relatively slight) chance that the "old" configuration will cause some issues.

---

### Post by ian-weisser on 2022-10-08
> **vanadium said:**
> Alternatively, a lot of configuration transfer can be achieved by taking note of the programs you added so these can quickly be installed on the newly installed system.

This is great advice, and how I have handled customization for over a decade. All my changes are in a (maintainable) script that's trivial to run after the first boot, simple to audit after new releases. The script also includes lots of comments --documentation for the source of each change and how to undo each step-- to make troubleshooting easier.

I've found custom-install-with-all-changes-pre-baked to be super-easy to install but sometimes brittle and sometimes difficult to troubleshoot when something breaks. Custom-image creation can be a fun hobby and learning experience (been there!), but I find myself going back to the tested defaults and my script for reliability and maintainability.

---

