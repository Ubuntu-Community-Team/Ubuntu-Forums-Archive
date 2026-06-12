---
title: "How to Download Distribution Upgrade for later installation?"
date: 2016-01-17
forum: General Help
---

### Post by neu5eeCh on 2016-01-17
Just a quick question, hopefully easy to answer: 

While I have access to an ultra-fast (at the library let's say) connection, how do I download the necessary files for a distribution upgrade for later install? 

In the apt-get man pages, I notice:

 -d, --download-only
           Download only; package files are only retrieved, not unpacked or installed. Configuration Item:
           APT::Get::Download-Only.

Does this switch combine with the distribution upgrade command?

---

### Post by deadflowr on 2016-01-17
> Does this switch combine with the distribution upgrade command?

No.
Distribution Upgrades are an entirely different command ***do-release-upgrade***,
and the -d option actually means development, as in it will upgrade to the development version.

I'm not sure how one would download the upgrade for later use.

i think I have seen somewhere about upgrading from a fresh livecd of a newer version, from within the existing system.
But don't hold that as true or accurate, I'm probably delusional or it was in a dream I had, or something.

---

### Post by neu5eeCh on 2016-01-17
Okay, thanks for the answer. I'll explore the live-CD, possibly drug-induced, fever-vision of which you speak. ;-)

---

### Post by grahammechanical on 2016-01-17
Please be careful.

It may have been fixed by now but about six months to a year ago some found that using the live DVD/USB to upgrade an existing install of Ubuntu actually worked like the Erase disk and install Ubuntu method. It certainly over-wrote what was in the Ubuntu partition. Maybe other partitions as well.

It may be fixed but who wants to be the first to try it out. Not me certainly. I would much rather back up my data and do a fresh install.

Regards.

---

### Post by neu5eeCh on 2016-01-17
Thanks for the warning. And I kinda' remember that imbroglio. 

Fortunately, I keep everything in triplicate (and all my inbox folders are linked to a separate partition). If I try the live-CD and it wipes out my install, then hey, I've got a fresh install. =)

---

