---
title: "Accidentally uninstalled a bunch of stuff"
date: 2007-03-08
forum: General Help
---

### Post by tpdasf on 2007-03-08
So I have Edgy installed and was trying to get .ape files to get recognized in k3d, and long story short I was having troubles with package dependencies and followed a few suggestions posted by other users.

As per this thread: [http://ubuntuforums.org/showthread.php?t=120775&highlight=kdelibs4-dev+unmet+dependencies](http://ubuntuforums.org/showthread.php?t=120775&highlight=kdelibs4-dev+unmet+dependencies)

I used the command: apt-get remove libgamin0

And now a lot of my applications are gone. When I logged onto my computer, it started KDE instead of Gnome (which I had as default before). (plus it didn't fix my problem with the dependencies...)

On the good side, my computer is running very fast and I'm not having that problem with lag I was having before, but I would like my applications back. (terminal doesn't work either)

Is there any easy way of doing this?

Thanks

---

### Post by watson540 on 2007-03-08
apt-get -f install
apt-get install ubuntu-desktop

---

### Post by tpdasf on 2007-03-08
Well that did it, thanks.
gotta figure out the dependency problem now...

---

### Post by watson540 on 2007-03-08
your welcome. you need to enable all the repos for apt and maybe you wont have dep. problems. use synaptic go in and edit the repos in there, make sure you check to enable universe and multiverse. just click every check box under repos then hit the reload button

---

