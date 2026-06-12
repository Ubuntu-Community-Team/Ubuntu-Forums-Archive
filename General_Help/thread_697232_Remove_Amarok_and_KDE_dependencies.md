---
title: "Remove Amarok and KDE dependencies"
date: 2008-02-14
forum: General Help
---

### Post by Chessmaster on 2008-02-14
Hey all,

I had Amarok installed but I found it would stall etc in Gnome. So, I removed it via Synaptic and I am now using Exaile which I am happy with. All good. 

But, Update Manager wants to download lots of KDE packages / updates etc. I am assuming this is because I only removed Amarok in synaptic, and did not remove the KDE dependencies. 

How do I go about removing the KDE stuff etc so I don't get any more KDE updates etc..

Thanks in advance.

---

### Post by Zeroangel on 2008-02-14
If you don't get a better response than this one -- just open Synaptic, do a search for 'KDE', sort by installed packages and remove some of what you see including kdelibs. If removing the package is gonna take down anything with it, synaptic will warn ya.

---

### Post by farruinn on 2008-02-14
You have a couple of options. If you use aptitude at the command line, then it marks packages as either manually or automatically (the dependencies) installed. When you then do aptitude remove [package] it will also remove the package's dependencies (as long as they aren't required for other packages).

Now, I'm not sure if that will work if you didn't install Amarok with aptitude and especially now that you've already removed Amarok. You could probably do 'aptitude install amarok' then 'aptitude remove amarok' and be set, but that's clunky, so...

You can use deborphan or gtkorphan to find packages that are no longer needed by any other packages.

---

