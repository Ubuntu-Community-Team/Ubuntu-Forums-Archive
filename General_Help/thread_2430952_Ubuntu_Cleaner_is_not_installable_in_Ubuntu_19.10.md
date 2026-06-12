---
title: "Ubuntu Cleaner is not installable in Ubuntu 19.10"
date: 2019-11-09
forum: General Help
---

### Post by antarex882 on 2019-11-09
Is there a solution to this irritating issue :-)?
I noticed that the system cleaner I have been using - Ubuntu Cleaner - is not installable in Ubuntu 19.10.
Probably because Python 2 has been removed (?).
Trying to install the tool with:
> sudo apt install ubuntu-cleaner gives the following error message:

The following packages have unmet dependencies:
 ubuntu-cleaner : Depends: python-aptdaemon but it is not installable
                  Depends: python-aptdaemon.gtk3widgets but it is not installable

python-aptdaemon is not available for Ubuntu 19.10 (python3-aptdaemon is though).

---

### Post by Tadaen_Sylvermane on 2019-11-09
There is a ppa for it but why. Linux doesn't need cleaners like Windows does. Other than the kernels the other stuff takes up so little space it almost isn't even worth the space on the drive for the app itself. And those can be removed with a simple ```
sudo apt --purge autoremove
```

Apt cache ```
sudo apt clean
```

You can write a script to run occasionally for it. Run with sudo.

```
#!/bin/bash

# clears apt cache
apt clean

# cleans old configs and kernels as well as unneeded dependencies.
# i purge all apps individually with this command like so. total cleanout.
# apt --purge autoremove $APP
# without the specific $APP it just removes everything that isn't needed.
apt --purge autoremove

# removes user thumbnails
for user in /home/* ; do
  rm -r "$user"/.cache/thumbnails
done
```

Don't need a whole app to do it. Does same thing without a whole package + dependencies minus the gui.

I wouldn't mess with the /home/"$USER" stuff though. Most people's computer habits are fairly consistent. Stuff will just get recreated again. No real point.

---

