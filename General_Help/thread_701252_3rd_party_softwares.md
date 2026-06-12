---
title: "3rd party softwares"
date: 2008-02-19
forum: General Help
---

### Post by chathurangamdk on 2008-02-19
I'm a new face to ubuntu.i'm using 7.10. so if this is a foolish question, just ignore it.

i want to get install some softwares into my laptop. from where can i get some apt line which provide newest softwares. at the same time i want to install a website grabber. what are the available grabbers.

Thanx a lot.

---

### Post by p_quarles on 2008-02-19
What software are you trying to install? The best method really depends on the specific application.

As for web scrapers/grabbers, the most effective tools are for the command line: wget and curl.

---

### Post by Littleweseth on 2008-02-19
As far as 'apt lines' go, use Synaptic (comes with Ubuntu) or Adept (comes with Kubuntu) - these are the graphical frontends to the apt package manager. If you want a commandline frontend to apt, use aptitude - it's quite nice, considering it's a text-interface app.

To get 'newest software', enable the 'universe', 'multiverse' and 'restricted' repositories (in synaptic or adept) and then update your package lists - your computer will now be aware of the latest software available from the Ubuntu package mirrors.

Website grabbers : as mentioned above, wget is the king of all recursive downloaders, and there are graphical frontends for it as well (so you don't have to get your hands dirty.) Search the keyword 'wget' in synaptic for a list of frontends to wget.

HTH;
-lws

---

