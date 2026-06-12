---
title: "Remove Evolution?"
date: 2005-03-23
forum: General Help
---

### Post by dtokeefe on 2005-03-23
Hi,

I would like to remove Evolution from my system to conserve memory, but I am worried about the consequences. Specifically, Package Manager says that I must also remove Ubuntu Desktop (which I like) when I remove Evolution. Does this mean I cannot have the one without the other?

Also, is there another solution? Some optimizing solution that allows me to simultaneously run Evolution plus OpenOffice plus Firefox plus a few other apps without running out memory (Athlon XP 1.6 mhz with 256 MB RAM, 32 MB video offboard)? 

Thanks in advance.

David

---

### Post by chz on 2005-03-25
[QUOTE=dtokeefe]Hi,

I would like to remove Evolution from my system to conserve memory, but I am worried about the consequences. Specifically, Package Manager says that I must also remove Ubuntu Desktop (which I like) when I remove Evolution. Does this mean I cannot have the one without the other?

Also, is there another solution? Some optimizing solution that allows me to simultaneously run Evolution plus OpenOffice plus Firefox plus a few other apps without running out memory (Athlon XP 1.6 mhz with 256 MB RAM, 32 MB video offboard)? 

Thanks in advance.

David[/QUOTE]
 I regretfully uninstalled evolution, and suffered major consequences...it made the OS nonbootable, and from reformatting back to the original, somehow ended up frying the partition i was using for ubuntu, the rest of the harddrive for some reason is still intact (it may have been from other causes, but what an odd coincidence ey?). So i suggest you not touch evolution, seems we are stuck with this program even if we dont want it, unless somebody does have a clean method of removing it.
Your processor seems fine, and i'm running a 32mb video card as well with no problems, but runnin OO.org is one hefty chunk of memory. Firefox can start off with a small amount, but i've experienced it saturating the rest of my ram after browsing for a little while (probably depends on what you are surfing). And i'm pretty sure Evolution may take up some ram as well, so even though its a nasty suggestion, but probably increasing your ram would be your best bet.

---

### Post by audax321 on 2005-03-25
Ubuntu desktop is just a meta package that depends on the other stuff that ubuntu installs. Although I would suggest reinstalling ubuntu desktop if you ever upgraded just to make sure everything got installed. I'm guessing when the upgrade occurs and ubuntu desktop is available, it will be upgraded as well and include any new packages the ubuntu distribution wants to install.

I had no use for Evolution because I use Thunderbird and didn't care for a distro packed Firefox either (I install it using the Mozilla installer). In fact, I removed OpenOffice as well. All of these depend on ubuntu desktop and I had no problems with it gone. Not sure what happened to chz, but that sucks  :-(

---

### Post by 620hun on 2008-05-25
```
aptitude search evolution
```

and ```
sudo apt-get remove
``` every stuff which has an "i" in front of it, except evolution-data-server-common

it doesn't remove any core parts of ub.:)

---

