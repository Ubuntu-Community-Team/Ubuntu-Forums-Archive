---
title: "Gnome-shell freezing at startup"
date: 2019-04-15
forum: General Help
---

### Post by buisteric on 2019-04-15
Hi,
I am using Ubuntu 18.10 MATE, but for some reason, gnome-shell gets started at boot and intermitently freezes with 99% of CPU usage. There is nothing responding, even Ctrl-Alt-F<n>, Ctrl-Alt-Delete, I need a second computer to SSH into the machine and then I can observe with "top" that gnome-shell is frozen. I cannot get logs because it is completely frozen.
 I tried many ways to unstuck without hard reset and it is pretty much impossible. Commands to restart X don't work anymore since SystemD. Before, it was possible to just go from runlevel 5 to 3 and then back to 5. Now it requires sequences of command I don't remember and each time I search for something, I get a different variation of a solution.  Killing gnome-shell doesn't work; kill does nothing now.
I'm not geeing why gnome-shell starts since I'm using MATE which should not depend on GNOME, maybe this is because I started from a Ubuntu with Unity, updated to Ubuntu with GNOME (18.04) and then installed MATE on top.
I cannot spend my time clean installing, because I cannot work with default settings (too small fonts, too small mouse pointer) and it takes me ages to figure out how to repeat and repeat all the customizations. I tried in the past to move my /home to a separate partition. On an SSD, this is inpractical, as systematically, the /home becomes too small and I need to wait forever to reorganize the SSD. So I would need, instead of a SSD, a way to install on an hard drive and use the SSD as a cache, but I cannot find anything about such a setup.
Maybe it could because of the NVIDIA driver now partly incompatible with the kernel? But I cannot spend my time swapping around graphic card. Now I would need an ATI. Next year it would be an NVIDIA again. The year after it would be something else. That just makes no sense!

---

### Post by buisteric on 2019-04-15
In case this can help, here is the log file from Xorg at the time of the last freeze.

[https://pastebin.com/bpZ5CkJ8](https://pastebin.com/bpZ5CkJ8)
[https://pastebin.com/Egqdjcsq](https://pastebin.com/Egqdjcsq)

Before the freeze, I also observed in "top" that fstrim was active. Maybe the "trim" operation is causing dead locks somehow, but I just cannot disable fstrim as I need unused blocks to be discarded on my SSD.

---

### Post by dragonfly41 on 2019-04-15
I have found that [petit]("http://crunchtools.com/software/petit/") sometimes makes more sense out of log files. Search for keywords as clues.
Recently on Ubuntu 16.04 i encountered a documented bug which prevents Python 3.6 from launching gnome-terminal.
it needs Python 3.5 apparently. But that is probably a red herring in your case.
Some other theories on general freezing are documented here .. from my bookmarks ..
[https://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes](https://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes)

---

