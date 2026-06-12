---
title: "Installed fglrx driver - fglrxinfo still says 'MESA'"
date: 2008-04-28
forum: General Help
---

### Post by marcosscriven on 2008-04-28
I've tried loads of different things I've read on the forums about this, including uninstalling and reinstalling the drivers, doing 'depmod -a', restarting.

But still fglrxinfo says I am using the MESA driver, and my window scrolling/moving performance is DIRE!

Plus. having made these changes, all of a sudden the mouse pointer on my second monitor has become a large square!?!

Any help appreciated - I am tearing my hair out now.

Marcos

---

### Post by jkwarras on 2008-04-28
Are you using compiz with XGL? That was my case and I had to remove XGL and use AIGLX (don't forget to enable the composite extension in xorg.conf).

---

### Post by marcosscriven on 2008-04-28
No - just an fresh install of 7.10, no new software.

It's so amazingly frustrating!

---

### Post by marcosscriven on 2008-05-07
Any ideas please?

---

### Post by kesman on 2008-05-07
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Install the drivers with Envy, it does the trick.

---

### Post by Alekkzz on 2008-05-07
I second that. Use Envy and remove xgl.

---

