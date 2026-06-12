---
title: "Seemingly random crashing with no option but hard reset"
date: 2014-06-09
forum: General Help
---

### Post by anforiummusic on 2014-06-09
I am using Xubuntu 14.04 64 bit on a system with these specs:
Core 2 duo e4300
3 gb RAM
NVIDIA Geforce 210 graphics (using the latest nvidia driver from the xorg-edgers ppa)
50 gb OCZ Vertex 2 SSD

The system crashes seemingly at random. There is no common factor as to when the crashes occur. They happen during a variety of tasks, such as web browsing, music production,basic office tasks etc. Once the system freezes, I am unable to press ctrl-alt-f1 (or any other "f" keys) to switch to a terminal. I am also unable to use any alt-sysrq combinations -- I have tried dumping the crash info and REISUB to reboot with no success. My memory passes the memtest86 tests just fine, and the temperatures stay within a reasonable range. I have no idea what else to try at this point, and it is quite an urgent issue, as it's impossible to get any real work done when I have no idea when the next crash will occur.

Any ideas?

---

### Post by robin7 on 2014-06-09
I suggest trying the 32-bit version.  In some 64-bit environments there are bugs that simply don't appear in their 32-bit counterparts, and for most users there is no noticable difference in performance.

---

### Post by pqwoerituytrueiwoq on 2014-06-10
have you checked the xorg/lightdm logs?
does REISUB work?
[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by anforiummusic on 2014-06-10
> **pqwoerituytrueiwoq said:**
> have you checked the xorg/lightdm logs?
does REISUB work?
[http://blog.kember.net/articles/reisub-the-gentle-linux-restart/](http://blog.kember.net/articles/reisub-the-gentle-linux-restart/)

No, I said in the OP that I had tried the sysrq combinations with no success. REISUB works fine when the system isn't frozen, however.

Where do I find the lightdm logs?

---

### Post by pqwoerituytrueiwoq on 2014-06-10
in /var/log/lightdm/

---

### Post by anforiummusic on 2014-06-10
> **pqwoerituytrueiwoq said:**
> in /var/log/lightdm/

There doesn't seem to be anything regarding errors/crashing in it. What exactly am I looking for?

---

### Post by pqwoerituytrueiwoq on 2014-06-10
have you tried to recover via ssh? (requires second system) that usually works for me when i have that problem, only once had that not work

---

### Post by anforiummusic on 2014-06-17
I tried installing the 32 bit variant to no avail. The system crashed about 5 hours after the install, in the same way as normal. Still no crash data in /var logs. I may try to install Windows to see if the problem occurs there as well

---

