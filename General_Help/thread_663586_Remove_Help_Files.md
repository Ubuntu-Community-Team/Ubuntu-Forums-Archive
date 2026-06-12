---
title: "Remove Help Files"
date: 2008-01-10
forum: General Help
---

### Post by acidtuch10 on 2008-01-10
Is it possible to remove all help files from Ubuntu. Personally I do not use them and they just consume disk space on an older computer. If so is there an easy way to remove them. 


Thanks

---

### Post by taurus on 2008-01-10
You mean the manpage!

```
sudo apt-get remove manpages
```

---

### Post by acidtuch10 on 2008-01-10
That will remove the contents of /usr/share/gnome/help/ ?


Thanks

---

### Post by taurus on 2008-01-10
You know that /usr/share/gnome/help takes up only 160MB of space.

---

### Post by acidtuch10 on 2008-01-10
160 mb on a 3 gig drive is allot :-)  its a IBM A20M that acts as a SSH and Privoxy server... I thought that stream lining it and removing all that is un-needed minus a browser and a few utilities make it run alittle better on this resource deprived laptop. Probably shoulda just installed server but its to late now and I do not wanna sit through another long install.

Already removed all games, office, multimedia etc..... Might remove all the audio things also 


Thanks

---

### Post by taurus on 2008-01-10
You can remove gnome-doc-utils.

However, if you want to have a minimal gnome window manager, why not install the server version than then install gnome-core only.  Then, only install stuff that you really need after that.

Otherwise, open synaptic and Search for gnome.  Then, remove whatever components you don't need.

---

### Post by acidtuch10 on 2008-01-10
ubuntu-docs = After unpacking 76.7MB disk space will be freed.

Seems to have worked 

thanks

---

### Post by Blario on 2008-03-23
gnome-doc-utils

Removing that worked wonders for me!  Freed up 220MB.  It uninstalled some other things in the process... including ubuntu-desktop which I am slightly worried about.  Think I will add that back solo though.

---

### Post by Blario on 2008-03-23
> **Blario said:**
> gnome-doc-utils

Removing that worked wonders for me!  Freed up 220MB.  It uninstalled some other things in the process... including ubuntu-desktop which I am slightly worried about.  Think I will add that back solo though.

From what I understand, ubuntu-desktop is a pseudo-package.... so I'm really not missing anything except for the other stuff.  Other stuff being "gnome-doc-utils gnome-user-guide ubuntu-docs yelp", which I don't need.

---

