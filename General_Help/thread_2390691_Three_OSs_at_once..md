---
title: "Three OSs at once."
date: 2018-05-01
forum: General Help
---

### Post by Autodave on 2018-05-01
I had Win10 and Xubuntu 16.04 running on the same PC. Xubuntu was on a separate SSD with Win10 on a spinner. I removed the SSD with 16.04 on it and installed a new SSD and installed 18.04 on that. How can I put all 3 HDs in the machine and get GRUB to recognize all of them. (I don't need advice on putting them all in the machine: just how to get GRUB running. :-))

---

### Post by oldfred on 2018-05-01
UEFI or BIOS?
All systems need to be in same boot mode.

It may be as simple as this if same boot mode,otherwise not possible from grub, just UEFI boot menu:
sudo update-grub

If that does not work:
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by HermanAB on 2018-05-01
Hmm, multi-boot is so 20th century.  Why don't you use Virtualbox and run them all at the same time?

---

### Post by dragonfly41 on 2018-05-01
I have Win 10 and Ubuntu 16.04 in the main drive of a Dell 3268 tower and I have old Ubuntu 14.04 (bootable) and another on two external drives via USB (just to transfer old files into the main drive).
The magic which brings them into one startup menu is boot-repair.

---

### Post by monkeybrain20122 on 2018-05-01
The question is why do you want that? Duaboot with Win 10 is hard to maintain and set up. But If you can  dualboot you can multiple boot with 2 linux since one will control boot and the other is not the problem, Windows is the problem. But why do you want two ubuntu's???

---

### Post by QIII on 2018-05-01
> **monkeybrain20122 said:**
> But why do you want two ubuntu's???

That is the user's wish.  While we do at times ask why a user wants to do something, it is appropriate only when asking the question is necessary to determine the user's needs for diagnostic detail and formulating a suggested course of action.  Beyond that, it is really none of our business.

@Autodave:

One important technical detail here is that as of late, Win10 updates often lead to the destruction of a well-planned GRUB configuration because Windows behaves as if it were the only OS in the world.  Something to bear in mind and be prepared for -- but not catastrophic.

---

### Post by Autodave on 2018-05-01
Win10 and 16.04 are both legacy. I am assuming that 18.04 was also legacy, but not sure. I really haven't done anything on 18.04 that can't easily be redone.

I have not been able to get WINE running properly on 18.04 and there is one program that I really need/want. However, on 18.04, one of the games I like has been significantly updated and is much better than on 16.04.

---

### Post by yancek on 2018-05-01
> I am assuming that 18.04 was also legacy, but not sure

No need to assume, just run the command below from a terminal on 18.04 and it will tell.

> [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"   

If it shows Legacy boot, then it's legacy and you can run the same command on 16.04.  If you were using UEFI, you would have an EFI partition which you can see using gparted or the command:  sudo parted -l

If there is no EFI and they are all legacy, all you should need to do is update-grub suggested above.

---

### Post by Autodave on 2018-05-02
> **monkeybrain20122 said:**
> The question is why do you want that? Duaboot with Win 10 is hard to maintain and set up. But If you can  dualboot you can multiple boot with 2 linux since one will control boot and the other is not the problem, Windows is the problem. But why do you want two ubuntu's???

I thought that I had answered that yesterday, but I do not see the post: not sure what happened to it.  The reason is this: 18.04 has/does some things way better than 16.04 does. I never got 16.04 and Audacity to play nice when recording 18 channels at one time, but it works fine on 18.04. However, after MANY hours of playing with Wine, I still could not get it to play an old game that I have. But, the game runs fine on 16.04.

Anyway, 3rd HD installed and working fine.  Thanks for the help folks!

---

