---
title: "iBus not working on non-KDE environment"
date: 2013-05-06
forum: General Help
---

### Post by etienoo on 2013-05-06
Hi,

I recently upgraded my Kubuntu 12.10 to 13.04 using the standard upgrade system.

Since  then, iBus (that I use to write in Chinese) only working in some windows; I have the impression that it corresponds to the KDE software (e.g., Kate but not Firefox, not Skype, etc.).
Technically, I cannot launch and stop the Chinese input when I'm not in a KDE software; furthermore, even if I launch the Chinese input in a KDE software, it will not input Chinese in non-KDE software (such as Firefox).
This did not happen before the upgrade to 13.04.

Do you have any suggestion?

**Configuration**:
Kubuntu 13.04 64 bits
[COLOR=#000000][FONT=Verdana]MacBook Pro 6.2[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]2.66GHz Intel Core I7[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]4GB 1066MHz DDR3 SDRM - 2x2GB[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]500GB Serial ATA Drive @ 7200[/FONT][/COLOR]

Thank you

---

### Post by albertyang on 2013-05-08
I had the same problem.
Doing the following seems to fix it:

$ sudo im-config
and change the input method from default to iBus.
Then log out and login.

---

### Post by etienoo on 2013-05-11
Yes, it works! Thank you.
(I was required to install the zenity package, btw.)

A side effect is that now I can't write the "^" letters (âêîôû) in KDE software (these letters are often used in French), but it's still OK.

Thanks!

---

