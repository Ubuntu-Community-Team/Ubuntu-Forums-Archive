---
title: "numberpad doesn't work in 8.04"
date: 2008-04-25
forum: General Help
---

### Post by ejay563 on 2008-04-25
Hi,

    I just upgraded to 8.04, and for some reason my numberpad doesn't work. The numlock is on, but it still acts like arrow keys, and no numbers who up when I type. Anyone know what's going on?

---

### Post by ejay563 on 2008-04-25
I've messes around with all the keyboard settings related to the numberpad, but nothing changed. It's a Dell usb multimedia keyboard, and it worked fine in 7.10, so I'm not sure what's wrong. Help please?

---

### Post by explemonk on 2008-04-25
What happens if you turn off numlock?  In both Arch and Kubuntu Hardy I have the problem where my numlock light reflects the opposite state; that is, if the numlock light is on, numlock is actually off, and if the light is off, numlock is on.  Both my Arch and Kubuntu installs are running the 2.6.24 kernel.

---

### Post by ejay563 on 2008-04-25
My numlock key seems to be inneffective, the keys act as arrows whether or not the indicator light is on. I noticed it works properly at the login screen, (my password includes numbers, and out of habbit I used the numberpad, and it worked) but after the login screen it doesn't work.

---

### Post by elwingert on 2008-04-25
Same thing happened to me, my fix was to do the following:
System -> Preferences -> Keyboard -> Mouse Keys (tab) -> Uncheck "Allow to control..."

---

### Post by juan@forum on 2008-04-25
> **elwingert said:**
> Same thing happened to me, my fix was to do the following:
System -> Preferences -> Keyboard -> Mouse Keys (tab) -> Uncheck "Allow to control..."

thanks...

---

### Post by dougie173 on 2008-10-02
> **elwingert said:**
> Same thing happened to me, my fix was to do the following:
System -> Preferences -> Keyboard -> Mouse Keys (tab) -> Uncheck "Allow to control..."

Thanks

---

### Post by Neil H. on 2009-01-24
Thanks elwingert.

I've just switched to 8.10 (hopefully for good) after playing with Ubuntu on and off since 7.04. I had this same keyboard bug after my recent install, and your fix seems to be working.

---

