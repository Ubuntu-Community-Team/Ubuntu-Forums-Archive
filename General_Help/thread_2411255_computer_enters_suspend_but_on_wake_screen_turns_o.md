---
title: "computer enters suspend but on wake screen turns on but stays black, motherboard beep"
date: 2019-01-27
forum: General Help
---

### Post by Macmee on 2019-01-27
I have an alienware x51 r3 with Ubuntu 18.10 kernel 4.20.

I have the proprietary Nvidia drivers installed, I'm running lightdm, Xorg and GNOME (wayward/gdm3 didn't work with nvidia).

I can enter suspend mode which puts the computer in a low power state just fine.

Upon resuming though, my monitor turns on but stays on a black screen. My second monitor stays off. The computer makes a "beep" sound every minute or so. During this time I cannot SSH into the machine nor can I enter text mode.

Does anyone know what the issue might be or how to debug it? I tried to find related logs in /var/logs but can't really see anything complaining.

---

### Post by HermanAB on 2019-01-28
This kind of problem can be very hard to debug, since you cannot see what is going on.  I suggest that you enable sshd, so that you can log into the computer from another computer over ethernet, to try and debug the issue.

---

### Post by Macmee on 2019-01-28
> **HermanAB said:**
> This kind of problem can be very hard to debug, since you cannot see what is going on.  I suggest that you enable sshd, so that you can log into the computer from another computer over ethernet, to try and debug the issue.

That's a great suggestion :D unfortunately though I'm timing out when I try and SSH into the device after waking it though so I think it's getting stuck early on in the wake procedure

---

### Post by HermanAB on 2019-01-28
Hmm, so you learned something...

It is also possible to enable the good old fashioned serial console.  In a data centre, greaybeard admins would cross over the serial ports between pairs of servers, so that when one gets buggered, they can connect with minicom from the other.

---

