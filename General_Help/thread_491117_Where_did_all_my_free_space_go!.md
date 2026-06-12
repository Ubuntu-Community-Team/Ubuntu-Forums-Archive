---
title: "Where did all my free space go?!"
date: 2007-07-03
forum: General Help
---

### Post by verucabong on 2007-07-03
Hi there-

I'm a relatively new Linux/Ubuntu user, but I'm familiar with "under the hood" things a bit because of OS X.  I have a 7.04 (Feisty) installation that's pretty basic, with the exception that I have VMWare Server installed with a Windows Vista VM that takes a max 10GB.  My hard drive is (I believe 180GB) and there *should* be enough room.  I admit that I have installed a few things through Synaptic, but I can't imagine using up all that space.  It's really a general use machine - internet, email, chat etc.  

Is there some temp space I can clear up or something?  Here's a df listing:
[HTML]Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            138141232 130582432    541612 100% /
varrun                  517640       132    517508   1% /var/run
varlock                 517640         0    517640   0% /var/lock
procbususb              517640       112    517528   1% /proc/bus/usb
udev                    517640       112    517528   1% /dev
devshm                  517640         0    517640   0% /dev/shm
lrm                     517640     23052    494588   5% /lib/modules/2.6.20-16-generic/volatile
[/HTML]

Thanks!!!

vb

---

### Post by verucabong on 2007-07-03
Well, I used Baobab to see where it all went.  Turns out my /var/log/cups folder is 115GB!!!  Specifically, the error_log.1 file.

Any reason that would happen?!

---

### Post by bodhi.zazen on 2007-07-03
What does the log file say ?

---

