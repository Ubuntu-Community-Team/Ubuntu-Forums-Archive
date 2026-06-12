---
title: "xerox printer (details)"
date: 2006-12-11
forum: General Help
---

### Post by dbbolton on 2006-12-11
ever read the great gatsby ?

i'm trying to install a Xerox Workcentre XK50CX on xubuntu 6.06 (i also installed the ubuntu-desktop package, gnome-cups-manager, and so on)

the computer detects the printer and gcm recommends the lex5700 driver (the xk50cx isn't on the list; it selects this driver for a xk35c)

however, linuxprinting.org states:

> **Section 3: Xerox WorkCenter XK50cx**

        
3.1 _How do I set it up?_                    Setting it up as a Lexmark GDI inkprinter with           Ghostscript "stp" driver.           gs -DIVICE=stp -sMODEL=lexmark-z52            
       3.2 _How well are the options supported?_                    All resolutions and quality parameter are available.           It is important to use the Lexmark Z52 model. Other           models aren't compatible to higher resolutions ober 600x600
i added a new printer as a lexmark z52 with the gutenprint driver, and under "connection" i chose "use another printer by specifying port", which is usb #1.

neither of these worked. with the lex5700 driver, the printer makes noises like it's printing but ultimately shoots out a blank page. with the gutenprint driver, it just spits out a blank page.

what exactly is "gs -DIVICE=stp -sMODEL=lexmark-z52"? when i run it in a terminal as sudo or not, i get this error:

-dvar=name requires name=null, true, or false


so, i tried "gs -DIVICE=stp -sMODEL=lexmark-z52 -dvar=null" but got the same error. same with true or false.

this is my friend's computer, so it really doesn't matter to me. but i would certainly like to help him and we would both appreciate your help.

---

### Post by dbbolton on 2006-12-11
please ?

---

### Post by dbbolton on 2006-12-11
is this even in the right thread

---

### Post by freebeer on 2006-12-11
This section **should** be ok, but you might want to try the Hardware forum.

Sorry, but I can't help you - my Xerox printer has a linux driver.  I see that your particular unit doesn't have one.  (I checked on Xerox's website.)

You might also want to do a search on these forums for "xerox printer".  I know I've seen a few threads on them, and I'm pretty sure one dealt with a WorkCentre (maybe not the same model, though).

---

### Post by dbbolton on 2006-12-11
thanks, freebeer.

>>>started another thread regarding the little ghostscript problem:

[http://www.ubuntuforums.org/showthread.php?t=317125](http://www.ubuntuforums.org/showthread.php?t=317125)

---

### Post by dbbolton on 2006-12-12
still no printing.

---

### Post by dbbolton on 2006-12-12
it would seriously be nice if more than one person took the time to respond.

---

### Post by dbbolton on 2006-12-12
hey taurus- it's pretty sad that i posted the same thread four times and still didn't get a single legitimate response.

---

### Post by hod139 on 2006-12-12
Here's another driver [you can try]("http://lists.freestandards.org/pipermail/printing-user-xerox/2004/000311.html"):

(Debian GNU/Linux) 
- CUPS 
- hpijs + foomatic 
 
Driver that is uses was "HP Laserjet 4 + foomatic" !

---

### Post by freebeer on 2006-12-14
> **dbbolton said:**
> thanks, freebeer.

>>>started another thread regarding the little ghostscript problem:



Still no luck, eh?  I'm still a noob with linux, so I'm sorry that I can't be of much help.  Here's an idea that you might want to persue (if you haven't already).  I would imagine (haven't checked) that your printer supports Postscript?  I know my Xerox does, so I was thinking that if I couldn't get the Xerox driver to work, I'd next try a generic Postcript driver.

---

### Post by dbbolton on 2006-12-14
yeah, i am totally lost when it comes to hardware

but the postscript idea sounjds viable. i'm going to give it a shot.

an ubuntu extra shot

---

