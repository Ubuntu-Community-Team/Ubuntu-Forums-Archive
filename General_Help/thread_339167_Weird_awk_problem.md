---
title: "Weird awk problem"
date: 2007-01-15
forum: General Help
---

### Post by bogoliubov on 2007-01-15
Hello. I have written a bash script to gather results from calculations that I've done (I'm doing a PhD in theoretical physics). 
The script works in OS X, but not in Ubuntu, and here's the reason:

OSX:
echo 0.01 | awk '{print $1*$1}'
0.0001

Ubuntu:
echo 0.01 | awk '{print $1*$1}'
0

Obviously, OS X does it correctly, but not Ubuntu.
Why does awk behave so differently? Have I done anything wrong?

---

### Post by Jussi Kukkonen on 2007-01-15
This depends on the awk you use. Dapper seems to have gawk (your example is incorrect) and Edgy has mawk (your example is correct). 

You can probably sidestep this by using mawk directly.

---

### Post by bogoliubov on 2007-01-15
Ok, thanks! Do you know any simple way of checking this, so that I can have my bash script check which version of awk is being used? I've seen configure scripts do this...

---

### Post by Jussi Kukkonen on 2007-01-15
> **bogoliubov said:**
> Ok, thanks! Do you know any simple way of checking this, so that I can have my bash script check which version of awk is being used? I've seen configure scripts do this...

Well, like I said, calling mawk instead of awk in your script is probably easiest... I don't even know which is the 'correct' result (or what yet other implementations might output) so that's also safest.

 *awk -W version* will spit some information out if you want to go that way, but there could be a more elegant method too.

---

### Post by bogoliubov on 2007-01-16
Ok, thanks for the help, I'll have a go at mawk.

---

