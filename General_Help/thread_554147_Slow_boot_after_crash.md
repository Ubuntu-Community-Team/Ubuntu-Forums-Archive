---
title: "Slow boot after crash"
date: 2007-09-18
forum: General Help
---

### Post by Rasitiln on 2007-09-18
Occasionally my system hard locks and I have to reset by pushing the powerbutton. Most the time the freeze happens when I'm trying to run Neverwinter nights (which hates me for some reason). So it isnt some kind of deeper system issue and I'm having random freezes just the occasionally what ever game I'm trying to emulate/run goes nuts. 

After the crash the boot process takes ages, a minute or more to load grub and then 2 or 3 more minutes to get to login screen. After that everything runs just fine and if I restart the boot processes is quick. I've never had this issues with Dapper or Edgy only on Feisty Fawn. 

Can any one help me find a solution to this mildly annoying problem, or at least an answer as to why it takes so freaking long to get past even grub?

---

### Post by Rasitiln on 2007-09-18
back to the first page..

---

### Post by Rasitiln on 2007-09-19
bump

---

### Post by Rasitiln on 2007-09-19
bump

---

### Post by lavajumper on 2007-09-19
Not seeing your computer boot, this is an educated guess as to what is happening:

When Ubuntu experiences an "ungraceful" shutdown, like a system freeze or power outage, it runs a disk consistency check on the mountable drives before it remounts them. This can take an annoying amount of time (or not so annoying compared to a complete loss of data and re-install), but you REALLY want it to happen.  

If you switch to console mode during the boot cycle you can watch the disk check progress, or see what the boot process is doing that's taking so long.

---

### Post by Rasitiln on 2007-09-19
Sadly I wish that was it. It doesnt preform any sort of check while loading grub as far as I know, and the console doesnt mention any kind of a check.

---

### Post by Rasitiln on 2007-09-20
bump

---

### Post by Rasitiln on 2007-09-21
bump

---

### Post by pmg on 2007-09-22
When booting, after the Xserver starts, hold the alt and ctrl keys and press F1, which will switch to the virtual console terminal with the startup messages.  That way you should be able to see where it's spending all the time.  If usually switches back to the Xserver once it's all the way up, but I've occasionally seen it fail to do that, in which case you can switch back using alt-ctrl F7.

You might also be able to find some details in the log files under /var/log, most likey in one of dmesg, syslog, and/or messages.

---

### Post by Rasitiln on 2007-09-22
i've looked under there it does nothing out of the normal except it does everything slower. :confused:

---

