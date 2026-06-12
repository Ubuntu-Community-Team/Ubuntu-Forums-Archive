---
title: "I want to boot to a prompt"
date: 2006-08-23
forum: General Help
---

### Post by charles.g.moore on 2006-08-23
I was wondering if there was a way that I could set up my system to boot to the $prompt and not start x until i told it to...

and if its possible will the system still mnt all of my stuff and run through the appropriate runlevels?

When I start up my system all i want to see is the textual login prompt at 
ctr+alt+F1

---

### Post by hw-tph on 2006-08-23
**sudo update-rc.d -f gdm remove** should do it. You can then start the graphical interface using **sudo /etc/init.d/gdm start** (will display the login window) or by just typing **startx**.


Håkan

---

