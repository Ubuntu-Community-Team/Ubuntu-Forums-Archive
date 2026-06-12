---
title: "Can someone explain this to me?"
date: 2007-07-04
forum: General Help
---

### Post by ardchoille42 on 2007-07-04
I always install apps from the repos and never compile. I have seen a lot of knowledgeable people advise to never install .deb packages that were made for other distros. I follow this advice but I would like to know why this is good advice? What exactly are the dangers with installing other distros' .deb packages in Ubuntu? Does it have to do with different versions of libs in the .deb packages? Different paths of libs?

I'm just trying to better understand how the Ubuntu packaging system works and feel better about passing this advice on to others.

Can someone shed some light on this please?

---

### Post by moore.bryan on 2007-07-04
*as i've found in the past, if you take a deb from debian--for example--and try to install it onto an ubuntu system, there may be a number of dependencies which don't work-out.  happened to me when i tried to install the newest iceweasel... needed to download a bunch of dependent debs from debian's unstable repo and i might eventually run into some problem.*

---

### Post by RedSquirrel on 2007-07-04
I've heard that sometimes the package names are slightly different as well so that could cause some dependency problems.

I feel more comfortable compiling than using either "foreign" debs or rpms with alien, but that's just me.

---

### Post by moore.bryan on 2007-07-04
*yeah... iceweasel was a pain in the a s s to get up and running, but is wonderful now.  sometimes i ask myself why i didn't just do a plain debian server install with openbox.  maybe next time.*

---

