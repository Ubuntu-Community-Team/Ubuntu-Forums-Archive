---
title: "i have a problem MINOR"
date: 2007-12-13
forum: General Help
---

### Post by drudogg on 2007-12-13
i have tried to install an update and also was trying to install FPROT antivirus and i get the same error

here is a cut/paste from my terminal

drudogg@drudogg-ubuntu:~$ sudo apt-get install build-essential libgtk2.0-dev checkinstall
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
drudogg@drudogg-ubuntu:~$ 
drudogg@drudogg-ubuntu:~$ dpkg --configure -a

then it asks for my password, and i give it then it says command not found.

what is it wanting me to do and why is it not doing it?

---

### Post by taurus on 2007-12-13
Try

```
**sudo** dpkg --configure -a
sudo apt-get update
sudo apt-get install build-essential libgtk2.0-dev checkinstall
```

---

### Post by drudogg on 2007-12-13
thanks i figured that i was leaving something out!

what would cause the download to slow to a crawl 

  0K .......... .......... .......... .......... ..........  1%  257.63 KB/s
   50K .......... .......... .......... .......... ..........  3%  559.04 KB/s
  100K .......... .......... .......... .......... ..........  5%  334.29 KB/s
  150K .......... .......... .......... .......... ..........  6%   86.30 KB/s
  200K .......... .......... .......... .......... ..........  8%    4.91 KB/s
  250K .......... .......... .......... .......... .......... 10%    3.84 KB/s
  300K .......... .......... .......... .......... .......... 11%    2.83 KB/s
  350K .....


one try it got down to 4.xx B/s

---

### Post by drudogg on 2007-12-13
0K .......... .......... .......... .......... ..........  1%   64.17 KB/s
   50K .......... .......... .......... .......... ..........  3%  463.42 KB/s
  100K .......... .......... .......... .......... ..........  5%  607.24 KB/s
  150K .......... .......... .......... .......... ..........  6%  348.38 KB/s
  200K .......... .......... .......... .......... ..........  8%   33.87 KB/s
  250K .......... .......... .......... .......... .......... 10%    3.69 KB/s
  300K .......... .......... .......... .......... .......... 11% *** 176.58 B/s***
  350K .

---

### Post by drudogg on 2007-12-13
this file is 2.9mb and i have dsl an it has taken more thatr 10 minutes and i have restarted the computer and tried it again and the above information was from last try, still running...

---

### Post by drudogg on 2007-12-13
okay after many tries i got this to work. and i got gnash plyer installed too. 

i can't mount my other hard drive or my two windows partitions. don't need the windows partitions but i do need the extra hard drive.

i have 4 partitions on the sata drive and one on an ide

partitions are as follows 
1st - win xp
2nd - win vista
3rd - ubuntu 7.10
4th - swap

all of these did show up at first.

---

### Post by drudogg on 2007-12-13
really need to gain access to by backup drive it has all my data on it... jsut wanted to test play a sond or something and - nada it won't mount.

---

