---
title: "Ubuntu running slowly"
date: 2008-03-02
forum: General Help
---

### Post by TheWhatkin on 2008-03-02
Ubuntu abruptly started to lag something awful a day or so ago; my CPU is now idling at something around 60% much of the time.

Info that may or may not be useful:
-Ubuntu 7.10 running on an Acer laptop with a 1.60 GHz processor and 2 Gig of RAM.
-top tells me that the process sucking up all my CPU cycles is called ntos_wq; google tells me this is related to ndiswrapper, but not how to fix it.
-ndiswrapper is being used to make an atheros ar5007eg card work.
-ndiswrapper was installed from sourceforge.

I don't /think I did anything to trigger the slowdown - the only change I'd made tot he system imediately prior was turning off the bluetooth applet.

So...help?

---

### Post by ryanhaigh on 2008-03-02
This may be the result of a kernel update which may mean that your ndiswrapper module needs to be recompiled. To see if this is in fact the case you could try booting with the old kernel and see if the issue remains. If it does not then you may simply need to recompile the ndiswrapper module as you did when you installed (unfortunately this is one of the issues with using driver level software from outside the ubuntu repositories)

---

### Post by TheWhatkin on 2008-03-02
Uninstall and reinstall doesn't solve the problem, unfourtionately. Any other suggestions?

---

### Post by TheWizzard on 2008-03-02
you can see what's using your cpu with the command top

personally i'm not a fan of using ndiswrapper

---

### Post by Dojan5 on 2008-03-02
> **TheWizzard said:**
> you can see what's using your cpu with the command top

personally i'm not a fan of using ndiswrapper
He did use the command top.
It told him that the process hogging all the CPU was something that had to do with ndiswrapper
ntos_wq was the process.

::::EDIT::::
Kill the process ntos_wq and ndiswrapper and start them up again. It might work.
Else you can try to reinstall ndiswrapper, see if it works.

---

### Post by TheWhatkin on 2008-03-02
Stupid question time: How do I kill the processes?

typing k and then the PID into the terminal with top running gives me Kill of PID 3759 failed: Operation not permitted.

Also, would it be possible to install an older version of ndiswrapper(and possibly less troublesome) from the ubuntu repositories? How?

---

### Post by TheWhatkin on 2008-03-02
New information:

Uninstalling then recompiling ndiswrapper fixes the problem, but only until I reboot the computer a second time. After that ntos_wq starts eating 40 - 60 % of my CPU again.

---

### Post by TheWizzard on 2008-03-03
> **TheWhatkin said:**
> Stupid question time: How do I kill the processes?

typing k and then the PID into the terminal with top running gives me Kill of PID 3759 failed: Operation not permitted.

Also, would it be possible to install an older version of ndiswrapper(and possibly less troublesome) from the ubuntu repositories? How?

sudo killall whatever

---

