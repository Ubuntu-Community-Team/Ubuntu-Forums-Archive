---
title: "Update GUI wants to install Kernel 6.1 for some reason"
date: 2023-07-01
forum: General Help
---

### Post by diesieben07 on 2023-07-01
Today I tried to print something on my terrible HP printer and it did not print using the default (built in?) driver. So I went to HP and found [HPLIP]("https://developers.hp.com/hp-linux-imaging-and-printing"). I ran their installer and it failed at some point due to some kind of version mismatch with Python (I am a developer, so I have Pyenv installed). Whatever, I gave up on the whole thing and just printed it using my phone.
This is just the backstory however. Now the "package updates" GUI wants to install all kinds of random kernel packages - including Kernel 6.1 for some reason:
[https://i.imgur.com/btGuCbJ.png](https://i.imgur.com/btGuCbJ.png)

Not paying too close attention I attempted to install these updates, and it dutifully installed things, only to come back again and again with the info that there are more updates (I do not have screenshots of this, because I did not know something was up at this point). After applying updates three times, I figured that something must have been broken. I attempted to reboot, only to (obviously) get stuck, because the system would not boot with whatever kernel had been installed. I fortunately could go back to the previous kernel using the GRUB menu.
However now I am still stuck with a package update GUI that wants to install random kernel packages that break my system.
Running apt update and then apt list --upgradable on the terminal shows none of these packages, instead it only shows NVIDIA driver updates:
[https://paste.ubuntu.com/p/PzzthQx5Qc/](https://paste.ubuntu.com/p/PzzthQx5Qc/)

Attempting to install these using apt upgrade does nothing and just informs me that the packages have been "kept back":
[https://paste.ubuntu.com/p/QcC4ppJjm9/](https://paste.ubuntu.com/p/QcC4ppJjm9/)

Why does the package update GUI do something different than APT? How do I find out where the bad kernel packages are coming from? And most importantly, how do I fix it?

Thank you for any insight and please let me know what, if any, additional information I need to provide.

---

### Post by diesieben07 on 2023-07-01
Uninstalling and then reinstalling the NVIDIA driver seems to have fixed it.

---

### Post by scpatl4now on 2023-07-01
I had a similar update problem this morning and just purging and reinstalling did not help I solved it with an answer I saw on the Nvidia forum.  My thread link is below.
[https://ubuntuforums.org/showthread.php?t=2488322](https://ubuntuforums.org/showthread.php?t=2488322)
My question is why are updates being pushed that break your install?

---

### Post by scpatl4now on 2023-07-01
I had a similar update problem this morning and just purging and reinstalling did not help I solved it with an answer I saw on the Nvidia forum.  My thread link is below.
[https://ubuntuforums.org/showthread.php?t=2488322](https://ubuntuforums.org/showthread.php?t=2488322)
My question is why are updates being pushed that break your install?

---

