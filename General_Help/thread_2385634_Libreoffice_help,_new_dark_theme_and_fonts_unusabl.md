---
title: "Libreoffice help, new dark theme and fonts unusable"
date: 2018-02-22
forum: General Help
---

### Post by aeronutt on 2018-02-22
Using version 5.4.5.1, very recently upgraded I assume. But suddenly the fonts, menus, and dark theme are completely unusable.   I can't even close windows, read many pull downs, get to help menu's, etc.
 Any way to fix this?
See how difficult it is to use the menu's below, just one example
. Extremely frustrating.  FYI, I haven't changed any of my system themes/fonts/settings in months, and this LibreOffice issue seems to have happened within the last day or so.

[https://i.imgur.com/mLyWrG5.png](https://i.imgur.com/mLyWrG5.png)

[https://i.imgur.com/egGq9lL.png](https://i.imgur.com/egGq9lL.png)

[https://i.imgur.com/r8NHZRN.png](https://i.imgur.com/r8NHZRN.png)

[https://i.imgur.com/P4UEkPm.png](https://i.imgur.com/P4UEkPm.png)

---

### Post by #&amp;thj^% on 2018-02-22
See if this helps: [https://ask.libreoffice.org/en/question/135900/libreoffice-5412-toolbar-icons-all-missing/](https://ask.libreoffice.org/en/question/135900/libreoffice-5412-toolbar-icons-all-missing/)
Same reply here as above link.
[https://ask.libreoffice.org/en/question/118218/solved-menu-bar-icons-missing/](https://ask.libreoffice.org/en/question/118218/solved-menu-bar-icons-missing/)

---

### Post by vasa1 on 2018-02-22
What happens if you close all LibreOffice applications and then rename ~/.config/libreoffice to something else and restart LibreOffice?

Did you have some sort of dark theme in use before?

Do you have libreoffice-gtk3 installed?

---

### Post by aeronutt on 2018-02-22
> **1fallen said:**
> See if this helps: [https://ask.libreoffice.org/en/question/135900/libreoffice-5412-toolbar-icons-all-missing/](https://ask.libreoffice.org/en/question/135900/libreoffice-5412-toolbar-icons-all-missing/)
Same reply here as above link.
[https://ask.libreoffice.org/en/question/118218/solved-menu-bar-icons-missing/](https://ask.libreoffice.org/en/question/118218/solved-menu-bar-icons-missing/)

Nope, didn't really help. 

It's a mess. Menu's won't dissapear (they end up 'stacking' over each other, making them unreadable.)  Menu text is white, even over the white 'paper'. Ug.

---

### Post by aeronutt on 2018-02-22
> **vasa1 said:**
> What happens if you close all LibreOffice applications and then rename ~/.config/libreoffice to something else and restart LibreOffice?

Did you have some sort of dark theme in use before?

Do you have libreoffice-gtk3 installed?

1) Didn't change anything.
2) Nope.
3) How do I check?

UPDATE #3, YES,  libreoffice-gtk3  is installed.

---

### Post by wildmanne39 on 2018-02-22
Please use the attachment feature or url's for images because a lot of people have slow connections and bandwith limits.

---

### Post by aeronutt on 2018-02-22
> **wildmanne39 said:**
> Please use the attachment feature or url's for images because a lot of people have slow connections and bandwith limits.

Ohh..ok..I see what you're saying. thanks.

---

### Post by wildmanne39 on 2018-02-22
Your welcome, I would have replied sooner but I am reinstalling Ubuntu on my desktop computer.

---

### Post by aeronutt on 2018-02-22
I downloaded and installed 6.01 (debs). Not my preferred solution, but it works.

---

### Post by aeronutt on 2018-02-23
Update. Deleted .deb install, and added libreoffice ppa. Now using 6.0.x with no issues. Never figured out what was so wrong with 5.4.5.
Thread marked solved.

---

### Post by vasa1 on 2018-02-23
Which ppa did you add?
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)
or
[https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-6-0](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-6-0)

---

### Post by aeronutt on 2018-02-23
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

Which is:
ppa:libreoffice/ppa

Which is currently v6.0.1.1

---

