---
title: "Which Version of GIMP Should I Download From Ubuntu Software?"
date: 2018-12-13
forum: General Help
---

### Post by scribner on 2018-12-13
I just did a clean install of Ubuntu 18.04 LTS last night and already I feel like I might have messed up something. First of all, I am new to Ubuntu and not much of a computer person. My problem is I downloaded "GIMP" from Ubuntu Software because I saw it was the latest version. Right after it finished downloading I clicked "Uninstall" because I saw there were no reviews for it and the developer was snapcrafters, whom I'd never heard of. I then downloaded and installed "GNU Image Manipulation Program" from Ubuntu Software because I saw it had five stars with over 1,300 reviews. My question is, could I have messed up my computer with the first "GIMP" download, even though I never opened it and uninstalled it right away? Could anything else have downloaded along with it? I see "core," the core runtime environment in snapd is installed as an add-on in Ubuntu Software. Not sure what that is. Also, how long should it take for "GIMP" to uninstall after I click the "Uninstall" button? I believe it only took my computer a few seconds. Finally, is there any way to confirm "GIMP" is fully uninstalled? Thanks to all who can help out a newbie!

---

### Post by CatKiller on 2018-12-13
The first version you installed was a snap package, which is a new, more self-contained way of installing things. The second version you installed was a traditional package.

Either is fine.

---

### Post by deadflowr on 2018-12-13
snapcratfers are snap package developers.
snap packages are a new packaging format designed by Ubuntu.
snaps are simply single image files with all the trimmings included in them.
so removal is quick and full.


That said, the snap version should be gone now and if you want the non-snap version then when installing packages from the software store look at the Details section at what the Source says.
Anything other than Snap Store means its a traditional deb package, typically it'll say something like ubuntu-bionic-universe or main or restricted or multiverse.
(Those are the four main Ubuntu repositories for the deb packages)

---

