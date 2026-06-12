---
title: "spin down two harddisks in hdparm.conf with no effect"
date: 2020-08-01
forum: General Help
---

### Post by muema12 on 2020-08-01
Hello

As a newbie I just set up a Ubuntu-Server without a graphical interface. The OS is on a SDD-Drive. Further the system contains two 3.5" Harddisks, which are mechanical. When I try to spin down these two ones by entering the following on the command line, they spin down in two minutes, which is exactly what I want.

sudo hdparm -S 24 /dev/sda
sudo hdparm -S 24 /dev/stb

Now I tried to make this setting permanent by editing /etc/hdparm.conf like this...

/dev/sda {
        spindown_time = 24
}
/dev/sdb {
        spindown_time = 24
}

...unfortunately with no effect after a reboot. :(

What am I doing wrong? Pleas note, that I'm a newbie and maybe it is just something very simple that I haven't found out by myself. If somebody can help me or guide me thru this, I would appreciate that very much. :P

OS: Ubuntu 20.04.1 LTS
Kernel: 5.4.0-42-generic

---

### Post by dino99 on 2020-08-01
Very old QR, but might bring some hints   [https://askubuntu.com/questions/39760/how-can-i-control-hdd-spin-down-time](https://askubuntu.com/questions/39760/how-can-i-control-hdd-spin-down-time)

an other possible tweak, (but the above seems better to me)  [https://github.com/izznogooood/log-spindown](https://github.com/izznogooood/log-spindown)

---

