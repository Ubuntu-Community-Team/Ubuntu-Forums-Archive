---
title: "Packages installation methods"
date: 2007-02-01
forum: General Help
---

### Post by thorosius on 2007-02-01
Hy!
               I am using Ubuntu 6.1. Sometimes I need to install different packages but the problem is I still cann't get my Intel Modem to work so I am unable to download packages from within Ubuntu. Although I have downloaded packages in Windows, but this is a tiresome process as I cannot determine which dependencies already exist in my Ubuntu installation and which do not. Is there anyother way or an easier way? Like an extra ISO for packages?

---

### Post by pseudonym on 2007-02-01
Hi, there is the DVD download (see the bottom of the [Ubuntu download page]("http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download")). But of course what you really want to do is get your modem working. What exactly is going wrong with it?

---

### Post by thorosius on 2007-02-01
There are a number of things first I can't confirm my modem chipset. On the actual card there is "Ambient" written, on the modem's packing "Intel Chipset" is written and in WindowsXP's Device Manager "Intel(R) 537 Modem" is written. ScanModem tool says something about Tigerjet Communications ](*,)

---

### Post by pseudonym on 2007-02-01
So it's a PCI modem card, right? To see what's happening with it under Ubuntu, post the output of these terminal commands - 'lspci' and 'lsmod' (without the quotes)...

---

