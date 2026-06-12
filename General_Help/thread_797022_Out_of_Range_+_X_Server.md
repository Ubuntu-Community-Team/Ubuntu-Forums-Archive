---
title: "Out of Range + X Server"
date: 2008-05-16
forum: General Help
---

### Post by d4ni on 2008-05-16
Hi everyone, since I upgraded to Hardy im experimenting some problems..

Starting with the "Out of Range" problem when I boot into ubuntu sometimes I get the "Your video card was not detected" and I have to make some manual fixes and choose a very low resolution so I can bypass that.. and sometimes I get "Out of Range" error from my monitor and I have to restart (sometimes several times until it works) .

Then I installed my vid-card drivers using ENVY and the installation run smoothly but when I reboot and I go to System => Administration => NVIDIA X Server Settings  I get the following error:

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

So I do what im told... "nvidia-xconfig" as root, and then I try restarting the X Server with   Cntrl+Alt+F1 and my screen goes black and I get the "Out of Range" problem from my monitor, so my only escape is to make a forced reboot =/      any ideas?

---

### Post by Gunman1982 on 2008-05-16
You can try to restart your graphical server by pressing ctrl+alt+backspce.
If you use ctrl+alt+f1 you just switch to a text console. I can't help you on the nvidia problem though, sry.

---

### Post by d4ni on 2008-05-17
> **Gunman1982 said:**
> You can try to restart your graphical server by pressing ctrl+alt+backspce.
If you use ctrl+alt+f1 you just switch to a text console. I can't help you on the nvidia problem though, sry.

still Our of Range  =/

---

### Post by d4ni on 2008-05-17
/bump

---

