---
title: "Sporadic Shutdown Hang"
date: 2007-10-28
forum: General Help
---

### Post by foxtrot23 on 2007-10-28
I've recently installed Ubuntu Gutsy on my Dell Inspiron 710m laptop.  I've found that on occasion when I shutdown using the shutdown button, the screen goes blank and the machine appears to hang.  The only way to get around it is to make use of the power button.  There is no pattern or consistency to when the issue occurs.

It has also happened in the past when I have shutdown via the shell command line (shutdown -h now).

The following appears in the syslog when the hanging problem occurs:

[COLOR=Purple]Oct 27 21:37:14 bizware init: tty4 main process (4071) killed by TERM signal
Oct 27 21:37:14 bizware init: tty5 main process (4072) killed by TERM signal
Oct 27 21:37:14 bizware init: tty2 main process (4076) killed by TERM signal
Oct 27 21:37:14 bizware init: tty3 main process (4077) killed by TERM signal
Oct 27 21:37:14 bizware init: tty1 main process (4078&#041; killed by TERM signal
Oct 27 21:37:14 bizware init: tty6 main process (4079) killed by TERM signal[/COLOR]

This is the normal sequence of events when the hanging doesn't occur:
[COLOR=Purple]
Oct 27 21:42:08 bizware init: tty2 main process (4087) killed by TERM signal
Oct 27 21:42:08 bizware init: tty4 main process (4083) killed by TERM signal
Oct 27 21:42:08 bizware init: tty5 main process (4084) killed by TERM signal
Oct 27 21:42:08 bizware init: tty3 main process (4088&#041; killed by TERM signal
Oct 27 21:42:08 bizware init: tty1 main process (4089) killed by TERM signal
Oct 27 21:42:08 bizware init: tty6 main process (4090) killed by TERM signal
Oct 27 21:42:10 bizware kernel: [  241.684000] /dev/vmmon[6173]: Module vmmon: unloaded
Oct 27 21:42:10 bizware kernel: [  241.700000] bridge-eth0: down
Oct 27 21:42:10 bizware kernel: [  241.700000] bridge-eth0: detached[/COLOR]

Am I correct in assuming that the problem is coming from the vmmon module (which I think is something to do with VMWare which I have installed)?

Any suggestions as to what I should be looking at or what I can do to rectify this problem?

Thanks

---

