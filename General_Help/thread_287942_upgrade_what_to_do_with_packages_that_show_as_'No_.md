---
title: "upgrade: what to do with packages that show as 'No available' and 'newer'"
date: 2006-10-29
forum: General Help
---

### Post by matrooswolf on 2006-10-29
Hi 
I read this comment from someone on slashdot who upgraded without problems 
> The key, I think, was in cleaning the crap (and un-upgradeable packages) off the box by getting the results of apt-show-versions | grep 'No available' | awk '{ print $1 }' (i.e. all packages with no repository entry) and removing them before starting. That and having a good backup.
So, is it wise before upgrading to clean packages and remove those that are 'No available'?
the command ```
apt-show-versions | grep 'No available' | awk '{ print $1 }'
``` shows lots of packages, should I remove them?

And what about packages that are newer than the archives?
```
apt-show-versions | grep 'newer' | awk '{ print $1 }'
```
also shows a lot off packages that are newer than those in the archives?
Should I remove them too, downgrade them?

---

