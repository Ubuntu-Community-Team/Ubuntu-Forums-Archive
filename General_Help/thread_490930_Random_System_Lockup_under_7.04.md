---
title: "Random System Lockup under 7.04"
date: 2007-07-03
forum: General Help
---

### Post by jkounis on 2007-07-03
I have been using Ubuntu 6.06 and then 6.10 desktop editions with a lot of success as a file/web/database server. Currently I run Samba, Netatalk, Mysql, and Apache as well as both the KDE and Gnome desktop environments. 

I am running a Pentium D 2.8 GHz with 1 GB memory. Since I am using a motherboard with onboard ITE8212 raid, in both cases I recompiled the kernel to enable IT8212 support.

After upgrading to 7.04, I have run into the following problems:

     (1) MAJOR: Every 2-7 days, the machine locks up. It stops responding to pings, Ctrl-Alt-Backspace, Ctrl-Alt-Delete, Ctrl-Alt-F1 or any other key combinations don't work. The only thing I can do is hit the big RESET button to get the machine to start working again. Under version 6.06/6.10, it would run for months at a time.

     Any ideas how to troubleshoot this serious problem? Since the machine is completely locked up, it's hard for me to determine what happened.

     (2) I used to use [this procedure]("http://ubuntuforums.org/showthread.php?t=122402") to log in remotely to the Gnome desktop environment. If I try to log in to the gnome environment now, it crashes and disconnects me immediately. Simultaneously, the main console for the computer also goes black, and I have to walk over to it and type Ctrl-Alt-F7 to get the screen to display something again.
     If I select the KDE desktop environment, I get an error that states that "The application Power Manager (guidance-power-manager.py) crashed and caused the signal 11 (SIGSEGV)." However, everything works after I close the error window. So at least KDE works.

     Any ideas what's wrong with my gnome environment that vncserver no longer works with it?


Thank you!

John Kounis

---

### Post by PaulFr on 2007-07-03
For troubleshooting, I would suggest you keep a terminal session from any machine logged in into your machine using ssh (not VNC). Then when the lockup occurs, you can check what is happening on the machine using **top**, **vmstat**, **dmesg** and look in /var/log for any recent file activity.

As far as VNCServer locking up, I have no idea - you did upgrade xinetd and vncserver when you upgraded to Feisty, I hope ?

---

### Post by jkounis on 2007-08-11
After much troubleshooting, I reverted to version 2.6.17.14 of the kernel, and all my system stability problems went away. I suppose it's a little unusual to run 7.04 on the 2.6.17 kernel, but it's much more stable than the alternative. So far, the sytem has been up for 36 days without a hiccup. The 2.6.20 kernel wouldn't run for more than a day or two without hanging.

Is there a problem running Feisty on 2.6.17?

---

### Post by vexorian on 2007-08-11
not that I know off.

I guess this is something to remember, but just for the record, do you have any wireless connection going on?

now that you got isolated the problem to a kernel version it would be nice to islate it a little more and see if the devs. can fix it, also try updating the kernel to a newer one and see if that doesn't fix it

---

