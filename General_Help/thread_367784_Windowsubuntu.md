---
title: "Windows/ubuntu"
date: 2007-02-22
forum: General Help
---

### Post by Boule on 2007-02-22
Hi,

I've noticed a couple of things since using ubuntu...

1. my laptop battery doesn't seem to last as long. I tested that by restarting and alternatively booting into windows and ubuntu, I always seem to lose around 30min. I'm not using anything fancy under windows, the portable/laptop scheme of the native driver.

2. on my desktop, the download speed when using torrents is extremely slow in ubuntu. utorrent and azureus under windows are faster than ktorrent and azureus under ubuntu.

Any ideas ?

---

### Post by blueglow on 2007-02-22
Hi Boule,

Not sure about (2), but as for (1): have you tried running powernowd? I found my Pentium M was always running at 2Ghz when there was no load. After running "**sudo powernowd**" it behaves itself and drops to 800Mhz when idle.

Jim

---

### Post by sardion on 2007-02-22
I hate to have to say this (since I love linux) but the 2.6.17 kernel (the default in edgy) has a dirty hack for pentium m processors that in some cases (dothan chips) causes it to run them with more power than is strictly necessary.  It won't hurt the chip at all (I repeat not at all) but it can eat up power.

Use powernowd or powersaved, that will help.  But this is one of those things in the linux kernel that is fixed in the newer versions.  So in feisty it should be better.

---

### Post by Boule on 2007-02-22
OK, I tried both. It doesn't seem powersaved is installed
powernowd ran fine, but except from openning system monitor and watching all processes, I couldn't see it. Isn't there a way to configure it ?

Will it run at startup, or do I have to manually add it ?

EDIT: I checked /etc/init.d and I found an entry there. So I guess it has been running the whole time. So now I wonder what happened when I typed the command, did it just display some info and went on with its business ?
In preferences->session->startup, there is gnome-power-manager. Are those 2 things different ?

---

### Post by Boule on 2007-02-22
Well I guess that [thread]("http://ubuntuforums.org/showthread.php?t=331161") answers my 2nd question

---

### Post by blueglow on 2007-02-22
With regard to powernowd startup, well my system allegedly started it up on boot it too, but yet I still had to run the damn command every session to get it to control the frequency properly. Could be user error as I'm a noob but in the end I added the call to powernowd to the /etc/rc.local file. Probably a hideous misuse of protocol/design/whatever, but it worked so there you go. (If any passers-by have any thoughts on this?)

In order to see powernowd in your system monitor, ensure you have "All Processes" in the view menu selected. I believe it runs as a daemon (whatever that means!).

I also recommend adding the "CPU Frequency Scaling Monitor" to one of your GNOME panels top or bottom to show you what the cpu is up to.

---

