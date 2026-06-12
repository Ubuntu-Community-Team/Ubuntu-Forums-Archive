---
title: "Installation Results: Kubuntu 0, Ubuntu 1. What could the difference be?"
date: 2013-04-30
forum: General Help
---

### Post by Roasted on 2013-04-30
I have a laptop that came with Windows 8. I disabled UEFI and installed Ubuntu. At first I had trouble installing 13.04. Well, let me rephrase that. I had trouble booting to Ubuntu 13.04 after installing it successfully. Eventually I did guided partitioning (I've done manual partitioning for many years) and it worked great. I noticed Ubuntu added an EFI boot partition, so when I redid my manual partitioning I duplicated those efforts and Ubuntu 13.04 booted without a single hiccup.

In an effort to check out Kubuntu 13.04, I took an image of my drive for safe keeping and installed Kubuntu 13.04 on this laptop. The installation failed each time, citing something about grub-efi. I had duplicated the same efforts in the Kubuntu install that I did in the Ubuntu install. Same partition layout, same mount points, boot flags, etc. I even tried installing Kubuntu with guided partitioning on 3 occasions, no dice.

One suggestion said that on the LiveUSB session, to connect to the internet and apt-get install a few packages. I can't recall them offhand, but it was something like grub-efi, grub-efi-64, and grub-efi-64-bin... then afterwards run the installer. No dice.

On top of that, I was disappointed to see that my brightness controls in Kubuntu acted incredibly strangely. For example, Brightness Down = Down, but Brightness Up = Down (90%), Down (80%), Down (70%), etc etc etc. Eventually you hit 0% and the screen is black, all while hitting Brightness UP... then if you keep hitting Brightness Up, it will go from 0% to 8%, then 4%, then 0%, then 8, 4, 0, 8, 4, 0. So if I start off on 100% brightness, down will bring it down, up will bring it down, then once I get to 0% up will bring it back to 8%, then down to 0, up to 8, down to 0, etc. In Ubuntu this worked perfectly.

For the time being I am on Ubuntu 13.04 since at the end of the day I need a working system, but I would really love to revisit Kubuntu 13.04 on this unit. Can anybody offer some insight as to how I might be able to make that a reality?

---

### Post by zero2xiii on 2013-04-30
Hay,

This is strange.. But try installing the kubuntu desktop alongside gnome and see what happens?

```
sudo apt-get install kubuntu-desktop
```

I think that should do it.

Cheers

---

### Post by Roasted on 2013-04-30
That's actually what I did at first, but I noticed my brightness controls were terribly messed up. In an effort to troubleshoot it I wanted to try a full Kubuntu environment without Ubuntu, which is why I tried to do a fresh install of it, but like I said above, it failed miserably.

Some discussions in the Kubuntu IRC channel suggested that Kubuntu may not have "proper" UEFI support yet - even though I'm trying to install with UEFI disabled in the BIOS... :(

---

### Post by zero2xiii on 2013-04-30
Hay,

 Then I have no idea.... I was only trying to give an alternative than installing a full new Kubuntu install. Not sure how it does not have "Proper" support as it basic is ubuntu with a different DE. Might be something deeper under the hood. Cant really be sure.


Maybe some one else has a better idea. You did check the kubuntu install's integrity?

Cheers

---

### Post by Roasted on 2013-04-30
> **zero2xiii said:**
> You did check the kubuntu install's integrity?



Yep. Even tried installing via DVD as well (burned at slowest speed of course), but LiveDVD and LiveUSB flash drive both failed, yet passed integrity checks.

Fun fact - The LiveUSB just successfully installed and booted on an ultrabook I have here, but it of course came with Windows 7 originally. Definitely seems like a UEFI issue of some sort. (Damn you, Microsoft)

---

### Post by zero2xiii on 2013-05-01
Wow,

This really is strange. Unfortunately I have very little knowledge of UFEI and related so I can not even guess on what the issue might be. Sorry.

Good luck though.

---

