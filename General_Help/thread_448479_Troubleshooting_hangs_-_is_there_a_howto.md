---
title: "Troubleshooting hangs - is there a howto?"
date: 2007-05-19
forum: General Help
---

### Post by hamburgerman on 2007-05-19
Hello everyone. I get periodic hangs on my feisty install - no mouse, no CTRL+F1, no nothing (except for my power switch, that is). 

Where should I start looking for the cause? Is there a troubleshooting guide somewhere? Are there specific logs I should look at?

(I can get around ok in a shell, etc, but haven't really used linux in about 10 years - wow it's come a long way!)

thanks a lot,

gage


-----------------------------------------
Info:
--AMD Sempron 3100+ w/512MB RAM
--Old nvidia card, Geforce 6600, using 9631 driver
--have beryl installed, but am using the gnome window manager
--yanked the wireless card out, so don't think that's causing the issue

---

### Post by hartz on 2007-05-19
Don't know about a how-to (did you search for one?), but there's a few things you can do.

Go back to your troubleshooting basics:
1. Look for log files, especially the syslog, messages and xorg log files.
2. Maybe it is just xorg which is hanging.  Try to log in remotely via the network, eg using ssh.  Note: For this you need to install an ssh-server.
3. Think about what has changed.  What software have you installed besides the normal software that came pre-installed.  What systems config settings have you changed.  Try disabling and/or resetting these items and see if the situation improves (elimination)
4. What components have you enabled, eg any themes/applets?  Again, try to eliminate the cause by disabling components.
5. Do you have a mis-behaving power-supply or overheating CPU?  Any other flaky hardware components, eg memory with errors?  Again, use elimination, eg remove half of your RAM, then test the system; then switch the RAM around and test the system running on the other modules.

P.S. To open a console from X, windows, you need to tap Ctrl-Alt-F1, not just Ctrl-F1.  Another key kombination to try is Ctrl-Alt-Backspace.

Have you done the numlock test (When the numlock key stops changing the state of the Numlock LED on the keyboard, you generally have a truly dead system.)

---

### Post by hamburgerman on 2007-05-19
thank you for the excellent suggestions (especially the num lock and ssh suggestions!). I think after the next hang, i'll try going back to the open nvidia drivers ('nv') rather than the proprietary ones ('nvidia') and try again. 

Again, thanks,

gage

(i'll come back and post the solution if i find one!)

---

### Post by siucdude on 2007-05-21
well this is easy to fix,  it the nvidia card.  I have the same card and it does the same thing, solution, change the nvidia to nv and you should be working,

---

