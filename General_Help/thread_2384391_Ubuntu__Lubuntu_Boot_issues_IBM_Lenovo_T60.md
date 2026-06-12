---
title: "Ubuntu / Lubuntu Boot issues IBM Lenovo T60"
date: 2018-02-06
forum: General Help
---

### Post by dorag on 2018-02-06
Hello I'm kinda to using Ubuntu / Lubuntu I know a bit about the terminal and its commands etc however after installing Lubuntu alongside Windows XP it loads to a black screen saying [COLOR=#111111][FONT=Consolas]dev/sda1: clean, 552599/6111232 files, 7119295/24414464 blocks  (this isn't exactly what my device said the numbers will be different but is the same message) [/FONT][/COLOR]It just stays on this screen permanently the only way to get it to load is to edit the grub and add nomodeset to the command line and it runs fine.

On the other side if I install Ubuntu everything is fine no issues after installing it loads right to the desktop.

---

### Post by dorag on 2018-02-18
Anyone got any ideas?

---

### Post by Impavidus on 2018-02-18
There shouldn't really be a difference between Ubuntu and Lubuntu as long as they run the same kernel. Different releases may be different though.

You already solved the problem yourself: add nomodeset.

To make this change permanent, you have to edit /etc/default/grub and run update-grub. See [https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](https://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu). Use the answer by Coldfish. I think it's still valid.

---

### Post by oldfred on 2018-02-18
You normally only need nomodeset until you install the proprietary video driver from Ubuntu's repostory?
Do you have nVidia or AMD?
And what video card/chip?
If you can boot:
sudo lshw -c display

---

