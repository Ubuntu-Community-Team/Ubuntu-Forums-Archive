---
title: "Xubuntu 24.04 impossible to use"
date: 2024-06-24
forum: General Help
---

### Post by lapetesson on 2024-06-24
I want to use Linux to test PC hardware when Windows malfunctions. The idea is to boot Linux from a USB stick. 

After initial experiments with Ubuntu, I decided to try Xubuntu with persistent partition. I prepare the USB stick using an Xubuntu ISO file and Rufus. I use a 32GB stick, and I set aside a varying capacity for persistent partition; I've tested 10, 5, and 4GB.

The results of the Xubuntu 24.04 tests are disastrous. Xubuntu boots, but response times are enormous. It takes a minute to open a terminal or to run ps or ls. It took around an hour to start Firefox. In the ps-e printout, a few processes have non-zero TIME, with Xorg consuming the most time, followed by systemd and firefox. The accumulated execution time of all processes after a two-hour operation is around 1 minute, but the system stands still.

The computer I'm using to test Xubuntu works normally under Windows.

Has Xubuntu 24.04 known problems? Have I missed something essential?

I have little Linux experience but many years of work with Unix, including delivering courses on Unix internals. But it was quite a few years ago.

---

### Post by Rubi1200 on 2024-06-24
Obviously, things are going to be slower on a live USB. But an hour for Firefox to open? I have personally never experienced this even on older hardware.

We really cannot help you look into this without knowing the full specifications for your computer.

Posting that would be a good first step.

---

### Post by grahammechanical on 2024-06-24
On the subject of creating a ISO image on a USB stick with persistence.

The Ubuntu 20.04 LTS has an option for a minimal install. I do not know if the Xubuntu 24.04 LTS installer offers the same option. The minimal install gives a desktop environment + Web browser + basic utilities including terminal.

The minimal install option seems to me to be ideal for creating a diagnostic USB stick. A lighter (less memory intensive) browser can be installed along with the users choice of diagnostic utilities. 

Regards

---

### Post by oldfred on 2024-06-24
I recently installed Kubuntu to several drives.
I prefer full installs.

My full install to an older smaller flash drive took almost an hour.
Install to a newer larger flash drive took almost half an hour.
And full install to an external SSD took about 12 minutes which is almost as fast as full install to internal SSD.
All installs were from RAM (using toram parameter) to same USB3 port.
Or type of drive can make a huge difference. 

There are some settings like noatime to reduce write, but with live installer you cannot easily change settings

---

### Post by nicolasdentremont on 2024-06-24
Some USB Flash Drives are very slow. I have a cheap 32Gb flash drive that's way too slow to be used for an install drive let alone as a live USB. And Xubuntu does have a minimal install option that comes without all the extra stuff so you can really pick exactly what programs you want.

---

### Post by lapetesson on 2024-06-25
[B]Partly solved.
[/B]
When you create the Xubuntu USB stick in Rufus **without the persistent partition**, Xubuntu works normally. It is slow to load, but when it's in RAM, it's normally fast. The persistent partition disturbs Xubuntu in some way, or Rufus does something wrong with it. I'm not trying to dig into it any further.

Also, creating an Xubuntu stick **without **a persistent partition is a lot faster. You quickly format the stick as FAT32 in Windows, and Rufus simply transfers Xubuntu onto it. If you do have a persistent partition, Rufus starts with formatting the stick, which takes a long time, and then transfers Xubuntu.

Not having a persistent partition is acceptable to me. I'll *install *Xubuntu on another USB stick and use it to boot Xubuntu. I will be able to configure Xubuntu, and everything will be faster.

Incidentally, Xubuntu occupies less than 4GB on the 32GB stick, so having a pretty big persistent partition should be fine. But it doesn't work when created with Rufus.

---

### Post by him610 on 2024-06-25
mkusb is my goto for installing distros to usb devices, including with persistence.
You can find how to download, install, and use it here, [https://ubuntuforums.org/showthread.php?t=1958073]("https://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by lapetesson on 2024-06-28
@him610: Thank you. Perhaps I'll try it next time. I'm already past this issue. I have Xubuntu installed on a USB. Xubuntu Live is not used any more.

---

