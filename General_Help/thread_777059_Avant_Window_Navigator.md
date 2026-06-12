---
title: "Avant Window Navigator"
date: 2008-05-01
forum: General Help
---

### Post by chrispche on 2008-05-01
It will not upgrade. It says it has a problem libawn and I should wait a few days. It's coming up under a Partial Upgrade and all the file's are to do with AWN.

[http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu)
[http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) (Source Code)

I'm using these repos for AWN. Is there something better.

Should I just wait, does repos at launchpad need to be upgraded?

Why will AWN not update if, it keeps prompting me to.

---

### Post by reefsrt4 on 2008-05-04
I seem to have the exact same issue here.  I'll post some screen captures:


Anyone have any advice on how to resolve?  Also attaching copy of sources.list for review.  

Thanks in advance.
Mike

---

### Post by moonbeam on 2008-05-04
Reacocard recently renamed some of his awn packages.

What appears to be working for most people is uninstalling all awn packages and reinstalling.

Issues with reacocard's packages tend to get the best response if you post in this thread:  [http://ubuntuforums.org/showthread.php?t=762363&highlight=avant+window+navigator](http://ubuntuforums.org/showthread.php?t=762363&highlight=avant+window+navigator)

---

### Post by reefsrt4 on 2008-05-04
Thanks for the help and link.  It worked.  :)

---

### Post by chrispche on 2008-05-05
> **reefsrt4 said:**
> I seem to have the exact same issue here.  I'll post some screen captures:


Anyone have any advice on how to resolve?  Also attaching copy of sources.list for review.  

Thanks in advance.
Mike

I found out how to solve this problem. Do sudo apt-get dist-upgrade although this will not upgrade Hardy it will upgrade AWN. Then once done un-install AWN and re-install the new version in the repos.

---

