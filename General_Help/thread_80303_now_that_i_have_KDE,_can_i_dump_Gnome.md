---
title: "now that i have KDE, can i dump Gnome?"
date: 2005-10-21
forum: General Help
---

### Post by fuscia on 2005-10-21
i installed breezy badger with gnome. it was slow, so i installed xubuntu from synaptic. i just installed KDE, to see what it's like and i find it to be yummy good. so, can i just use synaptic to dump gnome? anything i should watch out for?

---

### Post by Tiede on 2005-10-21
it's not going to be as easy as just deselecting ubuntu-desktop from synaptic, but it shouldn't be to hard neither. I think you have to search for files that depends on GTK Gnome libraries in synaptic... Can someone confirm this?

-- I removed KDE that way, by searching mostly for the files that begins with a K and the ones that have KDE in the description... But I don't know if it is the same for gnome :/

---

### Post by kairu0 on 2005-10-21
You can remove ubuntu-desktop, but its just a metapackage, so you'll be left with all the individual files to uninstall.

I recommend doing the categorical view in Synaptic and then removing whatever you need to from the Gnome categories. Then, do a search for "gnome" to remove libraries and whatnot thats left over.

Apply all of that and then use deborphan to kill the straglers.

---

### Post by Sirin on 2005-10-22
[QUOTE=kairu0]You can remove ubuntu-desktop, but its just a metapackage, so you'll be left with all the individual files to uninstall.

I recommend doing the categorical view in Synaptic and then removing whatever you need to from the Gnome categories. Then, do a search for "gnome" to remove libraries and whatnot thats left over.

Apply all of that and then use deborphan to kill the straglers.[/QUOTE]

Then install Kynaptic so you can ditch Synaptic. Kynaptic was built for KDE, so it performs better (when using KDE) and doesn't depend on any GTK+ engines, so it won't look crappy when you use it. :D

---

### Post by Stereotypical Rage on 2005-10-22
Kynaptic blows monkey nuts. Synaptic on the other hand rocks. It's so much more powerful.

---

### Post by aysiu on 2005-10-22
[QUOTE=Stereotypical Rage]Kynaptic blows monkey nuts. Synaptic on the other hand rocks. It's so much more powerful.[/QUOTE] Adept isn't too bad.

---

### Post by fuscia on 2005-10-22
[QUOTE=Stereotypical Rage]Kynaptic blows monkey nuts. Synaptic on the other hand rocks. It's so much more powerful.[/QUOTE]

how nice for the monkey.

---

### Post by fuscia on 2005-10-23
OOPS! that was a bad idea. had to reinstall (i don't know. don't ask). at least i cleared up all the stuff i f***ed up this past week.

---

### Post by Tiede on 2005-10-23
Sorry about your mishap fuscia. We're here to help if ever you need us :)

OK, now for *my* big question:
Here is the scenario. If I am in hoary (with pretty-powerful-gnome installed :D) and wish to change to breezy when I upgrade to breezy. Does deselecting the meta-package ubuntu-dektop and selecting the one kubuntu-desktop instead before doing the dist-upgrade will efficiently change it for me (I mean wipe out Gnome and replace it with pretty-darn-good-looking-KDE) or do I still have to go about taking out every last piece of gnome in synaptic?

---

### Post by shinygerbil on 2005-10-23
Not too sure, but I don't think so :/ As far as I know, metapackages can be safely removed without damaging dependencies, which presumably means that they aren't needed to tell synaptic/kynaptic/adept/apt-get/**aptitude**(:cool:) what packages to keep/upgrade etc.

Someone more knowledgable, correct me if I am wrong!

steve

(PS: Command-line package managers are the way forward :P If you have to use Synaptic, install gtk2-engines-gtk-qt!)

---

### Post by fuscia on 2005-10-23
[QUOTE=Tiede]Sorry about your mishap fuscia. We're here to help if ever you need us :)[/quote]

no mishap, really. my computer is a toy for me, so it provided much entertaiment. when i was using windows, i had always hoped to get some kind of virus, just to see what it was like. 

it's a pleasant surprise to  find so many helpful people on the internet.

> OK, now for *my* big question:
Here is the scenario. If I am in hoary (with pretty-powerful-gnome installed :D) and wish to change to breezy when I upgrade to breezy. Does deselecting the meta-package ubuntu-dektop and selecting the one kubuntu-desktop instead before doing the dist-upgrade will efficiently change it for me (I mean wipe out Gnome and replace it with pretty-darn-good-looking-KDE) or do I still have to go about taking out every last piece of gnome in synaptic?

i hope you weren't asking me that.  this is me reading that question...

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxdeer.jpg[/IMG]

---

### Post by Ulrik on 2005-10-23
Tiede, i'm pretty sure having kubuntu-desktop installed rather than ubuntu-desktop will give you a configuration similar to a standard Kubuntu install. It will still upgrade any installed Gnome packages, though. Which is good, if you ask me. I had both meta packages installed, which gave me an odd mixture of Ubuntu and Kubuntu. Can't recommend that.

---

