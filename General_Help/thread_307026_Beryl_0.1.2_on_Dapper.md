---
title: "Beryl 0.1.2 on Dapper"
date: 2006-11-25
forum: General Help
---

### Post by shanepardue on 2006-11-25
Has anyone gotten the latest stable Beryl (0.1.2) to run on Dapper? I was 
wondering what what new additions were added and how I would upgrade
 if I decided to?

Thanks

---

### Post by Monkey358 on 2006-11-26
I did it by using Trevinos repository only and letting the update-manager update the package to the SVN builds. It's been hit or miss stability though, and just for a few new effects as far as I can tell, so it's probably smarter to hang back.

---

### Post by shanepardue on 2006-11-26
What new effects? I'm an effects junkie!

Also, what has the misses on stability resulted in? I know now my Beryl 
will flicker and run the cpu at 100% from time to time, but there's an 
easy workaround. Please fill me in! Thanks!

---

### Post by steveneddy on 2006-11-26
> **shanepardue said:**
> What new effects? I'm an effects junkie!

Also, what has the misses on stability resulted in? I know now my Beryl 
will flicker and run the cpu at 100% from time to time, but there's an 
easy workaround. Please fill me in! Thanks!

What is the work around for the 100% CPU usage bug? Sometimes I have that problem, but not often, but when I do have the problem it annoys me. Please post the answer to this query.

---

### Post by shanepardue on 2006-11-26
I just exit Beryl-manager and it fixes the problem while my beryl graphics remain intact.

---

### Post by cmost on 2006-11-26
I never start Beryl-manager.  I find that it causes the CPU bug as well as flickery shadows on occasion.  To solve these problems, I have two scripts that I run at startup; they're timed so that one runs after a 10 second pause and the other runs after a 15 second pause (so that they start in the right order.)

Script #1:
#!/bin/bash
# Destroy any instances of Beryl & emerald
# Start Beryl effects only
killall beryl
killall beryl-xgl
killall beryl-manager
killall emerald
sleep 10s
beryl-xgl

Script #2:
#!/bin/bash
# Start the Emerald window decorator only
killall emerald
sleep 15s
emerald

Place these scripts in your startup group in Gnome Sessions manager and you'll be good to go.  You can still change Bery'd settings by going to Beryl Settings Manager under Gnome Menu --> Preferences.  The same for Emerald.

---

