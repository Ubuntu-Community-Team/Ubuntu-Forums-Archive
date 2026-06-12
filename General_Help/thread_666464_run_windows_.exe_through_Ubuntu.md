---
title: "run windows .exe through Ubuntu"
date: 2008-01-13
forum: General Help
---

### Post by dzuari on 2008-01-13
is there any way? by program or emulator?

---

### Post by ~LoKe on 2008-01-13
You can do it with WINE.

```
sudo apt-get install wine
```
Then you can run the app with wine.

```
wine appname.exe
```
Or, right click -> open with WINE.

---

### Post by dzuari on 2008-01-13
thx

---

### Post by erpo on 2008-01-13
Go to appdb.winehq.org to see if your program works with wine, or to find necessary tips on running your program.

---

### Post by sub2007 on 2008-01-13
Yup you should definitely check at WineHQ because it must be noted that not every program will work flawlessly under Wine. Ubuntu isn't Windows and it has a completely different packaging system and file system to Windows. If you can get a  Windows program working under Wine then it's a bonus, not an expectation. We're lucky really that we have a program that can run some Windows programs but you really can't expect it to handle every Windows program you hurl at it flawlessly.

If you want 100% compatability then the only workaround is to install Windows via a virtual machine (like Virtualbox) but you should be aware that you are effectively running two operating systems on shared resources and that you will only get an 8MB shared graphics card.

The final option is to dual boot into Windows to run the programs that you absolutely have to run under Windows (like games).

---

### Post by twright on 2008-01-13
also try winedoors, it automates many installations in wine ([apt:wine-doors](apt:wine-doors))

---

