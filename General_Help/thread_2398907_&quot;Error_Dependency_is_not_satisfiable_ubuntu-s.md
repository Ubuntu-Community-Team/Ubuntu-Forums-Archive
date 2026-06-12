---
title: "&quot;Error: Dependency is not satisfiable: ubuntu-sso-client (&gt;=0.99.6)&quot;"
date: 2018-08-19
forum: General Help
---

### Post by chartreuseraven on 2018-08-19
Hello, I recently upgraded to Lubuntu 18.04 from 16.04 on my Dell Inspiron-14-3452.

Upon upgrading, I found the Lubuntu Software Center wasn't working at all (it launched but couldn't install anything I put in the 'Apps Basket'). I searched around when I encountered this problem, and apparently GNOME Software is supposed to replace the Lubuntu Software Center in 18.04, but alas GNOME Software was not installed on my computer. I thought it was just a mix-up during the upgrade, so I uninstalled Lubuntu Software Center and installed GNOME Software through the terminal instead. However, GNOME software couldn't install anything either (the install button just didn't work). Then, I uninstalled that, too, and just straight up downloaded a .deb file for Ubuntu Software Center ver. 5.2 (nothing would come up when I tried to install it through the terminal, so I got it online).

When I opened the Ubuntu Software Center installer through gdebi, I was met with the error in this post's title: "**Error: Dependency is not satisfiable: ubuntu-sso-client (>=0.99.6)**" and could not install it. I tried googling around, but nothing came up for this dependency.

I've only been using Lubuntu for less than a year; I'm still kind of a noob to Ubuntu/Linux, so maybe there's something I'm not seeing?

Any kind of help/advice is appreciated. Thanks in advance!

---

### Post by mc4man on 2018-08-19
Open up whatever lubuntu uses for a terminal & go 
```
sudo apt install gnome-software
```

[https://packages.ubuntu.com/source/bionic-updates/gnome-software](https://packages.ubuntu.com/source/bionic-updates/gnome-software)

---

