---
title: "LIbreoffie is not responding properly"
date: 2018-03-18
forum: General Help
---

### Post by ajbozdar on 2018-03-18
Hello there,

I ran LibreOffice 5 for the very first time and it didn't turn right. I ran it into both standard Wayland and X sessions, but none of the editing icons appears as they should. I can type and save the files, though. Could you please tell me what I am missing? Please refer the attached screenshot for better understanding.

Thanks.



[ATTACH=CONFIG]278983[/ATTACH]

---

### Post by ank2 on 2018-03-18
I think I had this years ago. I think I had to install some GTK or QT libraries.

Anyway, go to the settings menu and see if you can change the theme. For other themes you might have the libraries necessary already installed.

---

### Post by #&amp;thj^% on 2018-03-18
> **ajbozdar said:**
> Hello there,

I ran LibreOffice 5 for the very first time and it didn't turn right. I ran it into both standard Wayland and X sessions, but none of the editing icons appears as they should. I can type and save the files, though. Could you please tell me what I am missing? Please refer the attached screenshot for better understanding.

Thanks.



[ATTACH=CONFIG]278983[/ATTACH]

I have found over the the past month or so that apparmor is preventing some rules for the current libreoffice in our repos.
But adding this PPA has the new rules included: "ppa:libreoffice/ppa"
I have always found that before Installing a newer version of Libreoffice is was best to first un-install libreoffice

Have a look here post #13: [https://ubuntuforums.org/showthread.php?t=2385614&page=2](https://ubuntuforums.org/showthread.php?t=2385614&page=2)

---

### Post by ajbozdar on 2018-03-20
Hi there,

I simply purged the standard .deb package and installed the **snap**. It works great now, and I believe snaps are going to be new packages using all dependencies within.

Thank you very much for your time. Have a great day!

-AJ

---

