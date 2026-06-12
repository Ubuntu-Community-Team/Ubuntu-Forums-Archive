---
title: "Cannot disable login/logout sounds?"
date: 2007-04-19
forum: General Help
---

### Post by ember on 2007-04-19
I have a strange problem, now that I have just installed Feisty anew:

Even if I disable all sounds both for root and my local account, I still have this login sound (drums). Does anybody know whether I need to edit some config file to get rid of this sound?

Best,
ember

---

### Post by bwhite82 on 2007-04-19
It would be wise to install the package "gconf-editor" for this kind of stuff. Then once it's installed, you run it from the command line "sudo gconf-editor", it will open a gui with tons of options for your desktop. It's pretty straightforward from there, you'll have to dig around until you find something that says "gdm" and you'll have to find the sound option and disable it.

There is a config file for this but I cannot remember it off-hand at this time.

---

### Post by x64Jimbo on 2007-04-19
It's in a different part of the configurations. 
In System > Administration > Login Window on the Accessibility tab, you can un-check the sounds. That should fix it.

---

### Post by bwhite82 on 2007-04-19
> **x64Jimbo said:**
> It's in a different part of the configurations. 
In System > Administration > Login Window on the Accessibility tab, you can un-check the sounds. That should fix it.

Or that too. :)

---

### Post by ember on 2007-04-19
Thanks for the hint - that's it.

btw: I already have installed gconf-editor. I'm just a bit reluctant to search all options at quarter to four in the night ;)

---

