---
title: "Backup Software"
date: 2015-01-14
forum: General Help
---

### Post by wobblycogs on 2015-01-14
Hi,

I'm about half way through setting a home virtualisation system based around a single box running Ubuntu Server14.04 and KVM. My thoughts have now turned to backing up the guests and I was wondering if anyone had any advice about the best route to take.

My setup:
1 * Physical machine running Ubuntu Server 14.04 and KVM
4 * Virtual machines all Ubuntu Server 14.04 (growing to 6 VM's max)
External storage available on a NAS with a fast connection
Collection of other windows and linux physical machines (optional)

In the past I've always rolled my own with rsync and a few scripts which has worked fine but I'm not overly keen on it. My initial thought was to use [Bacula]("http://bacula.org/") but the version available in the repository is nearly 2 years old and seems to have some issues that aren't even being looked at (and I'd need to learn how to drive it). I think if I use Bacula then I'll be installing it myself but I _really_ didn't want the hassle of that. The upside of Bacula is that I should be able to backup the other various machines I have around the place.

So, any thoughts on Bacula vs rsync vs something else? Anything I should think about before picking a solution?

---

### Post by DuckHook on 2015-01-14
You are going whole hog here, with an almost enterprise-grade setup. You may want to consider basing your entire system on LVM and using snapshots as part of your backup strategy. I've never used Bacula so can't help you there. Like you, my backups until now have been self-rolled using rsync, but after trying LVM on a spare laptop, I'm impressed. LVM is more a redundancy tool than a pure backup strategy, so it won't replace rsync (or whatever you choose instead of it), but it plays a part in safeguarding your VMs and, more significantly, your base system as well. Of course, it only works on those Linux boxes that you convert to LVM and it won't work for Windows at all. Conversion is not a trivial task, so it may not be practical for you.

---

### Post by wobblycogs on 2015-01-14
That's a really good idea that I'd not considered, thanks. All my VM's are LVM and already and the drives are small so snapshots are certainly an option as part of a bigger solution. If the Windows machines don't fit in to the solution I don't care so much there's other options I can use there.

I must confess I've thought a couple of times I'm going a bit overkill. Having said that I originally installed OpenStack - now that's overkill!

---

### Post by DuckHook on 2015-01-14
> **wobblycogs said:**
> ...I originally installed OpenStack - now that's overkill!...well, nothing's really overkill when it comes to opening up Linux to see what's under the hood. Some might say my setup is pretty outrageous too, but it's only the result of incurable curiosity. If your VMs reside on a LVM now, then you're 90% of the way there already! Go all in.

---

