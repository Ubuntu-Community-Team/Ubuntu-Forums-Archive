---
title: "Alternatives to update manager?"
date: 2014-06-29
forum: General Help
---

### Post by jwbrase on 2014-06-29
Over the past few LTS releases of Ubuntu, I've been finding that Update Manager has been getting less and less useful and more annoying to use with regards to its handling of unauthenticated packages.

The first change (between 10.04 and 12.04 as I recall) was that it went from allowing you to update unauthenticated packages with a warning to not allowing you run an update until unauthenticated packages were deselected. I was a bit annoyed by this, but as it was enforcing a policy that I really probably should have been using myself, I was quite willing to live with it.

The most recent change, however, makes Update Manager completely useless. On 14.04, Update Manager no longer gives a list of packages that can't be authenticated, meaning that I have no means of just running the updates that can be authenticated. I almost always have some repository or other that is having a temporary authentication issue, so now, when Update Manager comes up, I close it, open up Synaptic, hit "Mark All Upgrades", and have done with it. (Incidentally, this puts me in exactly the same habit of running unauthenticated upgrades, because it's easier than not doing so, that I was in previous to 10.04, so Canonical's efforts to get their users to behave more safely have come to naught).

So at this point I'd really like to find some sort of alternative to Update Manager. Bascially, anything that will notify me when updates are available and either allow me to install unauthenticated packages or give me a list of packages that aren't authenticated so that I can deselect them.

Can anyone offer any suggestions?

---

### Post by oldos2er on 2014-06-29
```
sudo apt-get update
``` will show you which repositories need authentication, and will usually give a specific reason for it e.g. NO_PUBKEY or BADSIG errors, both of which are not difficult to fix.

---

### Post by philinux on 2014-06-29
Then use grep too.

e.g

```
sudo apt-get update | grep NO_PUBKEY
```

and another example

sudo apt-get update | grep -E "NO_PUBKEY|BADSIG"

---

### Post by Bucky Ball on 2014-06-29
Yes to the above. I generally don't use the Update Manager (Software Updater), preferring:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

