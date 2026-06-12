---
title: "How to share upgraded packages between host and guest."
date: 2012-10-21
forum: General Help
---

### Post by Wim Sturkenboom on 2012-10-21
I'm running Ubuntu 12.04 desktop as a host OS and I'm running 12.04 desktop as a guest OS in virtualbox.

Installed packages on the two are partially the same. [COLOR="Blue"]Is there a way to share the upgrades of the packages that both have in common?[/COLOR] I usually have the host up-to-date and don't like to waste bandwidth (if not necessary) by downloading the same upgrades again for the guest.

I think I found the upgrades in /var/cache/apt ([COLOR="Blue"]please confirm[/COLOR]).

[COLOR="Blue"]Which other steps are required?[/COLOR] Please note that I'm quite new to virtualbox (don't even know how to share a directory or partition on the host from the guest, if at all possible); a little lazy here, I admit. Use of command line is no problem.

---

### Post by plucky on 2012-10-21
> I think I found the upgrades in /var/cache/apt (please confirm).


/var/cache/apt/archives hold the downloaded .deb files.

You could create a shared folder on the host and move the files into the folder and the guest OS should then be able to see the files.

You can then copy the files to the Guest in the /var/cache/apt/archives location.You could also do the same for the .list files or just run ```
sudo apt-get update
``` on the guest to update the list files.

When you run the upgrade,it won't need to download the .deb files again.

Good Luck.

---

