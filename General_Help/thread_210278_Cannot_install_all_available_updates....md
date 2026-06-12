---
title: "Cannot install all available updates..."
date: 2006-07-06
forum: General Help
---

### Post by Culito on 2006-07-06
I'm getting this message through the Update Manager:

Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely.
The following updates will be skipped:
gnome-cups-manager
python-netcdf

Synaptic marks nothing, and dist-upgrade gives me this: 

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gnome-cups-manager python-netcdf
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

What's the story here?

---

### Post by golfbuf on 2006-07-06
Wait another day for the rest of the package dependencies to make it into the repos.

HTH

---

### Post by Culito on 2006-07-07
Actually, It's been doing this for months, and the updates icon keeps poppin' up.

---

### Post by avtolle on 2006-07-07
I had the same issue for about 6 weeks; then, last week, the held back package (not the same one(s)) was miraculously installed along with some other updates. This fact took me a few days to note, as I had become accustomed to the message. So, if patience is a virtue, be virtuous. :mrgreen:

---

