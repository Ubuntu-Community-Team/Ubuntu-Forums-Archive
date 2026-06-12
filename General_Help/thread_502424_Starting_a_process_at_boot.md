---
title: "Starting a process at boot"
date: 2007-07-16
forum: General Help
---

### Post by hollandwl on 2007-07-16
I have installed Ubuntu Server 7.04.  I have installed NetApp's Data ONTAP simulator on that.  How do I configure Ubuntu to automatically start the simulator when it boots?  The script to start the simulator is /sim/runsim.sh.  I would really like it to run interactively on one of the tty's.

---

### Post by ayoli on 2007-07-16
i dunno exactly what you want to run, but if you want to run an app at boot you should use /etc/rc.local script and put your command just before last line (exit 0).
hope that helps you.

---

### Post by hollandwl on 2007-07-16
I had tried that, but when I try to login the process terminates.

---

### Post by Carrot425 on 2007-07-16
You could try using the GUI and go to System > Preferences > Sessions > Startup Programs

---

### Post by pointone on 2007-07-16
You can add a line to the end of /etc/event.d/ttyX for the desired terminal you want to run, I believe. I only have experience *editing* the existing line to run something instead of getty, but I don't see why adding a line at the end wouldn't work, either. Try it out.

---

### Post by hollandwl on 2007-07-17
> **Carrot425 said:**
> You could try using the GUI and go to System > Preferences > Sessions > Startup Programs

Using Ubuntu Server - no GUI

---

### Post by hollandwl on 2007-07-17
> **pointone said:**
> You can add a line to the end of /etc/event.d/ttyX for the desired terminal you want to run, I believe. I only have experience *editing* the existing line to run something instead of getty, but I don't see why adding a line at the end wouldn't work, either. Try it out.

Thanks, I'll give that a try.

---

### Post by hollandwl on 2007-07-18
> **hollandwl said:**
> Thanks, I'll give that a try.

That didn't work.

---

### Post by Spudgun on 2007-07-18
Should be able to do it with a [crontab]("http://www.hmug.org/man/5/crontab.php").

---

