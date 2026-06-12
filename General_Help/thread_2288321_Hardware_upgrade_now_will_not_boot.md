---
title: "Hardware upgrade now will not boot"
date: 2015-07-26
forum: General Help
---

### Post by halfprice5 on 2015-07-26
I had an old dell 270 running ubuntu 14.04.

I pulled that drive and installed it in a core 2 quad core hp and now it will not boot.

I've searched and can not seem to find an answer on how to fix it.

Any suggestions?

---

### Post by grahammechanical on 2015-07-26
If you give some detail on what is meant by "will not boot" then we might be able to guess what the problem is.

You had a Linux operating system with driver modules for one machine and now you want the same OS to run in a different machine without having the driver modules for that machine installed.

In the old machine were you using a proprietary video driver? Did you switch to the open source video driver before removing the hard drive from the machine? Does the new machine have the same video adapter as the old machine? Or is it a different model?  Is it of the same manufacturer or of a different brand?

At the Grub boot menu select Advanced options for Ubuntu and select Recovery mode. Then select Resume. If that gets you to a desktop go to System Settings>Software and Updates>Additional Drivers tab.

I am guessing that this is a video driver problem but without more detailed information a guess is the best that anyone can offer.

Regards.

---

### Post by Vladlenin5000 on 2015-07-26
Dell 270 were shipped with several different graphics chips/card. Dell lists 6 different drivers/hardware for the 270 model:

```
ATI 64MB PCI-Express x16 (DVI/TV-out) Radeon X300 SE, 128MB PCI-Express x16 (Dual VGA or DVI) Radeon X300
Intel 82865G Graphics Controller
ATI 128MB PCI-Express x16 (Dual VGA or DVI) Radeon X300
Intel 845 G/GL Integrated Video, Springdale G Integrated Video, Intel Grantsdale G Integrated Video
nVidia 64MB DDR nVidia GeForce4 MX
nVidia 128 MB DDR Nvidia GeForce FX 5200
```

Indeed, if you had nVidia or ATI with a (legacy) proprietary driver, you won't have video when booting with the new hardware. Not really a bad thing because:
 - Better to do all the required backups and do a fresh install anyway.

---

### Post by halfprice5 on 2015-07-26
the dell It has agp ATI card for video, no proprietary drivers. I checked to make sure before swapping the drive.

The HP has nvidia pcie

I get the 14.04 splash screen then the screen goes blank and remains there.

I never get to a point to access grub,

---

### Post by Vladlenin5000 on 2015-07-26
It's the new nvidia then... It probably requires the *nomodeset* parameter in Grub.
The Grub menu usually don't show up in a single OS installation. I guess you need to press SHIFT right after post. Then you'll be able to edit the entry that boots Ubuntu and add *nomodeset.* Next step: Install the proper drivers for your nvidia card, then you'll have normal video.

Again, booting a live session, doing your backups and making a fresh install is certainly a much better use of your time.

---

### Post by halfprice5 on 2015-08-09
Sorry for the delay in thanking you for your help. Had a hospital stay.

Did a backup and restore, worked for a while have another problem now. Will post in another question.

---

