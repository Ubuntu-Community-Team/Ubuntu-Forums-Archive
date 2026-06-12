---
title: "kinfocenter not in repos?"
date: 2008-01-27
forum: General Help
---

### Post by maestrobwh1 on 2008-01-27
I "lost" kinfocenter in gutsy.  It opens but there is nothing there.  I went to reinstall it but the the only item that shows up in adept is kinfocenter-kde4.

I also googled "ubuntu packages" to get to the ubuntu package search site.  I got no hits for "kinfocenter" except for the kde4 variant.  I did an overall package search for all distros. 

I did a more broad search of descriptions and got it as part of kcontrol so I reinstalled it but it looks the same.  It is also empty like kinfocenter now.  It used to work because systemsettings did not: it crashes.  Systemsettings can be launched as root.

I purged kcontrol and it took with it kdebase and several other packages.  I ran gtkorphan to get rid of residual configuration files, but when I reinstalled all of these things, I still have the same issue.

So now I have no access to personal configuration.

Help?

---

### Post by kuja on 2008-01-27
One thing worth trying is to create a new user and see if kcontrol + kinfocenter are "working" for the new user ..... if so the easiest "solution" would be to copy over your iles less any config files you can afford to lose to the new user and delete the original, delete the original home, delete the original user, recreate the original user, and copy back.

---

