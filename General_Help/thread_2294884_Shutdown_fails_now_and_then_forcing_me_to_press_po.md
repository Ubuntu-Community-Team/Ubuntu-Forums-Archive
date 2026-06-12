---
title: "Shutdown fails now and then forcing me to press power button"
date: 2015-09-14
forum: General Help
---

### Post by ELD on 2015-09-14
For some reason now and then Ubuntu won't shutdown, it closes all windows and removes the unity bars, but it just stays with my background and doesn't shut down.

This causes me to press and hold the power button, and each time I do this it messes up the filesystem causing me to use boot repair from a live USB.

How can I find what is causing this?

I run my OS from an SSD, and my /home on a HDD.

---

### Post by dino99 on 2015-09-14
you need to know what is happening on shutdown: glance at logs, and remove "quiet splash" from grub
if you have installed some third party packages, then back to the genuine ones
start cleaning the system: clean/autoclean/autoremove/gtkorphan
glance into /etc/rc?.d folders for possible broken links: if there is some, then erase them, the system will cleanly recreate what it needs on the next reboot

---

### Post by ELD on 2015-09-15
The problem is it doesn't actually seem to reach the shutdown stage for me to see anything, it seems like it gets stuck closing down the entire desktop, and my background is still there.

As I had it just now, but luckily reisub did work!

---

### Post by ELD on 2015-10-15
Okay, I've done the autoclean and autoremove.

How do I know what's a broken link in the /etc/rc?.d folders?

I tried doing SSH into the hung box, but it never seems to work.

---

### Post by sudodus on 2015-10-15
***SysRq R E I S U B*** is a good 'lifesaver' :-)

That way you might also be able to see which of the commands R E I ... that give a response (screen output or a noise), and which don't, so you can conclude at which stage the shutdown was interrupted.

Does it make a difference if you run ```
sync
``` before shutting down? (Sometimes it helps me to flush the buffers.)

Can you find a pattern - for example what programs or tasks you ran/performed when the shutdown did not work?

---

### Post by ELD on 2015-10-15
> **sudodus said:**
> ***SysRq R E I S U B*** is a good 'lifesaver' :-)

That way you might also be able to see which of the commands R E I ... that give a response (screen output or a noise), and which don't, so you can conclude at which stage the shutdown was interrupted.

Does it make a difference if you run ```
sync
``` before shutting down? (Sometimes it helps me to flush the buffers.)

Can you find a pattern - for example what programs or tasks you ran/performed when the shutdown did not work?

If I shut down from another session, like ctrl+alt+f1 will that show the issues? If I shutdown that way each time maybe it will tell me something?

As I do so much it's not really all that possible to find a pattern really.

---

### Post by Mithron on 2015-10-15
Tried CTRL+ALT+F1 to see the console? 
Broken links are generally blinking in modern consoles when you ls -al the folder.
It seems now that Unity(or maybe some other services) cannot fully turn off. Maybe something keeps it busy?

---

### Post by ELD on 2015-10-15
> **Mithron said:**
> Tried CTRL+ALT+F1 to see the console? 
Broken links are generally blinking in modern consoles when you ls -al the folder.
It seems now that Unity(or maybe some other services) cannot fully turn off. Maybe something keeps it busy?

I cannot switch session with CTRL+ALT+F1 when it's at the point of failing, as it seems to not take any input other than REISUB.

I've checked the links suggested, and all show up green in terminal (none broken).

---

### Post by sudodus on 2015-10-15
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

```
un[COLOR="#FF0000"]R[/COLOR]aw      (take control of keyboard back from X),
 t[COLOR="#FF0000"]E[/COLOR]rminate (send SIGTERM to all processes, allowing them to terminate gracefully),
 k[COLOR="#FF0000"]I[/COLOR]ll      (send SIGKILL to all processes, forcing them to terminate immediately),
  [COLOR="#FF0000"]S[/COLOR]ync     (flush data to disk),
  [COLOR="#FF0000"]U[/COLOR]nmount  (remount all filesystems read-only),
re[COLOR="#FF0000"]B[/COLOR]oot.
```

What I meant is that maybe you can find out at what stage of this sequence the shutdown hangs.

-o-

Did you get any information from the tips by *dino99*?

---

### Post by Mithron on 2015-10-15
Maybe you can go to console CTRL+ALT+F1 beforehand and than maybe type "shutdown -h now" there or REISUB and see the output there.

---

