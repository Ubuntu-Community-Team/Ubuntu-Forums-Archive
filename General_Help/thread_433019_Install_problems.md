---
title: "Install problems"
date: 2007-05-04
forum: General Help
---

### Post by randy1984 on 2007-05-04
Ok so I decided to install Ubuntu yesterday. I downloaded and burned the cd, installed. Well on reboot I got the "failed to start the X server" error. I found out this was from me having an ATI card. My card is an ATI Radeon 9200.

So I did these steps...

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

I then rebooted and got the same problem. So I tried doing the same steps but instead of rebooting I did a "startx"

That gave me a new error. This is what the screen said...



(WW) fglrx: No matching Device section for instance (BusID PCI:1:4:1) found

(EE) No devices detected.

Fatal server error:
no screens found

Xl0: fatal IO error 104 (Connection reset by peer) on X server ":0.0:"
After 0 requests (0 known processed) with 0 events remaining

Xauth: error in locking authority file /home/randy/.Xauthority




Alright so I have no clue what is wrong. I'm new to Ubuntu and have no idea what to do. This is so frustrating that I'm contemplating just restoring and installing XP again. Someone please help.

---

### Post by randy1984 on 2007-05-04
Anyone? I need help as soon as possible. If not I'm just restoring in a little bit. My first taste of Ubuntu has been horrible.

---

