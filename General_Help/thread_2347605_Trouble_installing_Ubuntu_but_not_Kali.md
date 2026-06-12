---
title: "Trouble installing Ubuntu but not Kali??"
date: 2016-12-27
forum: General Help
---

### Post by sgtkeebler on 2016-12-27
Hey guys, so I have my 32GB USB 3.0 that everytime I try using RUFUS to burn Ubuntu or Kubuntu to it gives me an "error parsing pcc subspaces". Its super weird because if I burn the Kali iso to that same flash drive it works no problem! So I grabbed a different flash drive and burned Kubuntu to it and I still got the same error "error parsing pcc subspaces", but this time it worked and I was able to install Kubuntu! I really like Kubuntu and I think I am going to keep it because I am really starting to like yakkety yak, but I really want ubuntu on my computer but for the life of me can not get it to work because of that stupid error! I have a lenovo yoga 2 11, I replaced the manufacture hard drive and put in a SSD so I can have a clean brand new linux install. Can someone please help me make sense of why I cant get ubuntu without the error "error parsing pcc subspaces"?  I really like Kubuntu compared to the older versions because all my drivers work. I have blue-tooth, wifi, and sound. On Kali I have to use a wifi dongle, bluetooth doesnt work and the sound is horrible.

---

### Post by ajgreeny on 2016-12-27
Does this help?
[https://ubuntuforums.org/showthread.php?t=2326630](https://ubuntuforums.org/showthread.php?t=2326630)
or this?
[http://askubuntu.com/questions/670509/error-parsing-pcc-subspaces-from-pcct-acpi-pcc-probe-failed](http://askubuntu.com/questions/670509/error-parsing-pcc-subspaces-from-pcct-acpi-pcc-probe-failed)

---

### Post by sgtkeebler on 2016-12-28
Yes it kind of does, So I think Kubuntu I installed using the old legacy way on my laptop, and Kubuntu automatically installed to UEFI. But Ubuntu every time I try to install it from USB drive number one I get that error. I have been thinking about it for a couple of days and do you think USB drive number 1 is corrupt? but if it was corrupt why would I be able to boot into kali Linux and install that no problem? These are a few questions I have. I love Kubuntu so I think I am just going to stay, but I would love having the option knowing I can just switch if the mood strikes.

How do you format a corrupted USB Drive using DD utility?

---

### Post by ajgreeny on 2016-12-29
You don't format a disk using dd, but you can clear it completely if that's what you want to do.

However, I suggest you get hold of [mkusb]("https://help.ubuntu.com/community/mkusb") which uses dd under the skin, but gives you a simple GUI, with warnings to reduce the possibility of dd living up to its nickname of **d**isk **d**estroyer.

You can also use mkusb to create a new install USB if necessary.

---

### Post by sgtkeebler on 2016-12-30
Hey so I got rid of Kubuntu everything just kept crashing all the time. I installed Ubuntu instead, much better. Is there anyway to install Ubuntu in UEFI mode without the parsing pcc subspaces error? I installed Ubuntu successfully but I can only boot if my laptop is set to legacy mode. If I try to boot using UEFI, I get no boot disk error.

---

### Post by yancek on 2016-12-30
You need to boot the Ubuntu install DVD/flash drive UEFI in order to install UEFI.  If you have other systems not UEFI, then you will have problems booting if you install it UEFI.  How to boot or know you are booting UEFI with Ubuntu is explained at the site below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sgtkeebler on 2016-12-30
That helps, good document. Its weird though Kubuntu installed in UEFI automatically it switched over when I went to install. I used RUFUS to help burn my Ubuntu ISO, I downloaded the 64-bit version, but it wont install in UEFI. According to the article though since this is my main OS it doesn't really matter if its installed in Legacy or UEFI, but I would prefer UEFI. Guess I will re-download and try burning it again and see what happens. Which tool do you recommended for burning?

---

### Post by sgtkeebler on 2016-12-30
Thanks friends this helped out a lot. I was able to install in UEFI mode with the help of that article. It did give me a weird message like " you can continue in UEFI mode, but may have trouble with other operating system" something similar to that. Since I have a 120GB ssd and ubuntu is my only OS. I can just format and reinstall if I wanted a new operating system right?

---

### Post by yancek on 2016-12-31
If you are installing Ubuntu, you can install either UEFI or the older MBR if it is the only system.  It's a personal choice as long as your hardware has UEFI capability.  As you read in the article, the problems come in when you have multiple systems.  They all need to be either UEFI or MBR as mixing the two will result in one or more not booting properly.

---

