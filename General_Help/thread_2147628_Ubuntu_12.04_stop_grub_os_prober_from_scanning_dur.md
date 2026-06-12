---
title: "Ubuntu 12.04 stop grub os prober from scanning during every update"
date: 2013-05-22
forum: General Help
---

### Post by nacho32 on 2013-05-22
I have Ubuntu 12.04 and a triple boot set up everytime I get a update the grub or os-prober scans my hard drives and take a long time how do I make it stop scanning everytime their is a lil kernal update ?
thanks Jeff

---

### Post by Irihapeti on 2013-05-22
To stop os prober, you need to make the script /etc/grub.d/30_os-prober non-executable.

Run the command
```
sudo chmod -x /etc/grub.d/30_os-prober
```

Are your other systems Linux or Windows?

If they're Windows, the above should do what you want. If they're Linux, you'll still need some way for grub to handle the fact that they also will get kernel updates from time to time.

---

### Post by nacho32 on 2013-05-22
that is correct I have a xp windows 7 and ubuntu 12.04 how would I manually update it? I add a new hd with xp on it and some one told me to run a command like sudo update grub and this is when the whole problem started

---

### Post by nacho32 on 2013-05-22
so now everytime I get a kernal or some update it scans the heard drives and takes a long time

---

### Post by Irihapeti on 2013-05-22
Ok, you have two Windows installs plus Ubuntu.

Then you should be all right with just running the command I gave in my earlier message.

I just wanted to be sure that you didn't have another Linux, in which case you would have needed to do something else as well.

---

### Post by andrekp on 2013-05-23
Some linux installs (i.e. Arch) don't need to update grub when the kernel updates (new kernel has same name and replaces old one).    My advice:  If you have a collection of O/S that you load, and ONLY Ubuntu needs to update-grub when the kernel changes, then run update-grub once to get the menu made, then cut and past the non-Ubuntu entries into the 40-custom file (whatever it's called) in /etc/grub.d, then disable os-prober as stated here.  Now when the installer automatically runs update-grub, it will update for Ubuntu, and ignore everything else, just loading the menu entries you amde that first time.  Works great.

---

### Post by nacho32 on 2013-05-23
great thanks for the reply's will try  tomorrow thanks again !

---

