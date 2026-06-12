---
title: "Where is the linux-image deb!!!"
date: 2006-09-03
forum: General Help
---

### Post by peabody on 2006-09-03
I was playing with the prims54 islsm drivers for my adapter.  I couldn't get them to work so now I'm going back to the way I had things with ndiswrapper, but now it isn't working.  I figure it has to do with the fact that the latest prism54 stuff installed new kernel modules, so I figured I just need to resort to the old ones.  But I don't have a linux-image deb in my /var/cache/apt/archives!  And I can't find a linux-image deb in the repositories either.  WTF???  Where does this file come from?

---

### Post by meng on 2006-09-03
That's funny, I could find this package
linux-image-2.6.15-23-386
"WTF??" - has it really been that frustrating for you? Take a deep breath!

---

### Post by peabody on 2006-09-03
> **meng said:**
> That's funny, I could find this package
linux-image-2.6.15-23-386
"WTF??" - has it really been that frustrating for you? Take a deep breath!

azathoth on IRC helped me out.  Yes, "WTF??" is not normally part of my repertoire.  I guess I was surprised that the package was no where to be found in my /var/cache/apt/archives.  I can usually find a deb I've had installed at one time from there.  I thought everything that ever gets downloaded via synaptic/apt-get ends up there.  After looking for about half an hour and not finding the deb in the repositories viewed raw from the browser I got very frustrated.

I should have thought to have just searched the main web site.  I forgot about the package listing.  It's been a long morning.

Just in case anybody else is dense like me and decides it's fun to just copy paste the sources line into the browser, linux-image kernel updates are on the security repo and they're under the linux-source-<version> folder.

---

### Post by meng on 2006-09-03
I guess I was just trying to say, don't let the glitches get the better of you. Getting upset is as good as getting defeated. Glad to hear it worked out. I wonder if you ever cleaned out your sources cache, or perhaps it gets done automatically periodically.

---

### Post by peabody on 2006-09-03
> **meng said:**
> I guess I was just trying to say, don't let the glitches get the better of you. Getting upset is as good as getting defeated. Glad to hear it worked out. I wonder if you ever cleaned out your sources cache, or perhaps it gets done automatically periodically.

I was sort of defeated :).

I have never done an apt-get clean once.  The /var/cache/apt/archives folder is absolutely filled with debs, but not one of them is named linux-image.  find turns up nothing.

Edit:  Something is definitely up!  I swear I've never done a clean on my apt cache, but I now only have about 400 megs worth of packages in there when at one time I had over 700.  Is there a cron.monthly clean script or something?

Edit2: There doesn't appear to be.  That is really, really, really, really strange.

---

