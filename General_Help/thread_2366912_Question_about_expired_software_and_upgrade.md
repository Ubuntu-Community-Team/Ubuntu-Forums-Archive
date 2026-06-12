---
title: "Question about expired software and upgrade"
date: 2017-07-23
forum: General Help
---

### Post by elvis6 on 2017-07-23
I got the prompt that says my software is no longer supported, and it gives me the option to upgrade.
It's currently running Ubuntu 12.04.
My questions are regarding how the upgrade is affected if I have Ubuntu running as a dual OS, and originally installed by WUBI.
In that situation, will I still be able to upgrade through the link provided ?
Second question is, will I still be able to keep the new upgrade running as a dual OS, or will it just replace both OS's ?

---

### Post by lisati on 2017-07-23
12.04 is past its end-of-life, and WUBI hasn't had active support for a long time. It might be necessary (and ultimately easier) to do a clean install of a newer version of Ubuntu in a separate partition. Don't forget to make backups of important data first.

---

### Post by vocx on 2017-07-24
> **elvis6 said:**
> I got the prompt that says my software is no longer supported, and it gives me the option to upgrade.
It's currently running Ubuntu 12.04.
My questions are regarding how the upgrade is affected if I have Ubuntu running as a dual OS, and originally installed by WUBI.
In that situation, will I still be able to upgrade through the link provided ?
Second question is, will I still be able to keep the new upgrade running as a dual OS, or will it just replace both OS's ?

Ubuntu has long term support (LTS) versions that are supported for 5 years. Ubuntu 12.04 was released on April 2012, and it already reached its end of life. You should have upgraded years ago to a more recent LTS version, such as 14.04, or 16.04, unless you have a reason for not upgrading. Usually only power users running servers keep old versions working. Normal users should upgrade their system more regularly, for example, every two years, which is the release schedule of the LTS versions.

1. I never used Wubi, so I don't know exactly what it installs and how. As mentioned, it is no longer developed or used.
2. Does Wubi install anything out of the ordinary in Windows? If it does, then you should probably remove it before performing an upgrade. If it was just used in the installation of Ubuntu, and never used again after that, then it probably does not affect the upgrade of Ubuntu.
3. When you installed the two operating systems, I am assuming a Windows and Ubuntu, are they in separate disk partitions? If this is the case, when you upgrade Ubuntu, it will only update the files in its own partition. It does not need to touch the other partitions. So, no, it will not replace both OSes, only one.
4. As you have a very old version of Ubuntu, you would probably need to upgrade first to 14.04, and then to 16.04. This may take a long time downloading files, and setting up the system. Depending on what kind of personal data you have, you may wish to back it up in an external hard drive, and perform a fresh install instead.

Performing a fresh install may bring your system to a modern version quicker, while at the same time clean up the clutter that your system may have accumulated in over 5 years. Of course, if you heavily customized your system with packages, themes, wallpapers, bookmarks, and things like that, those things would have to be recreated in the new installation.

Performing an upgrade will only modify your system folders, and should not touch your personal files in "/home". Performing a clean installation will overwrite the entire system, including "/home", so you would need to back up these files first. And again, an upgrade or fresh install should only affect the existing Ubuntu partition, without affecting the other Windows partition.

---

### Post by deadflowr on 2017-07-24
From memory wubi is a Windows Program and what it does is creates a virtual hard drive file (like vdi or some other virtual hard drive) on Windows and then creates a special boot menu entry in Windows boot manager.

Two possibilites to move away from wubi are either to run a backup of the Ubuntu then create a new partition for Ubuntu and reinstall and restore the backups
or you may be tempted to try the wubi migration utility:
[https://help.ubuntu.com/community/MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi")
of course the migrate tool also requires having a ready to use partition.

Personally I would do a backup and restore.

---

### Post by Skaperen on 2017-07-24
i would suggest two hard drives, one for windows and one for linux/ubuntu.  then i also suggest running windows in a virtual machine under linux/ubuntu.

---

### Post by Autodave on 2017-07-24
How large is your HD and how much free space is on it?

---

### Post by unityforever on 2017-07-24
there was a time i was using expired version and when i check the update all of the servers in the world deny me...

(i wish one of the forum administrator would modify my post and fix my grammar error, thanks)

---

### Post by hakuna_matata on 2017-07-27
> **elvis6 said:**
> 
In that situation, will I still be able to upgrade through the link provided ?

I know that there are users who upgraded successfully a Wubi installed Ubuntu from 12.04 to 14.04 with [software updater.]("https://tutorials.ubuntu.com/tutorial/tutorial-upgrading-ubuntu-desktop") But a workaround has been necessary since Ubuntu 14.04. For further information see [https://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted](https://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted) 
Maybe, it is also helpful to install a [Wubiuefi]("https://github.com/hakuna-m/wubiuefi/wiki") script which patches initramfs before upgrading. see [https://github.com/hakuna-m/wubiuefi/issues/5#issuecomment-211083990](https://github.com/hakuna-m/wubiuefi/issues/5#issuecomment-211083990)

> **elvis6 said:**
> 
Second question is, will I still be able to keep the new upgrade running as a dual OS, or will it just replace both OS's ? 

It does only affect Ubuntu and it doesn't upgrade Wubi installer on Windows.

My post should be not a general recommendation for an upgrade of a Wubi installed Ubuntu. There are better options as other users wrote above. But if you plan to keep the unsupported 12.04, the upgrade is not the worst option.

---

