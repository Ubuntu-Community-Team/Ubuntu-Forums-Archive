---
title: "how can I run wubi with less than 256mb of RAM"
date: 2008-05-28
forum: General Help
---

### Post by Yondergod22 on 2008-05-28
I found this on [https://wiki.ubuntu.com/WubiGuide#head-3b62d195ae4508cbc9cda21f715c530637901377](https://wiki.ubuntu.com/WubiGuide#head-3b62d195ae4508cbc9cda21f715c530637901377), but I don't understand what it means, how do i start it w/ an "argument" and also i do have 256mb of RAM, why does it say I don't have enough? is it b/c other programs and stuff are using too much of it?
and this is the thing I found...
"Can I force Wubi to install even if I have <= 256MB of memory?

Yes start Wubi with the argument "--skipmemorycheck". The installer may not work in such conditions." 

Thank You

---

### Post by ago on 2008-05-29
start > run

\path\to\wubi.exe --skipmemorycheck

---

### Post by chronographer on 2008-05-29
Oh and when you install, chose xubuntu, which is a light weight graphics version of Ubuntu. If you can't choose this, download the xubuntu CD. Good luck!

---

### Post by scottlenger on 2008-06-03
Cool. I had a laptop with 8mb of ram allocated to onboard video leaving me with 248mb. --skipmemorycheck made it work.

---

