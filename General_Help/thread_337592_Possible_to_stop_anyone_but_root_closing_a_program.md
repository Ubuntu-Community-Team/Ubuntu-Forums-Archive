---
title: "Possible to stop anyone but root closing a program?"
date: 2007-01-13
forum: General Help
---

### Post by jonboy99 on 2007-01-13
Running kubuntu dapper on a dell laptop - I want to have gkrellm the hardware monitor running all the time to keep the temperatures down.  It autostarts on logon.

I'm worried that if someone else is using the laptop they may close gkrellm without realising the problems that may result.

Anyway to require the root password before it can be closed?  It is a home computer so we all use the same account, but only I know the sudo password.

Cheers
Jon

---

### Post by fnf on 2007-01-13
Each user in the system should have a separate account for security and to avoid setting
conflicts. It will also resolve your problem in a natural way.

---

### Post by jonboy99 on 2007-01-13
Not sure it will - I am loading gkrellm through the .kde/autostart folder, which I would have to do through each user, and they therefore would be able to stop it.

---

### Post by fnf on 2007-01-14
If you want to invoke a command everytime an X session starts, you may put it into
/etc/X11/xinit/xinitrc (the commands will be invoked as root). But I'm not sure whether
KDE will honor this (some WMs I have used such as IceWM, Fluxbox and e17 do).

[Edit]: In addition to xinitrc, you may want to examine Xsession scripts which are
located under /etc/X11/Xsession.d/ (just add the command into an appropiate
script or create yours). Again, the DE might be configured to ignore them or not
start them at the right moment. It's worth a shot though.

---

