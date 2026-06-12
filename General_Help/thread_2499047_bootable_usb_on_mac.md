---
title: "bootable usb on mac"
date: 2024-07-09
forum: General Help
---

### Post by lubuntero on 2024-07-09
hi everyone

I tried to make a bootable external hard disc with Lubuntu.
I tried with Balena and unetbootin.
This with a mac mini 2014 12.7.5
Both failed.
With Balena everything runs and it shows finished.
In Disk Utility the hard disc shows bootable no after.
With unetbootin it runs normal.
Same result in Disk Utility.

After it was so called done, I tried to install Lubuntu on a barebone.
The barebone shows no bootable media inserted.

The barebone is completely new.
What am I doing wrong?

---

### Post by currentshaft on 2024-07-09
I'm not entirely sure what you're trying to do - create a USB installer for Lubuntu? You don't need any third party tool for that.

wget [https://cdimage.ubuntu.com/lubuntu/releases/24.04/release/lubuntu-24.04-desktop-amd64.iso](https://cdimage.ubuntu.com/lubuntu/releases/24.04/release/lubuntu-24.04-desktop-amd64.iso)
sudo dd if=lubuntu-24.04-desktop-amd64.iso of=/dev/<path to usb device> bs=4m

---

