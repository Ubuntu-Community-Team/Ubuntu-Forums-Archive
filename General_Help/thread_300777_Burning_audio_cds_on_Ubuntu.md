---
title: "Burning audio cds on Ubuntu"
date: 2006-11-16
forum: General Help
---

### Post by Gargamella on 2006-11-16
Is it possible to burn an audio cd with K3b or Gnome baker from mp3s?

I tried with both,K3b doesn't want to burn mp3s for audio cds,Gnome baker starts the process but it fails without doing nothing to the cd.

Any idea?

---

### Post by dragomirov on 2006-11-16
I usually do it with k3b. Are you sure every k3b is installed? Check with synaptic (do a search "k3b" with both description and name).

You need libk3b2-mp3 I think....

---

### Post by strabes on 2006-11-16
yeah the reason it's failing is because you probably don't have the correct mp3 libraries. Not sure if this will help but check out [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[edit] i found this on the restricted formats page...

sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.8-mad gstreamer0.8-misc

you should probably just go ahead and install all the stuff on that page so you won't have media problems again

---

### Post by Nameless_one on 2006-11-16
Have you tried serpentine? It comes with the standard ubuntu installation (with dapper at least).

---

### Post by Gargamella on 2006-11-16
gonna try i will answer then

---

