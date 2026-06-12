---
title: "lubuntu-14.04.5-desktop-i386 - Run Preview from disc crashes"
date: 2016-09-22
forum: General Help
---

### Post by srd75 on 2016-09-22
Hi, I've downloaded and burnt lubuntu-14.04.5-desktop-i386 to DVD, used it to boot my NEC L1100.

At the setup screen, it asks if I want to try before installing, and I select Yes.

I get to a black screen with a list of errors, the last of which is:

(initramfs) Unable to find a medium containing a live file system /bin/plymouth: error while loading shared libraries: /lib/i386-linux-gnu/librt.so.1: invalid ELF header.

The NEC L1100 has 2GB of RAM.

Help appreciated.

---

### Post by sudodus on 2016-09-22
Welcome to the Ubuntu Forums :-)

At least it boots (to the menu, where you can select 'Try Lubuntu before installing').

I suspect that it can be one of a few problems:

***1. Bad download or bad burn.***

Please check with ***md5sum*** that the downloaded iso file is correct. See this link: [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

and and the boot menu,  select ***'Check the disk for defects'***. If problems, please try to burn the DVD at the lowest possible speed.

[B][I]2. Problems with a driver for the graphics or wifi.
[/I][/B]
Please specify your computer

- Brand name and model (NEC L1100, you already told us, but it is difficult to find a specification via the internet, please give more details)
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It makes it easier for us to help.

- You may need some boot options, for example nomodeset. See this link: [Boot options](https://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

- There might be problems if you have an Intel graphics chip, and you might be better off with a another version of Lubuntu, either ***14.04.1 LTS*** with the Trusty kernel series (3.13) or ***16.4.1 LTS*** with an updated driver package for Intel.

---

### Post by Impavidus on 2016-09-22
Have you tried to check the disk for defects? If it passes that test, you may have to test the memory. 2GB should be enough.

Keep in mind Lubuntu 14.04 only has 7 months of support left.

---

