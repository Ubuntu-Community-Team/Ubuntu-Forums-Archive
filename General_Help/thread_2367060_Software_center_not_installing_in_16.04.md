---
title: "Software center not installing in 16.04"
date: 2017-07-25
forum: General Help
---

### Post by gde061-www on 2017-07-25
My issue is trying to install through the software center, I click the button for "install", it says "installing" for a few seconds, and then the button goes back to "install" ... as the package install didn't happen.

I can install some packages from command line with apt.  Others apt seems unable to find, even though they show up in Software Center search. Example would be "Dropbox", witch software finds but won't install, and apt can't find!  (This issue remains a mystery)

Gnome-software didn't report the error, but when I tried in Ubuntu Software Center, I got: Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.82'}): org.debian.apt.install-or-remove-packages  (This issue now appears solved.  See below)

I read all about issues with the software center on initial release of 16.xx, but I would think they would be fixed by now. 
How do I fix?

---

### Post by Autodave on 2017-07-25
Install *synaptic *and use that to install your programs.  "sudo apt-get install synaptic".  If you are looking for a program, you can type the n ame of the program into the search box or you can type keywords into the search box. OR, you can find the name of the program in the software center and then go to synaptic and type it in there.

---

### Post by gde061-www on 2017-07-27
> **Autodave said:**
> Install *synaptic *and use that to install your programs.  "sudo apt-get install synaptic".  If you are looking for a program, you can type the n ame of the program into the search box or you can type keywords into the search box. OR, you can find the name of the program in the software center and then go to synaptic and type it in there.

I suppose I am in the minority, but I prefer the Ubuntu Software Center to other GUI front ends.  The Gnome "Ubuntu Software" had the same issue.

Once I got the description of the error from Ubuntu Software Center I was able to try a few things.  I started by manually adding Polkit to my startup, but that didn't work. So I deleted the ~/.config/autostart folder, which contained entries for remmina (?) and mate.  Since then the problem seems to be solved.

---

