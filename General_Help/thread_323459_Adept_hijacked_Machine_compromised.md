---
title: "Adept hijacked? Machine compromised?"
date: 2006-12-22
forum: General Help
---

### Post by cgl72 on 2006-12-22
Hello to all
I have a small incident to report and want to know if this has happened before.

I logged into Adept this morning to look if anything such as easytag was available in the repositories. I started by fetching updates, then wrote the word "tag" in the search box at the top, then quickly changed the word to "tags" to restrict my search. I looked at acouple package descriptions, then chose "easytag", selected to install.

I often go directly to "apply changes" but for some reason this time I clicked on "preview Changes" and to my big surprise there were 4 packages. This can happen with dependencies. But I was surprised to see the following packages pertaining to the trustcommerce credit card payment platform!

Python-tclink
Python2.3-tclink
Python2.4-tclink

there is a remote chance that I may have made a false manipulation during my initial package selection, but I cannot figure out for the life of me how by searching for the word "tags" I could have ended up selecting these packages. Needless to say I did not install these packages.

Could this be the work of a rootkit? or other malware? I am not a sysadmin and have no deep knowlege of linux but I am worried about security nonetheless.

Christian

---

### Post by ThrobbingBrain66 on 2006-12-22
I highly doubt there's anything to worry about.  A quick google of the 3 packages shows nothing of concern.  They are all part of Debian's repos and therefore pose no threat.  In my time using Kubuntu, I noticed that Adept did weird things some times.  Synaptic is a much better package manager, IMO.

---

### Post by yopnono on 2006-12-22
No you are totally infected, all you can do is to move to ms windows much safer.
Just kidding. Those packages are in the repo. And like above said, synaptic is much better.

---

