---
title: "WINDOWS INSTALLATION with Vmware server CRASHES!"
date: 2007-02-07
forum: General Help
---

### Post by gadget00 on 2007-02-07
Hi all. Im having problems installing windows with the vmware server.

VMWare installed fine, runs fine, creates the virtual machine in a fine way; even boots the windowsCD fine!
[U][B][I][COLOR="DarkRed"][SIZE="5"]
But when I choose to do the drive format(NTFS, both regular or quick), it goes to the 0% screen, keeps there for a while, and then the virtual machine gets off by itself![/SIZE][/COLOR][/I][/B][/U]

**[COLOR="Black"]If I retry the installation, then tells me "operating system error" and never boots.[/COLOR]**

Also, all the programs running start having internal errors and crash. I knew it because each time i launch any app, the bug-report program launched, and then crashed too!

I dont understand why this is happening. I even switched the directory that keeps the virtual machine files, just in case it had any permission issues, but keeps on failing. It was supposed to be fine. I saw a guide here in the forums, and they didnt had problems. Im really out of ideas now. Hope for an answer ASAP.


***Also, I tried to use the recoveryCD that came with the laptop(Toshiba Satellite L10-S104) and that also gave an "Internal Memory Error" and didnt worked either. THe difference is that doing this didnt made the apps crash.*

---

### Post by robcarr2 on 2007-02-15
Try this tutorial:

[http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html](http://maconstuff.blogspot.com/2006/06/how-to-run-windows-xp-under-ubuntu.html)

It isnt using vmware, but another piece of virtual machine software.

Or if you follow that and windows is running to slow for you try out this tutorial:

[http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation](http://www.hants.lug.org.uk/cgi-bin/wiki.pl?LinuxHints/QemuCompilation)

It is a bit more advanced, but it compiles the program with a plugin which speeds things up a hell of a lot.

Hope this helps :)

---

### Post by Robin T Cox on 2007-02-16
See:

HOWTO: Install Windows XP/2000 in VMWare Player
[http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275)

---

