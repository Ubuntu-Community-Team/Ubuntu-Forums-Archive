---
title: "Nautilus and other packages showing up as &quot;local or obsolete&quot;"
date: 2008-05-03
forum: General Help
---

### Post by akshaydua on 2008-05-03
I am seeing important packages like nautilus, evolution and update-manager in the local or obsolete section of synaptic. Anyone know why that's happened? Is ubuntu not supporting those packages anymore, they don't seem to belong to a repository at all? Can I remove them?

---

### Post by RATM_Owns on 2008-05-03
Try this:

sudo apt-get update
sudo apt-get upgrade

I don't really know what else would work.
But don't remove Nautilus.

---

### Post by chrisccoulson on 2008-05-03
Packages will appear as 'local or obsolete' if they do not reside in any of the currently specified repositories. This can be because:
[LIST]
[*]The package was installed from a stand-alone deb package
[*]The package has been removed from the repositories
[*]The repository that the package was installed from is no longer specified as a software source (you removed it from sources.list)
[/LIST]

You definately shouldn't remove the packages you mentioned

First of all, please open 'Software Sources' and make sure 'main' is selected. Also bear in mind that some mirrors are still running slow, and give mixed results. Try selecting another mirror.

You could also post the contents of your /etc/apt/sources.list file, as this may help

---

