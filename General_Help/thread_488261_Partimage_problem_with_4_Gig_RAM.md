---
title: "Partimage problem with 4 Gig RAM?"
date: 2007-06-30
forum: General Help
---

### Post by elfstone214 on 2007-06-30
I am having a very weird problem with partimage ever since I upgraded to 4gig RAM. Whenever I try to restore an old image it tells me the "compression level is not correct" or "segmentation fault"? I have no problem creating the image but it will not let me restore images even those which I created before upgrading my RAM. This is really starting to tick me off

Does anyone have any idea what could be the problem? I have tried partimage from the Ubuntu live-cd and by using System Recovery live-cd. I have the same problem in both cases.

---

### Post by swisscow on 2007-06-30
I am by no means an expert on this but I read somewhere (can't remember) that some PCs can't handle 4 GB or more of RAM - it does strange things. Whether this is true or not I don't know. But it does lead me to thinking you could:


1) reduce the RAM to less than 4GB and then see if that makes a difference

or

2) perhaps some of the RAM is bad - memtest (I know it's on the livecd boot screen) might help with this.

Anyway, this may all be complete rubbish and of no help to you but on the other hand..

I wish you all the best

---

### Post by elfstone214 on 2007-06-30
Thanks swisscow

my RAM actually works OK in the physical sense. I am running amd64 ubuntu which can handle 4gig fine and all 4gig show up in system resources. I have also run memtest86+ successfully with no errors.

I think partimage itself is just not liking seeing 4gig, dunno maybe it is just a coincidence that I just installed 4gig but I have used partimage many times before successfully.

---

