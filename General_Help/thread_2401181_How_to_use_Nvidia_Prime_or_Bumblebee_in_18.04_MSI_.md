---
title: "How to use Nvidia Prime or Bumblebee in 18.04 MSI Laptop"
date: 2018-09-14
forum: General Help
---

### Post by ethanamm on 2018-09-14
this is my 3rd week using Ubuntu as my main system.
but my laptop has low battery life due to always running Nvidia driver.
i have read many tutorial across the web about how to use Nvidia Prime but i didn't found the solution yet.
i have MSI laptop with gtx1050 gpu and running 396 driver.
I want to know how can i make my Nvidia GPU turns off its power while using Intel mode.
i dont mind manual switching between intel and nvidia mode.
Thanks.

---

### Post by #&amp;thj^% on 2018-09-14
```
sudo prime-select intel
```
log out and back in>>>or reboot

---

### Post by ethanamm on 2018-09-14
i did it but nvidia driver is still running :( any fix ?

---

### Post by #&amp;thj^% on 2018-09-14
Did you log out and back in>>>or reboot?
Also what shows for this:
```
apt policy nvidia-prime
```
This link might add some light: [https://github.com/stockmind/dell-xps-9560-ubuntu-respin/issues/8](https://github.com/stockmind/dell-xps-9560-ubuntu-respin/issues/8)

---

### Post by noctis13 on 2018-09-14
All I know is Nvidia in Ubuntu 18.04 always's going to work even if Intel is the Nvidia-prime selected. The kernel of this version drop the support, or something like that, of Nvidia prime/optimus.

---

### Post by mc4man on 2018-09-14
> **ethanamm said:**
> i did it but nvidia driver is still running :( any fix ?
After doing that install inxi if not already and run
```
inxi -G
```
Post results

---

