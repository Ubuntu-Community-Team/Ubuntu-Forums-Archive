---
title: "Problem uninstalling Eclipse with ap-get"
date: 2007-01-23
forum: General Help
---

### Post by mrwooster on 2007-01-23
Hi,

I installed eclipse using apt-get, I then attempted to install several plugins from the eclipse website, the result of which eclipse is now not working - I get errors all over the place.

I now want to completely unistall eclipse and reinstall it - but I can't seem to do it.

I have used apt-get remove eclipse, but it says it is only going to remove 377kb of data, not the full 100mb of eclipse, and when I do remove it, the files in /usr/share/eclipse are still there. I tried removing the files in /usr/share/ but that did not work either - it still only re-installed the 377kb of data and then eclipse did not work at all (I only moved the files and later restored them to /usr/share/ so now am back to the origional problem).

I have tried apt-get clean and apt-get autoclean but it still does not seem to work.

I have also tried using --purge but still no luck. 

How do I **completely** remove eclipse and reinstall it? All 100mb.

Thanks

Guy

---

### Post by flixer on 2007-01-23
you can do it easily in synaptic. Just right-click the program and you'll see a bunch options. Then click remove completely.

---

