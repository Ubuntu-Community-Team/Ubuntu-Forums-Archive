---
title: "Booting From Linux USB in Win10Pro"
date: 2021-10-18
forum: General Help
---

### Post by chunkydrew2 on 2021-10-18
Can someone help me? I have always been able to run Ubuntu Live (and other Linux distros) by inserting a USB drive with Ubuntu, editng my BIOS boot order to boot first from USB. Voila - it would work. Now, I'm no longer able to do so. When I try, I get errors saying that I must disable BitLocker to continue. When I do so, it still doesn't work, and gives me the same error message.
Has anyone else encountered this situaion? Is this something new to Win10? I'm running Windows 10 Pro on my Dell XPS 7590. Should I permanently BitLocker? I'm at wits' end, because I really enjoy trying out distros, to see if I want to add them as a dual or tri-boot option (I have lots of SSB space). Right now, I'm only using Ubuntu through WSL to login to my Ubuntu file server. I really want to dual-boot ''real" Ubuntu.

Help!

---

### Post by ajgreeny on 2021-10-18
Is this behaviour and inability to boot a Ubuntu USB a new problem since you got this Dell Computer, or have you had an update of Windows 10 that has caused the problem?

If you managed this previously on another computer, was the older one using UEFI or BIOS?

How did you create the USB, and was it done so as to produce a UEFI enabled USB?  As the computer is running Windows, it will, I assume be using UEFI, so the USB will have to be created in a manner that allows it to boot on a UEFI computer.

I know nothing about BitLocker so will have to leave that to others to comment.

---

### Post by dragonfly41 on 2021-10-18
I am on Dell 3268. Original internal drive has Windows 10, WSL(1) and old ext4 partition for old version of Ubuntu.
Most of my activity is on external USB SSD's (two, Ubuntu 20.04 and backup) plus some other USB containers just containing archives.
But earlier today I did dual boot into Windows 10 and was reminded that I need to upgrade before 31st October.
I only go into Windows when I need to.

Now personally I do not use BitLocker but I found these articles which might help you.

BitLocker
[https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview](https://docs.microsoft.com/en-us/windows/security/information-protection/bitlocker/bitlocker-overview)

[https://itsfoss.com/dual-boot-ubuntu-windows-bitlocker/](https://itsfoss.com/dual-boot-ubuntu-windows-bitlocker/)

---

### Post by chunkydrew2 on 2021-10-22
I'm pretty sure I've run Live USBs on this laptop before, without issue. I just downloaded the ISOs, then used Rufus to create bootable USBs. I think it has something to do with BitLocker, but I had no idea it was even running. Must have  come in a Win update. That seems to be the main culprit in preventing me from booting from USVB

---

### Post by chunkydrew2 on 2021-10-22
Thanks for your responses, especially dragonfly41. Your 2nd link seems to be a detailed tutorial on how to solve my issue. I'll definitely try it out later today. I also had Win10 Pro on my previous laptop, but I guess the BitLocker is really new.
Once again, thanks for your help!

---

