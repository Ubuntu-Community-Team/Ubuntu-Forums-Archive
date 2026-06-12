---
title: "ubuntu 19.10 boots to a tty instead of gui login"
date: 2020-04-14
forum: General Help
---

### Post by kaybee19 on 2020-04-14
Hey there, im running ubuntu 19.10 along with windows 10 on lenovo legion y540
I havent faced this problem before but since i upgraded to 19.10 ,first i got stuck at **IWLWIFI **error ,that still persists but im able to boot to a tty.
After logging in that tty im able to run startx to bring up the gui but i cant make it automated and have to do it each time i boot.
Any help would be appreciated.
Cheers :D

Edit: I just switched to lightdm and it works now, still no idea why gdm3 didnt start on boot

---

### Post by gsahli on 2020-04-14
In terminal, try 
sudo systemctl set-default graphical.target

---

### Post by kaybee19 on 2020-04-16
sadly that didnt work,no change.

---

