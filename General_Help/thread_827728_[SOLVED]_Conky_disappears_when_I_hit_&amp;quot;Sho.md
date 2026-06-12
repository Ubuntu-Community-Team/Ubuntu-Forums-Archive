---
title: "[SOLVED] Conky disappears when I hit &amp;quot;Show Desktop&amp;quot; button"
date: 2008-06-13
forum: General Help
---

### Post by laffinet on 2008-06-13
Howdy !

How do I keep Conky from disappearing when I hit the "Show desktop" button ?

Cheers,

laffinet

---

### Post by bthoward on 2008-06-13
Can you post your .conkyrc?  You do have conky setup to be part of the desktop right?  Sorry for asking the stupid questions but I can't tell you how many times the is it plugged in question has helped me with stuff. :)  

I don't normally use a show desktop button I use the compiz scale plugin but I just added a show desktop button to my panel to run a test for ya and it seems to be working as it should on my system in Hardy (8.04) using the conky from the repos.

---

### Post by easybake on 2008-06-13
add this above TEXT

own_window_type override

---

### Post by laffinet on 2008-06-13
I didn't :(

Now I do :)

And now it works :cool:

Thanks :D

---

### Post by marko_4454 on 2009-01-24
> **easybake said:**
> add this above TEXT

own_window_type override

thanks easybake, worked great!

---

### Post by TSWMIN85 on 2009-06-26
Hi, I'm having this same problem with the desktop button.

I installed Compiz, and have 4 desktops running with Desktop Cube.

It's my first day running Ubuntu, I love it!

So, how do I do the fix. In lamest terms for a first time user.

Thanks in advance!

---

### Post by VCoolio on 2009-06-26
You can change things in the config file for conky. If you don't know where it is, it is .conkyrc, a hidden file in your home folder (press ctrl+h in nautilus to show hidden files). Or if your conky is so fresh that even that one doesn't exist yet create it with running in a terminal
```
conky -C > ~/.conkyrc
```
Open the file in a text editor and find the line starting with own_window_type and change what follows to normal, or override, find out what works best for you . (other options are desktop and, with the newest conky, widget). Everything above TEXT is configuration, everything below it is what is actually shown on your desktop.

For the issue of conky disappearing on 'show desktop' button go to system > preferences > compiz config settings manager > general options find the check box for "hide skip taskbar windows" and make sure it is unchecked.

---

### Post by AintJoe on 2009-07-12
> **VCoolio said:**
> For the issue of conky disappearing on 'show desktop' button go to system > preferences > compiz config settings manager > general options find the check box for "hide skip taskbar windows" and make sure it is unchecked.

Finally, that worked for me. Everyone kept telling me to use override, but that would cause conky to flicker. Thanks.

---

