---
title: "cannot find &quot;device manager&quot; nor &quot;hardware information&quot;"
date: 2008-06-28
forum: General Help
---

### Post by wallarro on 2008-06-28
I am a linux beginner and just installed Ubuntu 8.04 through wubi, but the wireless internet does not working,

I found some info on how to install wireless driver with ndiswrapper, but all of them require me to find the hardware info through Administration->Device Manager OR Preferences-> Hardware Information

I could NOT FIND either of  them!

Anybody can help? Thanks!

---

### Post by Kevbert on 2008-06-28
Go to Applications - Accessories - Terminal.
At the prompt enter
```
iwconfig
```
This will give you any available wireless information.
To exit just click on the X in the top righthand corner of the terminal window.

---

