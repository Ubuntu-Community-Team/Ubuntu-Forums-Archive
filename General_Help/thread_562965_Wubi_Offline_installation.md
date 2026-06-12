---
title: "Wubi Offline installation"
date: 2007-09-29
forum: General Help
---

### Post by aashay on 2007-09-29
I hope i make sense here because its not me who is facing the problem, but a friend of mine.
According to him, the installer wants to download the Ubuntu iso from the net before installing. He has a really slow connection (3kBps believe it or not) so this is not really an option. I have given him the Feisty iso which he has on his disk. So is there any way to perform an offline install with the pre-existing iso?

---

### Post by divague on 2007-09-29
[https://wiki.ubuntu.com/WubiGuide#head-4318fa9eb3579a59ea165e974bd52773b9b9ef76](https://wiki.ubuntu.com/WubiGuide#head-4318fa9eb3579a59ea165e974bd52773b9b9ef76)

---

### Post by aashay on 2007-09-29
Thanks..

---

### Post by saj4eva on 2010-03-13
> **divague said:**
> [https://wiki.ubuntu.com/WubiGuide#head-4318fa9eb3579a59ea165e974bd52773b9b9ef76](https://wiki.ubuntu.com/WubiGuide#head-4318fa9eb3579a59ea165e974bd52773b9b9ef76)

Doesn't work. That page says: *"download both Wubi and the required ISO [...] Then copy both files within the same folder on the machine with no internet access. Then run the Wubi executable."*

When I try that, Wubi STILL tries to download some log file but can't (since I'm offline) and ignores the Ubuntu ISO in the same folder next to it.

I'm using Wubi v9.10 and ubuntu-9.10-desktop-i386.iso of size 689 MB (723,488,768 bytes).

Using the "--skipmd5check" switch didn't help.

Here's the actual error message shown:

```
---------------------------
Ubuntu Installer
---------------------------
An error occurred:

Cannot download the metalink and therefore the ISO

For more information, please see the log file: d:\docume~1\temp\wubi-9.10ubuntu1-rev160.log
---------------------------
OK
---------------------------

```So, what next?

---

### Post by saj4eva on 2010-03-23
Nobody can help a Windows user trying to use Linux? ;)

---

### Post by 3rdalbum on 2010-03-23
Wubi is already inside the ubuntu-9.10-desktop-i386.iso file. Just burn it to CD and insert it while Windows is running, then follow the prompts.

Better yet, insert the CD while the computer is not running, and set your BIOS to boot from CD. Then install Ubuntu the regular way. Wubi has some pretty severe limitations so I always recommend doing a real, regular dual-boot.

---

### Post by saj4eva on 2010-03-27
> **3rdalbum said:**
> Wubi is already inside the ubuntu-9.10-desktop-i386.iso file. Just burn it to CD and insert it while Windows is running, then follow the prompts.
THANK YOU! :D This was the only way to get Ubuntu to install, without it trying to download another whole 700 MB distro.

---

