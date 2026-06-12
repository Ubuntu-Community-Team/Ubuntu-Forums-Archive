---
title: "Can not reinstall gdm and ubuntu-desktop"
date: 2008-04-26
forum: General Help
---

### Post by dmooreng on 2008-04-26
I am new to Ubuntu, and was successful in loading UBuntu 7.10 onto an old PIII.  The only problem was getting my sound card to work.  Being a good old Soundblaster 16, I figured there would be no sweat. So far I've been wrong.

Using "SoundTroubleshooting" document from the Ubuntu site, I had no success with "modprobe", so I went to the next step and decided to reinstall the linux-sound-base, etc.  I used terminal and typed away:
"sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils"
The document warned that this might remove gdm and ubuntu-desktop as well.  Sure enough it did, but the document indicated no problem, just use:"sudo apt-get install gdm ubuntu-desktop"
No luck!   

I took a look at  "/etc/apt/sources.list" and only the CD source was not marked as a comment.  I used "sudo nano" to change the "source.list" to list all "deb" lines and put my Ubuntu disk into the drive.  I then used "apt-get install" again for "gdm" and "ubuntu-desktop".  No luck.  

The computer does not seem to be trying to access the CD drive and I get the following message:"package gdm is not available, but is referred to by another packge. This may mean that the package is missing, has been obsoleted, or is only available from another source.E: Package gdm has no installation candidate."Same thing when I tryed to reinstall ubutu-desktop on its own.

HELP!  Suggestions please.

---

### Post by bodhi.zazen on 2008-04-26
Just a guess, but try first re-enabling your sources then:

```
sudo apt-get update
```The re-install gdm / ubuntu-desktop

If you want to install from CD I believe you now need to use the so called "alternate" cd an not the desktop CD.

---

### Post by dmooreng on 2008-04-26
I tried to get update and it appears that I get "Failed to fetch ..." and "Could not resolve ..." for each source.  I also put an Ubuntu 7,10 Alternate disk in CD drive, without success.  Also got message, "E: Some index files failed to download ..."

I am using a wireless connection and it was working fine before I tried to resolve the sound card issue.

Any more thoughts?

---

### Post by dmooreng on 2008-04-26
I tried to get update and it appears that I get "Failed to fetch ..." and "Could not resolve ..." for each source.  I also put an Ubuntu 7,10 Alternate disk in CD drive, without success.  Also got message, "E: Some index files failed to download ..."

I am using a wireless connection and it was working fine before I tried to resolve the sound card issue.

Any more thoughts?

---

### Post by bodhi.zazen on 2008-04-27
My guess is either you do not have a working internet connection or your there is a problem with your sources. I am seeing ubuntu-desktop in the 7.10 repos here.

can you post your /etc/apt/sources ?

---

### Post by dmooreng on 2008-04-27
I will see what I can do later tomorrow.  

I also tried to repair the system with the Alternate disk, but for some reason it couldn't mount the CD drive even though the drive was reading the CD fine?  I am going to download another image and burn another copy and try that again too.

Thanks for all the help! I'll be in touch.

---

### Post by dmooreng on 2008-05-03
Thanks for your help, but I finally had to reload and basically start from scratch.  Everything is running, except I still can't get the sound card to wor.  This surprises me since it is a standard Soundblaster 16.  Any thoughts on this?

---

### Post by dmooreng on 2008-10-19
Problem solved.  Dug out another sound card in my "used parts" bin, installed it and it works fine.

---

