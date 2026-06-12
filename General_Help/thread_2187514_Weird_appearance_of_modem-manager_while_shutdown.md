---
title: "Weird appearance of modem-manager while shutdown"
date: 2013-11-12
forum: General Help
---

### Post by seb22 on 2013-11-12
Hello forum,

I am using Xubuntu (currently 13.10) for a while now, but something weird happened lately. I shutted down the notebook, but it surprisingly took much longer than normally (also the following boot of the OS).
I rebooted again to see whats going on while shutting down (by pressing the "up"-button) -> suddenly there were several lines containing modem-manager, like "modem-manager: ttyS4 Closing Serial Port" (maybe not exactly that, because after the lines appear, the OS shuts down quickly), which havent been there about a week ago.
Isn't that strange?

I thought about uninstalling the modem-manager (because there is no modem in my notebook)...

Maybe the attached list of lately installed packages could help you to help me.
[ATTACH]247785[/ATTACH]

So, has anyone experienced that or could just tell me why this is happening?
Thanks in advance!

Best,
Seb

---

### Post by Dennis N on 2013-11-12
Seen it in shutdown messages, and yes it sometimes takes a few seconds to respond. It's used in mobile communications, so you may want to keep it:

From apt-cache show modemmanager:

> Provides a D-Bus interface to communicate with mobile broadband (GSM, CDMA,
 UMTS, ...) cards. Implements a loadable plugin interface to add work-arounds
 for non standard devices. Also provides patches to use networkmanager (and
 the applet) with modem manager.

---

### Post by seb22 on 2013-11-12
First of all, thanks for your answer. Help is really appreciated :)

But why does it appear now? Was it included in the new kernel? I never noticed it before. And furthermore: What is it doing with the serial interface (i am guessing that ttyS4 is a serial interface^^).

---

### Post by Dennis N on 2013-11-12
It's been there for years. The only message I ever see is that it is shutting down. Sorry, I have no insight about the reference to serial port. Perhaps someone else will know.

---

### Post by seb22 on 2013-11-12
Hmm...I think I will open another Thread regarding this exact question.
I found several entries in the syslog and have no idea, why the modem-manager tries to open a serial port...

But anyway, the slow boot and shutdown remains...

---

