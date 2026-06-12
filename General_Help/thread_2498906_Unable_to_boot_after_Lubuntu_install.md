---
title: "Unable to boot after Lubuntu install"
date: 2024-07-03
forum: General Help
---

### Post by toxyrock20 on 2024-07-03
Hi, last night I installed Ubuntu on my PC but as soon as I restarted these messages appeared:
Could not create MokListRT: Volume Full
Could not create MokListXRT: Volume Full
Could not create SbatLevelRT: Volume Full
Could not create MokList Trusted RT: Volume Full
Something has gone seriously wrong: import_mok_state() failed: Volume Full
After these messages the PC just shuts down.
From what I understand the EFI partition is full (I think it's the fault of Windows 10 that I had on my PC), and even if I try to boot with the USB with Ubuntu inside it gives me the same errors.
However, I managed to boot with a USB stick with Slakware, but the only terminal I can access from is the grub one...
I also tried activating and deactivating secure boot and also fast boot but nothing.
Any ideas on what to do with the grub terminal (efibootmgr doesn't work, I've already tried, it tells me it's not recognized)?

---

### Post by yancek on 2024-07-03
Disabling Secure Boot and removing EFI boot entries should help.  Discussed at the link below, read all the way through the posts.

[https://askubuntu.com/questions/1401737/couldnt-create-moklist-volume-full-grub-doesnt-start-at-all](https://askubuntu.com/questions/1401737/couldnt-create-moklist-volume-full-grub-doesnt-start-at-all)

I don't know what you mean by the 'grub terminal' in Slackware.  Do you have a Slackware Live OS on your USB or just the standard Slackware which is just the installer?  If you have the live version, you should be able to boot ir and use efibootmgr.  

Which release of Ubuntu did you install?  Is windows 10 the only other OS on the machine?  Had you installed other Linux systems previously?

---

### Post by toxyrock20 on 2024-07-03
Hi, so:
1. In the end I solved it thanks to your advice, and also removing the boot options with efibootmgr, from the Lubuntu live distro.2. For the grub terminal it was only because I had first tried to solve with Slackware, but when I wrote the forum I wasn't able to start it, even if then after about 1 hour I managed to start Slackware but I couldn't do anything because: lack of experience with distros outside of Debian and Arch (and also with linux in general), so I didn't know how the slackpkg package manager... worked, and it didn't connect to the internet.
But then thanks to your advice I managed to start Lubuntu and I solved...
Thanks for the idea.
3.It's Lubuntu 24.04, before there was Windows 10 inside, and I think this was the problem..., and then this is the first Linux distro in general that I put on this PC, since it's not my main PC, it's just a super low-end Asus pc from 2018. (It has a dual core celeron, 1ghz...)

---

