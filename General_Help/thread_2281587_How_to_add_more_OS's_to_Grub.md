---
title: "How to add more OS's to Grub"
date: 2015-06-08
forum: General Help
---

### Post by robertzito on 2015-06-08
I have been running grub to boot y laptop for about 3 yrs now. When I installed Ubuntu I I used WUBA and did a dual boot between win7 and ubuntu 14.04. The question is, how can I add another OS to grub if I want to add the operating system like OpenSUSE 13.2? I know I can do it via VM but I would like to boot up interdependently, can you add more OS's to grub and how?

---

### Post by sudodus on 2015-06-08
Wubi is no longer developed and supported, because it does not work with Windows 8 and newer. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229766"]
Forums Staff recommendations on WUBI[/URL]

Instead, I suggest that you create a real dual boot system by installing Ubuntu alongside Windows instead of using wubi. You can prepare for that installation by backing up your system, testing some linux distros live and editing the partitions when booted from an Ubuntu install DVD or USB drive.

Use ***gparted*** to edit the partitions.

In the installer, at the partitioning window, you can select **Something else**, and select the partition(s) that you created with gparted.

See these links and links from them for more details

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

