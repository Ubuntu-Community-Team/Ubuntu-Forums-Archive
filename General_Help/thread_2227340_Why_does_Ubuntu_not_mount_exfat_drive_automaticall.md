---
title: "Why does Ubuntu not mount exfat drive automatically?"
date: 2014-06-01
forum: General Help
---

### Post by nknwn on 2014-06-01
Hi,
I wanted to access a hard drive which was formatted in Windows with the **exfat** format.

I found this handy video: [https://www.youtube.com/watch?v=IbILFQFBVFA](https://www.youtube.com/watch?v=IbILFQFBVFA)
and the commands in the Terminal were:

**sudo add-apt-repository ppa:relan/exfat**

followed by

**sudo apt-get update && sudo apt-get install fuse-exfat exfat-utils**

This worked and the hard drive mounted automatically.

My question remains why does Ubuntu not already have the above installed?
Also, why is there nothing found in the Software Centre when I search for **exfat**?

Might it be to do with intellectual property?

---

### Post by mc4man on 2014-06-01
It's not default installed in Ubuntu but has been available for some time & currently for all supported releases so really  no need for a ppa 

As far as software-center, well it has some anomalies in searching. Try ```
exfat-
```
(actual package names are exfat-fuse & exfat-util

---

### Post by nknwn on 2014-06-01
Thanks,** exfat-** works as a search term in the software centre while **exfat** does not. Seems like a bug to me.

---

### Post by mcduck on 2014-06-01
"exfat" works, but because it's not a graphical application it doesn't appear unless you either click the "Show 4 Technical Items"-text near the bottom of the window or use specific enough search term. Not exactly a bug but more of a design issue, the button for displaying libraries, command-line apps etc. is pretty easy to miss...

---

### Post by mc4man on 2014-06-01
> **mcduck said:**
> "exfat" works, but because it's not a graphical application it doesn't appear unless you either click the "Show 4 Technical Items"-text near the bottom of the window or use specific enough search term. Not exactly a bug but more of a design issue, the button for displaying libraries, command-line apps etc. is pretty easy to miss...
Correct you are, forgot about the tech item deal as prefer synaptic. Seem an odd descision to put in an added dark 'border' though I guess it's fairly obvious after some use..

---

