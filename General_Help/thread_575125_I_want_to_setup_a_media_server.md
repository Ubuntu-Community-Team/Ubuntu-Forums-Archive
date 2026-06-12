---
title: "I want to setup a media server"
date: 2007-10-13
forum: General Help
---

### Post by Swarms on 2007-10-13
Hello.

I am am about to rebuild my old work station into a media server for my whole family, so they can store all their music, films, texts whatever for streaming purpose.
It also got another purpose, that I connect both our laser A4 and our Inkjet A3 printer to it, so we can print through it with both our Windows and Ubuntu boxes.

Is this possible, I guess there will be interaction issues but can they be solved?
And yes I would highly prefer to install Ubuntu as the operating system. ;)

---

### Post by milosz.galazka on 2007-10-13
Give it a try :) If that printers works under linux than there shouldn't be any unsolvable problems...

---

### Post by skompier on 2007-10-13
May be look at Freevo. [http://freevo.sourceforge.net/](http://freevo.sourceforge.net/). It's in Feisty [http://doc.freevo.org/FreevoAptUbuntu](http://doc.freevo.org/FreevoAptUbuntu)

---

### Post by Swarms on 2007-10-14
Are there any other ways? Freevo looks like a HTPC program to me.
Its an expensive Lexmark Laser and a Canon Pixma printer. And are there any easy way for the Windows computers to access it?

---

### Post by milosz.galazka on 2007-10-14
[Sharing Printers With Windows PCs]("http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html")
[Push Windows Printer Drivers with CUPS]("http://www.enterprisenetworkingplanet.com/netsysm/article.php/3621876")
[How to make Windows use CUPS IPP]("http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html")

---

### Post by Swarms on 2007-10-14
Thanks a lot Milosz! Anyone got any input on a easy way to share files?

---

### Post by milosz.galazka on 2007-10-14
[How to share files using Samba ]("http://ubuntuforums.org/showthread.php?t=26438")

---

### Post by strabes on 2007-10-14
In my opinion, the easiest way to add a printer across a network is to just use its http address:```
http://ip.of.host.computer:631/printers/nameofprinter
```

To find the ip of the host computer, run "ifconfig" and find the line that looks like this:>  inet addr: xxx.xx.xx.xxx

---

