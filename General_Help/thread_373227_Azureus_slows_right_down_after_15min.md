---
title: "Azureus slows right down after 15min"
date: 2007-03-01
forum: General Help
---

### Post by detectiveinspekta on 2007-03-01
I first installed azureus through apt-get and got bad preformace after 15 min. I then downloaded java and installed bittorrent in my ~ directory. Ran a largest torrent I could find one with 10,000 seeds and 2,000 peers. After 15min the download rate drops from 200KB/s to <1KB/s. The GUI then become semi-responsive and the CPU usage drives high.
Where is the problem?

---

### Post by anaconda on 2007-03-01
I had similar problems.. solwed them by changing to utorrent run in wine..

---

### Post by Hallvor on 2007-03-01
I run Bittornado. Always very fast, and doesn`t use much memory.

---

### Post by detectiveinspekta on 2007-03-01
There is really not much measurable difference in bittorrent clients. Azureus is the best out there and I say that because I just got it working :D
The problem was with the version of java I was using. I installed 1.5 java but azureus didn't know that and used the old version bundled with ubuntu.
So java I installed was put in /usr/java/jre1.5.0_11/
You need to add in /usr/java/jre1.5.0_11/bin to PATH="" in the ./azureus.

Problem solved...(with the help of #azureus at irc.freenode.org)

---

### Post by Kateikyoushi on 2007-03-01
I would try to change the gui refresh rate of AZ to 5 seconds, that decreases cpu usage and who knows might help.

---

