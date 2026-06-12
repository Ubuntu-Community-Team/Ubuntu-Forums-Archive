---
title: "Uninstall XP and Remnant of Ubuntu and leave Xubuntu"
date: 2013-11-01
forum: General Help
---

### Post by glennc on 2013-11-01
Hello to all,
  Short version...... Wanted faster system than Ubuntu, tried several & didn't like. During this time I lost wireless connectivity so installed various Linuxs and XP to try to get wireless drivers working. Ignorance. With the forums on solving that problem which at the time had XP and Ubuntu 12.04 LTS dual booting and crashing on Ubuntu, as I waited for the sage instructions that would eventually save me, I loaded Xubuntu current. During the install, it offered a choice to install Xubuntu over Ubuntu!!! For whatever reason I chose this option. Your forums membership and moderators solved my wireless problem in like 30 seconds.....
An hour ago the machine boots to grub and shows the Xubuntu and recovery, an unknown Linux installation and the XP and recovery.
Watching a youtube I installed GParted. and it showed the Windows partition, and a second partition containing an extended, area of ext4 and a swap. I deleted the Windows partition and the Linux/Linuxes section would not allow a resize. The choice was greyed out. I did the delete XP, I formatted it ext4, nothing I've done has allowed GParted to give me a resize command.
  I wish to resize and then remove the grub loader and use Xubuntu as the only OS. While waiting for the forums excellent help, I set up all my accounts and programs and updates and more update. Would prefer not to have to reinstall. Plus I'm afraid I am going to loose wireless again. Normally not a problem but the little lady wants to get online!!!!
Thanks for any and all assistance!
glennc

---

### Post by Impavidus on 2013-11-01
You installed gparted. As it's installed by default on a live disk, I assume you try to run it from the installed Xubuntu. But you cannot modify the partitions mounted by a running system. Boot from a live disk and run gparted from there. If it still refuses to resize, disable the swap partition. In gparted, right-click on the swap partition&#8594;swap off, IIRC.

---

### Post by glennc on 2013-11-01
> **Impavidus said:**
> You installed gparted. As it's installed by default on a live disk, I assume you try to run it from the installed Xubuntu. But you cannot modify the partitions mounted by a running system. Boot from a live disk and run gparted from there. If it still refuses to resize, disable the swap partition. In gparted, right-click on the swap partition&#8594;swap off, IIRC.

Hello Impavidus, 
   Well that certainly makes sense, and thank you for this insight!! Cool. I will give it a try!
Much appreciated
glennc

---

