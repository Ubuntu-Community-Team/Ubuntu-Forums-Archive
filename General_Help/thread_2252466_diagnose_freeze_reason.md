---
title: "diagnose freeze reason"
date: 2014-11-12
forum: General Help
---

### Post by atlante on 2014-11-12
Hi all, 
i'm writing here after days and days of search in log files, googling ecc....without any result.
I'm using Ubuntu from years without any problem. My hardware is:
Lenovo ThinkStation E30, Intel C206 chipset, Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz, 8GB RAM.
I used this hardware without problems with ubuntu 10.04 64bit LTS until september 2014, with 2 1tb hdd configured in software raid 1 with mdadm, workstation ALWAYS ON, NEVER CRASHED.
Then, i decided to update.
I installed ubuntu 14.04 64bit. Configured mdadm and raid 1. Here started the problems. Sometimes....i didn't know why and when (also tried without any programs left opened!) i find the thinkstation completely freezed!
No ping, no screen...nothing.
I also tried to replace the hdd's, new fresh install of Ubuntu 14.04, WITHOUT RAID....same problem.
I haven't found NOTHING in the various LOG FILES!
Memtest OK
Tried to disable Suspend following this guide [http://askubuntu.com/questions/452908/how-to-disable-suspend-in-14-04](http://askubuntu.com/questions/452908/how-to-disable-suspend-in-14-04)
...nothing changed


So....i'm wrinting here to ask if you can help me in diagnosing the problem.


Any idea?

---

### Post by atlante on 2014-12-01
Hi all, 
the same problem happens on other Lenovo Thinkstation!
- another Thinkstation E30, Intel C206 chipset, Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz, 8GB RAM (same as mine)
- a Thinkstation E32, Intel C226 chipset, Intel(R) Xeon(R) CPU E3-1225 v3 @ 3.20GHz, 8GB RAM (different as mine)
The same way, with Ubuntu 10.04 OR 12.04 NO PROBLEMS at all, all the problems start when i install 14.04. Also here NO upgrade but new installation!
When the PC freezes i also tried the "magic sysrq" key (that i previously configured) but nothing happens: no possibility to reboot, show processes...nothing.


Any little idea?

---

### Post by tgalati4 on 2014-12-01
Are there any other cards in these systems?  It's possible there is a pci_e card that the newer driver is causing lock-up issues.  Try stripping one machine down to basics, no extra cards and see what the result is.  Try booting using a LiveUSB of 14.04 (use the latest version of 14.04).  Try Linux Mint MATE 17 in case Unity 3D graphics are causing an issue.

---

### Post by mörgæs on 2014-12-01
Before taking the hardware apart I suggest a live boot of L/Xubuntu 14.10.
Drivers for Intel graphics have improved in the latest kernels.

---

### Post by atlante on 2014-12-01
Thank you for the reply!
-The pcs have no pci_e cards.
-We are using gnome-session-fallback metacity, no graphic effects.
We are using LTS version of Ubuntu since 6.06, and we prefer not to change for a non LTS one! (ex. 14.10 or Mint...)

---

### Post by tgalati4 on 2014-12-01
Are you running 32-bit or 64-bit versions of Ubuntu?  Without some log messages, this would be difficult to troubleshoot.

---

### Post by atlante on 2014-12-02
Good morning,
64 bit as i mentioned above.
As i told first, I haven't found NOTHING in the various LOG FILES! Nothing that seems similar to an error in the minutes around the freeze!
So i'm writing here asking were to start....i don't know ..i wonder if there is a "debug mode" to run the S.O. to have more verbose logs...or something similar?!

---

### Post by tgalati4 on 2014-12-02
Try declocking the computers in BIOS.  Turn down to lowest speed possible.  If the machine boots then try logging in with another machine (using 12.04, or something that works) using *ssh* and keep the terminal open in case there is a freeze.

Once the machine freezes, see if you can get it to boot with the [magic sysrq keys]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Commands"). 

It's not much to work with, but it may narrow down what is going on.

Additional tips:  [http://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop](http://askubuntu.com/questions/11002/alt-sysrq-reisub-doesnt-reboot-my-laptop)

---

### Post by I.Bun.Tu on 2014-12-12
I am having a freezing issue on my Lenovo Ideapad y410p and this was the only discussion I found of a similar issue.

I  have one question, when the system freezes, are you able to pop over to  another tty and pop back to unfreeze the system? If so, I believe we  are having the same issue. If not, I will start a new thread.

To  clarify, when my system freezes the mouse cursor usually stops mid swipe  or something and I can't give any input to the system. Then I switch to  a tty (via ctrl+alt+f4 or f3 or f5, etc.) and then back (via ctrl + alt  + f7) to the desktop environment. 

I tried this the first time  my system froze and it has always worked so I haven't bothered to  troubleshoot the issue but I am finally getting around to it so let me  know if your system freeze can get unlocked in the same way. cheers

---

