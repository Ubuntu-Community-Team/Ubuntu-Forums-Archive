---
title: "Downgrading wine"
date: 2007-12-15
forum: General Help
---

### Post by azurelight1337 on 2007-12-15
alland@allan-desktop:~$ winecfg
wine client error:2e: version mismatch 317/315.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?


I removed "wine" from the Synaptic Package Manager and installed 9.46 (I had 9.48)

Any help?

---

### Post by pizpot on 2008-02-08
I don't know about your error, but here is how to downgrade to the working version of wine for ubuntu:


To downgrade wine, uninstall it:

sudo apt-get remove wine

Then get wine 9.45 for ubuntu 7.04 (even though you are at 7.10 don't fret) from here:

i386:
[http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.45~winehq0~ubuntu~7.04-1_i386.deb)

Then run that, then go into Synaptic and lock the version so it does not upgrade by clicking System->Administration->Synaptic Package Mager and searching for wine, selecting "wine" in the list, and clicking Package->Lock Version

Tada, now you can join Battlenet and play warcraft3 or the war3 demo till you are blue in the face. :-)

---

### Post by stchman on 2008-02-08
> **azurelight1337 said:**
> alland@allan-desktop:~$ winecfg
wine client error:2e: version mismatch 317/315.
Your wine binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?


I removed "wine" from the Synaptic Package Manager and installed 9.46 (I had 9.48)

Any help?

You can downgrade packages via synaptic.

---

### Post by pizpot on 2008-02-08
How?

---

### Post by stchman on 2008-02-09
> **pizpot said:**
> How?

System--->Administration--->Synaptic Package Manager

Search for WINE and do a Package--->Force Version after downgrading the package you will need to lock the package version by doing a Package--->Lock Version

Don't forget to hit apply.

The downgraded package will be in the Pinned section.

---

### Post by pizpot on 2008-03-13
Update:

I went to wine headquarters:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

and on that page is this command to add their repostitory:

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

Then I clicked System->Admin->Upgrade Manager and it upgraded my wine from 9.45 to 9.56 and Battlenet works. (hint, I had to unlock wine in synaptic because I had locked)

There was a message about an authentication key, but it did not do anything. Happy gaming.

---

