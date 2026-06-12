---
title: "Scribus Dependencies not complete"
date: 2015-07-27
forum: General Help
---

### Post by arkoprovo1996 on 2015-07-27
Dear All,
I'm not sure I'd this is the right place to post this; nevertheless, I believe that the dependencies of scribus packed for apt-get seems to be incomplete. Scribus depends on texlive-latex-base, but it does not get installed while scribus is installed via apt-get and needs to be installed separately. I'll be glass if someone could fix this problem. Thank You.

---

### Post by Bucky Ball on 2015-07-28
*Thread moved to **General Help**.*

Welcome. You might be better off contacting the [Scribus]("http://www.scribus.net/") or Canonical devs about this. None of us here have any power over what does or doesn't get packaged. We are all volunteers and regular users here, just like you.

Good luck.

(PS: Can't you simply,

```
sudo apt-get install texlive-latex-base
```

Slightly confused about what support you are asking for to be honest. Have you actually got problems running Scribus? :))

---

### Post by ian-weisser on 2015-07-28
Looking at the dependencies for scribus in 15.04:

```
$ apt-cache depends scribus | grep texlive
  Suggests: texlive-latex-recommended 

$ apt-cache depends texlive-latex-recommended | grep base
  Depends: texlive-base
  Depends: texlive-latex-base
```

The dependency is indeed there. But it's a 'Suggests', not a 'Depends'.
The dependency type may be different on your release of Ubuntu. Easy to check (see above).

'Suggests' means the package is not critical to usage of most Scribus features. I don't happen to use Scribus, so cannot judge if that's appropriate.
Suggested packages are NOT installed by default. That's an apt.conf setting, and [easy to change]("http://askubuntu.com/questions/18545/installing-suggested-recommended-packages").

If you want to install suggested packages, [here's an easy way]("http://askubuntu.com/questions/18545/installing-suggested-recommended-packages").

If you believe that the 'Suggests' relationship label is inappropriate and should be changed, please file a bug report against the Scribus package at Launchpad.net. Please ensure you bug report has enough detail for a volunteer Triager to duplicate the problem on their system. If somebody has already filed such a bug report, don't open a duplicate bug; subscribe to the existing bug by clicking the 'Affects me too' link at the top of the bug report.

---

