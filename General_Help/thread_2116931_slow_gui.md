---
title: "slow gui"
date: 2013-02-17
forum: General Help
---

### Post by witblits1970 on 2013-02-17
ive been noticing my box is progressivly running slower and slower as time goes by. i have a 3.4 Ghx quad core bulldozer chip. 16 Gig of DDR3 ram at 1333Mhz and a M5A97 Mobo. all went ok until recently when FF stalled and i tried to end the FF process. upon doing so i noticed there were 179 processes running?? is this normal seeing that in MS there is only 41-43 running on idle? to my mind having this many processes running is obviously bottlenecking my system somewhere hence the slowness. 
thanks

---

### Post by sudodus on 2013-02-17
I happen to have exactly the same number of processes running in an hp xw8400 workstation with 4 GB RAM. So it can be 'normal'. It is more interesting to find out which processes are eating cpu horsepower or ram or causing swap or other disk read/write activity.

*Edit*: I have 118 processes running in an old IBM Thinkpad T41 with Pentium M.

---

### Post by witblits1970 on 2013-02-18
ok with gui running so slow i think its time for a fresh install

---

### Post by ZippyUbu on 2013-02-18
Hi - You could run 'htop' from the terminal and see what process is consuming resources. If you don’t have the 'htop' package installed try the below:

```
sudo apt-get install htop
```Post your findings

--
Zu

---

