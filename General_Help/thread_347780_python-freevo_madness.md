---
title: "python-freevo madness"
date: 2007-01-27
forum: General Help
---

### Post by Placenta Juan on 2007-01-27
So, there was an update to freevo earlier today, I think from ubuntu.geole.info, and as soon as I installed it, it gave me an error about python-freevo not updating correctly. I tried fixing broken packages, reinstalling, and uninstalling python-freevo, but nothing works. I get the following error (which shows up anytime I use apt-get also):
```
Removing python-freevo ...
usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f]

update-python-modules: error: /usr/share/python-support/python-freevo does not exist
dpkg: error processing python-freevo (--remove):
 subprocess pre-removal script returned error exit status 2
postinst called with unknown argument `abort-remove'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-freevo
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Seems like python-freevo doesn't exist, and yet it shows up in Synaptic as being installed. I have no clue what's going on. Anyone have any ideas?

---

### Post by big_gie on 2007-01-30
I'm having the exact same problem...

---

### Post by rvdb on 2007-01-30
i had the same problem. somewhere on the web (forgot where) i found

sudo rm /var/lib/dpkg/info/python-freevo.*
sudo apt-get -f install

for me this works, but i really don't know why and whether i have not introduced other errors (i just was so frustrated with the whole thing... i just tried).

Now i can install and remove packages again.

Bu now apt-get is 'complaining' everytime that there are a lot of packages that are autoremovable (but i have read all warnings not to do so...)

regards
Rein

---

### Post by Placenta Juan on 2007-01-30
That seemed to work, I was able to uninstall python-freevo and then reinstall it. Now Freevo is working correctly.
I'm not getting any apt-get complaints, I'm under the impression that autoremove cleans up unneeded dependencies, so maybe you have some leftover "orphaned" libs related to freevo? I don't think there would be any problems playing it safe and keeping them, though.

---

### Post by big_gie on 2007-01-31
Thanx rvdb that did the trick.

---

