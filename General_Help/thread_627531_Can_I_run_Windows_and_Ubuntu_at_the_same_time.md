---
title: "Can I run Windows and Ubuntu at the same time?"
date: 2007-11-30
forum: General Help
---

### Post by LALING on 2007-11-30
I was wondering if it was possible to run Windows and Ubuntu at the same time on the same computer.

For example, can I switch from Windows desktop to Ubuntu without shutting the computer off and booting to Ubuntu and vice-versa.

My Windows and Ubuntu are installed on their own separate drive.

---

### Post by mellowd on 2007-11-30
Not really. You can do it via virtualisation though. You can run a Windows XP system inside of a Linux system but it's impossible to have them both running natively at the same time

---

### Post by eriqjaffe on 2007-11-30
> **mellowd said:**
> Not really. You can do it via virtualisation though. You can run a Windows XP system inside of a Linux system but it's impossible to have them both running natively at the same timeIt's possible, using VMWare Player, to run your physical Windows installation simultaneously.

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

There are a handful of caveats to keep Windows from getting horribly confused if you try to boot directly into it, but it's certainly doable.

---

### Post by atlfalcons866 on 2007-11-30
use virtualbox thats what i use to do with ubuntu in windows xp now i have ubuntu on its own partition and windoze vista on the last partition

---

### Post by mellowd on 2007-11-30
> **eriqjaffe said:**
> It's possible, using VMWare Player, to run your physical Windows installation simultaneously.

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

There are a handful of caveats to keep Windows from getting horribly confused if you try to boot directly into it, but it's certainly doable.

This is exactly what I said. This is not running it natively. This is running it through virtulisation.

---

### Post by eriqjaffe on 2007-11-30
> **mellowd said:**
> This is exactly what I said. This is not running it natively. This is running it through virtulisation.Well, yeah, but any changes to make to the Windows machine in VMWare would then be reflected if you boot natively into Windows, so it's sort of a quasi-virtualization at that point.

---

### Post by criskat777 on 2007-11-30
I use Virtual box with Guest Additions it works sweet. Windows Vista as Host and Ubuntu as guest. dual screen.  On my left Vista an Ubuntu to the Right of Vista.  I really wish i could run Ubuntu all the time but my Ubuntu install after i did all my additions 3D Desktop+Compiz Fusion +Effects+Dual screen+AWN  is having random freeze that i think is my Xserver but have no idea how to fix even thou i have read hundreds of threads:confused: .But O well some day it will work how i want it to:lolflag:.

---

