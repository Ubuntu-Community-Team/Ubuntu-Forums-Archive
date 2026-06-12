---
title: "Installing .deb for squeak on hoary"
date: 2005-08-12
forum: General Help
---

### Post by Nasir Amra on 2005-08-12
I've used synaptic to check if the smalltalk language called squeak is available , and it is not ( see [http://www.squeakland.org/)](http://www.squeakland.org/)). However, there are .deb packages available at the above website so I was wondering if installing these in ubuntu would be o.kay. I would also be interested in making ubuntu compatible .debs if someone can point to some tutorial or guideline on how to convert .deb files to fit the ubuntu distributions.
Thanks,

---

### Post by mcmuffy on 2005-08-12
I can't speak for every .deb out there but the ones that I have downloaded from websites on installed with dpkg have all worked fine.

---

### Post by mird on 2005-08-12
As mcmuffy pointed out, you can install deb packages using the [font=fixed]dpkg[/font] utility.  To do so open up a terminal window and type: ```
sudo dpkg -i yourdebfilename.deb
```
You may have problems installing the squeak packages however since they will probably complain about unresolved dependancies.  You might be in luck tho because it looks there are squeak packages in the breezy repository, so you can put in a request to the backports team and it might appear in the hoary backports repository.

Otherwise you will have to attempt to build your own package.  It's not entirely simple, but that is to say it's not entirely difficult either.  There is a pretty good explanation of the process in [this thread](http://ubuntuforums.org/showthread.php?t=51003) if you're interested.

---

