---
title: "Few errors always poppingup whenever I use the packages manager..."
date: 2005-10-08
forum: General Help
---

### Post by zoobooboozoo on 2005-10-08
```
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

```

thx in advance for the help

---

### Post by darkmatter on 2005-10-08
The Backports have been removed from mirrormax, so the error is the result of trying to connect to a non-existant repository. 

Only hoary-extras is still hosted there.

You will need to replace the mirrormax references in /etc/apt/sources.list to reflect the changes

The new reference to backports should be
```
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
```

After you have made the change in sources.list, run
```
sudo apt-get update
```
from a terminal.

The next time you run Synaptic, the errors will be gone

---

### Post by zoobooboozoo on 2005-10-11
How can I make my APT/Pmanager with lots of packs?
Like it use to have with the older address:)

---

### Post by mjhaynes on 2005-10-11
Thanks for catching this, darkmatter. I don't think they've updated the unofficial ubuntu site with the changes.

---

### Post by zoobooboozoo on 2005-10-12
How can I make my APT/Pmanager with lots of packs?
Like it use to have with the older address?

ANY other backport nonofficial yet reliable serverS?

---

