---
title: "Reboot always shuts down"
date: 2005-10-17
forum: General Help
---

### Post by elefthera on 2005-10-17
Hi

As the title suggests, every attempt to restart/reboot Ubuntu goes through the shutdown process then powers off. The PC is a HP Brio, so I'd say pretty standard motherboard and BIOS. 

FWIW WinXP on the same machine performs exactly as it should.

Any ideas?

---

### Post by dgs on 2005-10-19
I have exactly the same problem. Have you found any solution yet?

/Dennis

---

### Post by Ocxic on 2005-10-19
check you APM (advanced power managment) setting in your bios, sometimes it can screw with the system, if it's disabled, enable it or visa versa, that may help.

---

### Post by aysiu on 2005-10-19
Does it reboot when you reboot from console? ```
sudo reboot
```

---

### Post by dgs on 2005-10-19
Thanks for replying.

Ocxic, I tried to switch things on and off a little, but i doesn't seem to help me out.

Aysiu, unfortunatly not.

It worked perfectly in hoary and still does in xp so this is quite strange. It stopped working when I upgraded hoary->breezy. Then I reinstalled breezy from scratch but it didn't solve my issue.

/Dennis

---

### Post by elefthera on 2005-10-20
I'm exactly the same as Dennis here; system works exactly per spec under XP, but Ubuntu always shuts down the system. I haven't had a previous distro on this PC so I can't comment there.

And yes, sudo reboot at the console also shuts down.

Weird. Ideas anyone?

---

### Post by cwhitmore75 on 2005-10-20
I have had the same issue since upgrading to Breezy.  Nothing seems to help.  Any suggestions would be great.

---

### Post by Apostata on 2005-10-25
Got the same thing happening on this thread:  [http://www.ubuntuforums.org/showthread.php?p=443128&posted=1#post443128]("http://www.ubuntuforums.org/showthread.php?p=443128&posted=1#post443128")

Looks like we got a bug!:KS

---

### Post by Trab on 2005-10-25
i had that issue as well, it was in breezy-colony-3... but then the machine died (totally unrelated) and my new computer with breezy-colony-3 worked just fine... upgraded it to breezy-final and also worked fine... i think its a hardware issue, but i dont remember if a reinstall fixed it (sorry, i had alot of computer issues back then...)

---

