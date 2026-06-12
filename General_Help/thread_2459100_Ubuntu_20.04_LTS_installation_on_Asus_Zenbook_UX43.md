---
title: "Ubuntu 20.04 LTS installation on Asus Zenbook UX434F"
date: 2021-03-10
forum: General Help
---

### Post by lordgallen on 2021-03-10
Hi, 

This is by far the best laptop I have ever purchased, I hope she last at least 4 years considering the cost. The Ubuntu installation seems to have gone well, however, is there a command I can run to find any conflicts or issues with drivers, etc.... Thank-you!

---

### Post by DuckHook on 2021-03-10
In Linux, the standard way to track down issues is by examining the logs. They are arcane. There's no way around that fact. So it's more of a power&#8209;user exercise. I have no idea how comfortable you are with logs, but they can be super informative.

Other than that, if it's working well, then it's working well. When it comes to the obscurity of HW/OS, the old adage applies: "No news is good news."

---

### Post by DuckHook on 2021-03-10
**Addendum to the above…**

A few log reading tricks:

[list=1]
[*]Filter dmesg to return only errors and potential troublespots: ```
dmesg | egrep -i 'error|'warning'
```
[*]To check for crippled services: ```
sudo systemctl list-units --type=service
```
[*]Filter systemd's journal for potential issues in current boot environment (warning: this generates a lot of output): ```
sudo journalctl -b 0 -p warning
```
[*]Or filter journal for just more serious stuff: ```
sudo journalctl -b 0 -p err
```
[/list]
There are variations on the above too numerous to list. Be sure to scan syslog, kern.log, etc too. A web search for journalctl usage or the man pages of each command are always instructive.

Good Luck and Happy Ubuntuing!

---

### Post by lordgallen on 2021-03-10
I can look at logs, interpreting them is another story :P. Yes, everything seems to be fine, even the webcam works, I see nothing broken. So I am going to assume I am ok.

---

### Post by DuckHook on 2021-03-10
I hope you don't mind my nosiness, but I've just looked up your machine and it looks very interesting. It's the first time I've seen anything like the "screenpad" thingy. I'm curious: does this work the way it is supposed to with Ubuntu? Right out of the box?

---

### Post by lordgallen on 2021-03-10
> **DuckHook said:**
> I hope you don't mind my nosiness, but I've just looked up your machine and it looks very interesting. It's the first time I've seen anything like the "screenpad" thingy. I'm curious: does this work the way it is supposed to with Ubuntu? Right out of the box?

No I don't mind at all. 

It appears to work as intended with Ubuntu. It is configured under settings -> display. It's basically acts as 2nd screen.

---

### Post by DuckHook on 2021-03-10
> **lordgallen said:**
> …It's basically acts as 2nd screen.
Ah. But a touch screen. I'm a bit surprised, though pleasantly, that Ubuntu has managed to integrate it so well. Thanks for the update!

---

