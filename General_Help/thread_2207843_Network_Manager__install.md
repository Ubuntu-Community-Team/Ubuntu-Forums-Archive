---
title: "Network Manager_ install"
date: 2014-02-25
forum: General Help
---

### Post by christon74 on 2014-02-25
Hello again Ubunters of all feathers:)

I have this slim PC (do not ask me what make it is _ All I can say is the motherboard is  a FOXCONN TPS01 _ or something like that)
I once had Ubuntu installed on it. But a few days ago I decided to install XP [Yes i know XP will be die on 8th April this year]_ Now I would like this second computer to dual boot too. The problem is that when I run the ubuntu install, there is this step when the Network Manager tries to establish a connection. I have tried up to 10 times and every time NM fails to establish a connection. The odd thing is that I can connect to the web when I load XP. I should also add that this slim pc will only connect when a Usb2.0 to fast ethernet adapter is plugged in.#-o

---

### Post by varunendra on 2014-02-25
So are we trying the USB-to-Ethernet connection? If so, please show us the outputs of -
```
uname -mr
sudo lshw -numeric -C network -sanitize
```

---

### Post by christon74 on 2014-02-28
Thank you Varunendra :)
I am going to try that right now.

---

### Post by christon74 on 2014-02-28
Hello again Varunendra. Well on second thoughts, I think I am going to leave things as they are now and keep XP until it really does .... expire. (8th April). Or perhaps I will try another Linux destro, possibly one which is lighter than ubuntu and can easily be burnt on a 700 Mb CD-rom.
Anyway, thank you so much for all help and trouble. Have a nice week-end. 
Chris.

---

### Post by varunendra on 2014-02-28
No problem at all! :)

For lightweight variants, you may try Xubuntu (much recommended these days as the default Ubuntu is getting heavier) or Lubuntu (even lighter, but also being more basic in certain features).

Lubuntu fits on a CD, but Xubuntu exceeds its size, so needs a DVD.

However, if your system(s) can boot from USB, it is recommended to use Live USB instead of Live CD/DVD. Both the installation and Live session experience are much faster with USB than with an optical disc.

---

