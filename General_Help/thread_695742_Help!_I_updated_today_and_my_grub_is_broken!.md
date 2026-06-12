---
title: "Help! I updated today and my grub is broken!"
date: 2008-02-13
forum: General Help
---

### Post by Jennabob on 2008-02-13
I did my upgrades today and it asked me to restart, so I did. When I got to the part where I was going to get my login in screen I got a terminal like setting. It would not boot up or start any graphical programs! I had to boot up on a old grub which I believe is off my particition I have going. Does anyone have any ideas how to fix this so I can get back to the latest verison with out having to reinstall?

---

### Post by wirawan0 on 2008-02-13
Please let us know:

- what versions of ubuntu you are upgrading from and to?
- in the "terminal-like" screen, were you offered a login prompt like this:

Ubuntu 7.10 hostname tty1

hostname login: _


Wirawan

---

### Post by Jennabob on 2008-02-13
I am using Gusty and I have kept everything upto date as far as I can. I was just doing the normal update manager updates this morning.

The screen I got after I rebooted did offer me a log in that looked like that but after that it remained in a text mode.

---

### Post by benzo8 on 2008-02-13
It sounds like your upgrade included a kernel upgrade (hence the reboot requirement). If you're using restricted or proprietary drivers for your graphics card, they will need to be rebuilt for the new kernel before Xorg can load them and give you a graphical login prompt.

Not knowing how you installed your drivers in the first place, I can't offer much more advice, but if you're using an NVidia or ATI card then Envy will help you reinstall the drivers.

---

### Post by Jennabob on 2008-02-13
The drivers for my graphics card are ATI accelerated graphics driver and i also have another restricted driver of atheros hardware acess layer (hal)...hmm any idea oh how to fix that?

---

### Post by benzo8 on 2008-02-13
Download and install Envy New from here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Run Envy from your Start->System Tools and the 3rd option should be Install ATI driver - select that, let Envy do its thing, and all being well, another reboot should get you back your graphics.

---

### Post by Jennabob on 2008-02-13
hmmm right now I am running on another particition...how would I do that from a command prompt?

---

### Post by seventhc on 2008-02-13
When you get to the command promt, login then once your logged in try
```
startx
```
See if it gets you to your desktop and if not, what errors.

---

### Post by Jennabob on 2008-02-13
haha I am kicking myself right now! I had tried to fix in the xorg.conf file my system from going blank after 10 mins. Apparently that was the wrong thing to have done!
Thank you for your help it pointed me straight to what I had done wrong.

---

