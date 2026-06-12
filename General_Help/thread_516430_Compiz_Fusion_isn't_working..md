---
title: "Compiz Fusion isn't working."
date: 2007-08-03
forum: General Help
---

### Post by linux123 on 2007-08-03
Hello, i have installed compiz fusion, but when i give the command compiz --replace, nothing happens. I have reinstalled my vga card driver in various methods. But it didn't help to solve my problem. I'm using Radeon X200 onboard vga card. can someone help me to get Compiz Fusion working on my desktop? 

Channa.

---

### Post by khughitt on 2007-08-03
Did you install drivers for your ATI card? What guide did you following to set-up compiz fusion?
Bring up a console and type **fglrxinfo**, and copy and paste the results here.

Keith

---

### Post by linux123 on 2007-08-03
At first i tried the ATI driver with envy. When the compiz didn't work, i removed the envy driver and reconfigured xorg and then followed this guide :

[http://ubuntuforums.org/showthread.php?t=488385&highlight=install+compiz+fusion](http://ubuntuforums.org/showthread.php?t=488385&highlight=install+compiz+fusion)

this is what is gives when i applied the command fglrxinfo. 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by khughitt on 2007-08-03
Okay, your driver looks like it is good. What happens when you run compiz --replace in a terminal? (what does it output?) Did you restart your x-server, and log in to "xgl" rather than "gnome"?

---

### Post by linux123 on 2007-08-04
Yeh, I didn't log in x-server with XGL,
When I Log in using X-SERVER with XGL, Its Working!!
Thanks a Lot!

---

### Post by khughitt on 2007-08-04
np. glad you got it working :)

---

### Post by Jofaba on 2007-08-04
So do you need XGL for Compiz to work? I have an nVidia 7900gt and just like him, everything installed properly but "compiz --replace" wont work. When I try it through terminal I get this:

Fatal: Failed test: Composite extension
Checks indicate that it's impossible to start compiz on your system.

---

### Post by khughitt on 2007-08-04
> So do you need XGL for Compiz to work?

Hmm.. good question. I'm not exactly sure. I think it's also supposed to be possible with [AIGLX]("http://en.wikipedia.org/wiki/AIGLX").

Can you paste you paste the contents of your /etc/X11/xorg.conf file to the forum? I think your problem may be with your xorg configuration.

---

