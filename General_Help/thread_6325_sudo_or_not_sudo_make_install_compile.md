---
title: "sudo or not sudo make install compile"
date: 2004-11-27
forum: General Help
---

### Post by taygan on 2004-11-27
I've recompiled a kernel or two on debian, always from the root account.  I tried to compile the newest WINE from my ubuntu user account using sudo, and had a horrible failure as the install script used su.  I used "sudo .tools/wineinstall"  I have not tried "./configure && make && make install" I'm assuming I would have to "sudo ./configure && make && make install"

1. Should I use the root terminal for make commands?
2. Should I use sudo for make commands?
3. When is it best not to use sudo for make install?

Thanks!

---

