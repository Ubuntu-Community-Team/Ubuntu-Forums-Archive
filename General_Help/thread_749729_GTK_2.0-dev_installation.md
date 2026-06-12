---
title: "GTK 2.0-dev installation"
date: 2008-04-08
forum: General Help
---

### Post by SlalomMan on 2008-04-08
I've had this problem with installing this package as well as many others. When I type in "sudo aptitude install libgtk2.0-dev", it asks me to remove various packages, including ubuntu-desktop. Also, it wants me to downgrade compiz. Should I be using apt-get to install this? Or synaptic? (i'm trying to get the hang of the terminal here)

EDIT: Okay, so it turns out that, by going into synaptic, libpango was the problem. I needed to have libpango-dev installed. However, it won't install, telling me that 
"Depends: libpango1.0-0 (=1.18.2-0ubuntu1) but 1.18.3-0ubuntu1 is to be installed"

What does this mean? I'm really new to this kind of stuff...or at least kind of new.

I've now messed around with this stuff...and downgrading libpango1.0-0 to 1.18.2-0ubuntu1 would require me to remove multiple packages, including compiz, avant window navigator, and ubuntu-desktop.

---

