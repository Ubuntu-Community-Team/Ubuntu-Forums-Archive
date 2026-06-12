---
title: "I have fubared CUPS"
date: 2021-08-02
forum: General Help
---

### Post by Acharn on 2021-08-02
Working on Ubuntu 20.04 LTS. I have been unable to print to my Canon G2010 all-in-one. I'm able to scan with it, but not print. I was gathering data to send with a bug report. Early afternoon I got email saying the Thai government has set up a new center to register expatriates for Covid-19 vaccination, and I used the scanner to copy my passport to send with the registration. It worked flawlessly, but sometime later I tried looking at Settings > Printers and it says, "Sorry, the system printing service doesn't seem to be available." I'm also unable to connect to 127.0.0.1:631, which I was able to do a couple months ago. In desperation I ran: ```
sudo apt-get purge cups
sudo apt-get install cups
``` and it came back that the installed CUPS is already the latest version.
Then I ran ```
$sudo /etc/init.d/cups start
Starting cups (via systemctl): cups.service.
```
but I'm still unable to connect to 127.o.o.1:631 (or localhost:631). In a way this isn't too bad, because I wasn't able to print anyway, but it's very scary. This particular installation is experimental, so if I reinstall it it's only a matter of configuring the browser and installing a few programs, but I'd rather find out how to fix it if I can.

---

### Post by Acharn on 2021-08-03
Never mind. Easiest thing to do was re-install Ubuntu. Luck I hadn't yet done any work on this installation.

---

