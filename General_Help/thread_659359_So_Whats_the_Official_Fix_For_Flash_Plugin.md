---
title: "So Whats the Official Fix For Flash Plugin?"
date: 2008-01-05
forum: General Help
---

### Post by CarlosinFL on 2008-01-05
I can see from a basic search there are a few suggestions to resolve the Flash plugin problem in 7.10 however there are just that ... too many suggestions. 

I have already received the bar on Firefox that indicates I am missing the Flash plugin so I selected to auto install option which did not produce any errors however I still can't view Youtube or any page that requires Flash plugin. I then try and install it again via the bar that appears above my browser and am already advised that it has been installed.

What do I do?

---

### Post by NilsE on 2008-01-05
My opinion is that the fix outlined in the attached link is the best and easiest way to go.

First completely remove flashplugin via Synaptic and install the deb file (download and install with gdebi) in the blue area of the first post.  Make sure Firefox is closed.

[http://ubuntuforums.org/showthread.php?t=636397&highlight=flashplugin](http://ubuntuforums.org/showthread.php?t=636397&highlight=flashplugin)

---

### Post by CarlosinFL on 2008-01-05
I have never used Synaptic - is it easier to remove it from APT-GET or CLI? I simply just don't know what the package is called to remove.

---

### Post by carrett on 2008-01-05
In the terminal:

```
sudo aptitude purge flashplugin-nonfree
```
In synaptic, well, it's harder to explain but supposedly more intuitive.

---

### Post by SOULRiDER on 2008-01-05
From IRC:
> **The Flash plugin installation is currently broken. This is due to Adobe changing the tar file that the package downloads. See [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397) if you need to fix this immediately, but it's recommended to wait for an official fix.**

---

