---
title: "Process Howto: Run firefox-bin in background"
date: 2006-12-24
forum: General Help
---

### Post by mohamad on 2006-12-24
Hi,

When I start firefox, a process called 'firefox-bin' pops up in my process list. This first starting-up is very slow, but when I open another firefox window it opens very fast because the process firefox-bin is allready running.

So I tried to always have firefox-bin running in the background, even if there is no firefox window open.
Does anyone know how to do this?
"firefox &" didnt work for me

Thanks,
Mo

---

### Post by PriceChild on 2006-12-24
*Thread moved and bumped*

---

### Post by bodhi.zazen on 2006-12-24
Check out prelink:

[http://doc.gwos.org/index.php/Prelink](http://doc.gwos.org/index.php/Prelink)

This may also help with overall performance tips:

[http://doc.gwos.org/index.php/Improve_Performance_In_Ubuntu_6.06](http://doc.gwos.org/index.php/Improve_Performance_In_Ubuntu_6.06)

---

### Post by mohamad on 2006-12-24
Thanks I'll check it out and post what has been useful
greets

---

### Post by mohamad on 2006-12-24
> **bodhi.zazen said:**
> Check out prelink:

[http://doc.gwos.org/index.php/Prelink](http://doc.gwos.org/index.php/Prelink)

This may also help with overall performance tips:

[http://doc.gwos.org/index.php/Improve_Performance_In_Ubuntu_6.06](http://doc.gwos.org/index.php/Improve_Performance_In_Ubuntu_6.06)

It didnt really do the trick.
I'm still looking for something that can 'keep binary files always in RAM'. 
If this is not possible, is there maybe a way to start firefox, but without a window?
Kind of the 'screen' option in a terminal, but now for a GUI

---

### Post by casaschi on 2006-12-24
> **mohamad said:**
> It didnt really do the trick.
I'm still looking for something that can 'keep binary files always in RAM'. 
If this is not possible, is there maybe a way to start firefox, but without a window?
Kind of the 'screen' option in a terminal, but now for a GUI

Try adding "alltray firefox" to your startup program list.
This way firefox will be launched at startup, minimized in the system tray. Everytime you close firefox, it would minimize to the tray instead.

---

### Post by mohamad on 2006-12-25
Thanks!
This worked, many thnx to all and I now also use prelinking, i feel my machine working faster!

---

