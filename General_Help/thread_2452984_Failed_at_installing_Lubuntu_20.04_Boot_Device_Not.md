---
title: "Failed at installing Lubuntu 20.04: Boot Device Not Found"
date: 2020-10-31
forum: General Help
---

### Post by ardouronerous on 2020-10-31
I'm very frustrated and tired. I have scheduled myself to do a clean install from Lubuntu 18.04 to 20.04.1. The install process went smoothly, then I restarted my system. Upon boot up, I got this message:

[IMG]https://www.diskpart.com/articles/images/boot-device-not-found-hp-4125/boot-device-not-found.jpg[/IMG]

I have used Lubuntu from 12.04 onwards and never have I ever experienced this message before. After two failed attempts at installing, I decided to reinstall Lubuntu 18.04. Now, during the reinstalling of 18.04, I saw that 20.04 was installed on my SSD since the installer asked me if I wanted to install 18.04 alongside 20.04, so I decided to erase the entire disk and install 18.04.

This experience has soured me on upgrading to Lubuntu 20.04 for now. This experience has caused to experience an anxiety attack and I was praying to God that the reinstall of 18.04 will succeed, which it did, thank goodness.

I don't know what happened here. All I know is, Lubuntu 20.04 doesn't boot on my laptop, which is a HP ProBook 450 G2, but Lubuntu 18.04 does.

This is a very frustrating experience, especially coming from a LTS release. For now, I'm thinking about trying out Xubuntu, but I want to try to install Lubuntu 20.04, because I've been using it for years.

---

### Post by jp734 on 2020-11-01
Hello. Sorry for the experience you are having but it's hard to understand what is causing without enough information. The next time you try to install 20.04 and get the same result, I would recommend booting from a live media and check grub entry, run "blockid" and make sure everything is the way it should be. The other thing I can suggest is if installing 20.04 again doesn't work, install 18.04 alongside 20.04 and see if grub will detect 20.04 and create a grub entry and let you boot. Let us know and give more detail. Good luck.

---

### Post by GhX6GZMB on 2020-11-01
The main thing that happened with 20.04 is of course the change to LXQt, but that is irrelevant to installation and booting.

The second thing that happened is using the Calamares installer for 20.04.
I suspect your problem lies here. The new installer needs a bit of help when partitioning, particularly concerning formatting and mount points. I encourage you to select "Manual partitioning" when installing.

---

### Post by ardouronerous on 2020-11-01
> **jp734 said:**
> Hello. Sorry for the experience you are having but it's hard to understand what is causing without enough information. The next time you try to install 20.04 and get the same result, I would recommend booting from a live media and check grub entry, run "blockid" and make sure everything is the way it should be. The other thing I can suggest is if installing 20.04 again doesn't work, install 18.04 alongside 20.04 and see if grub will detect 20.04 and create a grub entry and let you boot. Let us know and give more detail. Good luck.

I figured out what the problem was, my laptop was set to Legacy Boot Mode and I switched it to UEFI Native Mode, Lubuntu was able to boot.

> **ml9104 said:**
> The main thing that happened with 20.04 is of  course the change to LXQt, but that is irrelevant to installation and  booting.

The second thing that happened is using the Calamares installer for 20.04.
I suspect your problem lies here. The new installer needs a bit of help  when partitioning, particularly concerning formatting and mount points. I  encourage you to select "Manual partitioning" when installing.

After a couple of hours of using Lubuntu 20.04, I got a headache from the design of LXQt, it sucks, so I switched to Xubuntu 20.04. LXDE is better, they should have improved it instead of switching to LXQt.

---

