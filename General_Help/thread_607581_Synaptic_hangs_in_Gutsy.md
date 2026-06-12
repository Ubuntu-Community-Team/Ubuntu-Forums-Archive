---
title: "Synaptic hangs in Gutsy"
date: 2007-11-09
forum: General Help
---

### Post by rola25 on 2007-11-09
Hi to all!
I have following strange problem:

Everytime I go to "Settings-Preferences" in Synaptic, then change something (like colums, which should be displayed) and the press OK or Apply, Synaptic hangs and can only be killed in a terminal window. Everything else works (installing software,....)

I have already tried following:

apt-get clean
/var/lib/apt/list removed and create new directories, then apt-get update
/var/cache/apt/*.bin files deleted and executed apt-get update
root/.synaptic directory removed (starting with a clean synaptic.conf) - same problem

Are there any other files, which could be corrupted and make synaptic hang?

Thanks + Greetings from Austria

rola25

---

### Post by manzyuk on 2008-05-06
I confirm the problem. I was unable to pin it down either.

---

