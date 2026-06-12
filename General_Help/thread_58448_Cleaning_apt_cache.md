---
title: "Cleaning apt cache"
date: 2005-08-20
forum: General Help
---

### Post by kLy on 2005-08-20
Hey

I know there's an apt-get clean and autoclean but that's not what I'm looking for. I don't have a lot of bandwidth so keeping .debs are important to me. However I also don't like wasting disk space. Now "autoclean" cleans everything that can't be downloaded any more. That doesn't help me. For instance I have this in the cache:

mozilla-firefox_1.0.2-0ubuntu5.4_i386.deb
mozilla-firefox_1.0.2-0ubuntu5_i386.deb
mozilla-firefox_1.0.6-1ubuntu1~5.04ubp1_all.deb

Now I wouldn't need the older versions ever I don't think. Is there some way to automatically clean out older versions of debs or debs that aren't installed (provided of course it asks you for confirmation) but keeping the rest?

Thanks

---

### Post by nad on 2005-08-20
man apt-get :
       autoclean
              Like  clean,  autoclean  clears  out the local repository of re-
              trieved package files. The difference is that  it  only  removes
              package  files that can no longer be downloaded, and are largely
              useless. This allows a cache to be maintained over a long period
              without  it  growing  out  of  control. The configuration option
              APT::Clean-Installed will prevent installed packages from  being
              erased if it is set to off.

---

### Post by kLy on 2005-08-20
Yeah, that's what I meant by "autoclean". However, like I said, this would remove certain packages I want and others that I don't. I found this, which may be useful:
[http://home.tiscali.cz:8080/~cz210552/aptsmartclean.htm](http://home.tiscali.cz:8080/~cz210552/aptsmartclean.htm)

---

### Post by nad on 2005-08-20
aptsmartclean looks interesting if the APT::Clean-Installed switch set to off is still to aggressive.

"The configuration option APT::Clean-Installed will prevent installed packages from being
erased if it is set to off."

Or just move debs you want to keep elswhere.

---

### Post by kLy on 2005-08-20
actually, it wasn't aggressive enough. It kept most of the older packages since I guess they can "still be downloaded" ie. from the original ubuntu depos.

---

