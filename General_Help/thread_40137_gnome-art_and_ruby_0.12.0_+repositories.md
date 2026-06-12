---
title: "gnome-art and ruby 0.12.0 +repositories"
date: 2005-06-07
forum: General Help
---

### Post by gotmonkey on 2005-06-07
I have been trying to get gnome-art working. It requires ruby 0.12.0 and it's dependencies. I have found plenty of sites that have deb packages, but synaptic keeps freaking out on me.

Could somebody help with this?

thanks

---

### Post by adwait on 2005-06-07
Have you tried apt-get via the commandline? In the root terminal type apt-get install ruby.

---

### Post by gotmonkey on 2005-06-08
yeah, the repositories that I have listed in sources.lst only go up to 0.11.0 for ruby-gnome2.

---

### Post by gotmonkey on 2005-06-27
I found a way around my dependencies. I added the breezy repositories to my source, grabbed the files required for the program, and disabled them afterwards. Worked like a charm

---

