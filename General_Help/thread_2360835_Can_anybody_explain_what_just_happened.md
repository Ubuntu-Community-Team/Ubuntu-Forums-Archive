---
title: "Can anybody explain what just happened?"
date: 2017-05-09
forum: General Help
---

### Post by emptyocean1 on 2017-05-09
Ok so I'm actually making an account on this site just to sort of ask if anybody can explain this mystery I've been dealing with for the past couple of hours. So to start out I just recently moved to ubuntu as my primary OS (yaay). I set up a partition and halved my ssd in order to do a dual boot of windows and ubuntu, like a lot of you guys do. I love ubuntu and for the past few months i haven't even touched windows unless I had to. So this is where the weird stuff starts happening. I decide I want to try out Tails, so I go through the process of downloading and installing and everything is easy, i do a reboot on my pc in order to boot into tails on my flash drive and I get some sort of error message saying I cant boot in safety mode, so I restart and all of the sudden my boot manager isnt there, it just goes straight into windows. So I go through the nightmare that is actually trying to disable all of windows' crap in order to get back into the bios and load into ubuntu and...its not there, theres no option for it. So i do some hunting and discover that I need to go into Ubuntu live mode and run a boot repair. Fortunately I still have the original USB from when i first installed ubuntu so after some fiddling and doing stuff like turning off safe boot and all that jazz I finally get boot repair to work. Doesnt work. Still no boot option for ubuntu. So after about an hour and and a half of trying to figure out how to get into it I decide to check my partitions. Windows is telling me theres nothing on the partition, no boot files and reading as "100% Free". So now I'm stumped. Did my computer just completely wipe all the data from ubuntu? Without telling me? Or is Windows somehow hiding ubuntu? I have backups of everything important on the cloud fortunately so all i really lost is my time but I would sort of like an autopsy of the situation.

TL;DR Tried to run Tails, computer wigged out, windows is now saying ubuntu no longer exists on my computer.

---

### Post by QIII on 2017-05-09
Hello!

This isn't really a question about the installation or upgrade of Ubuntu, but a question of what happened when you attempted to install Tails.  General Help should be a better fit.

---

### Post by HermanAB on 2017-05-09
Hmm... So you had Windows and Linux dual booting, then you went and installed another version of Linux and aborted halfway?

All I can say is - don't do that.  If you want to experiment with operating systems, install Virtualbox and experiment in virtual machines.

BTW, Windows doesn't understand Linux file systems, so you cannot use Windows to debug Linux.  Rather boot off your original Linux install disc/USB widget.

---

