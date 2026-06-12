---
title: "Open Office ICONS"
date: 2007-11-26
forum: General Help
---

### Post by x2fast on 2007-11-26
I just downloaded and installed open office

I already had some parts installed by default...(running Gutsy Gibbon)

I wanted the other programs available and the ability to automatically get updates so I downloaded the RPM's from openoffice.org....
then I installed.....

fakeroot alien -i *.rpm    blah blah blah you know the rest
dpkg yada yada yada

Everything works fine but my new openoffice install is not under "Applications > Office"  I can still run everything from command line....ex oowriter oomath, etc.

I want it in my menu, and also be able to see the shiny new icons.  My life would no longer be a downwards spiral.

---

### Post by x2fast on 2007-11-26
Well...I know how to add new items to the Menu...I just can't locate the new Icons for OpenOffice?  Not in pixmaps?

---

### Post by PeterJS on 2007-11-26
> **x2fast said:**
> 
I wanted the other programs available and the ability to automatically get updates so I downloaded the RPM's from openoffice.org....


This doesn't make any sense, if you wanted it to automatically get updates then why did you go outside the package manager? That's one of the nice things about package management is that it does auto-update for every thing.

If you really want to go the rpm + home brew menu route you can find all the icons by running:
```

locate ooo | grep png

```

---

### Post by Perfect Storm on 2007-11-26
> Everything works fine but my new openoffice install is not under "Applications > Office" I can still run everything from command line....ex oowriter oomath, etc.

Easy just make the shortcuts (the command to execute) in alacarte.

---

