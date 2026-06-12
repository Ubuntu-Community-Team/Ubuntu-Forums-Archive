---
title: "Firefox 3 is now Firefox 2?"
date: 2008-06-20
forum: General Help
---

### Post by jessedyer on 2008-06-20
I got up this morning and fired up my browser, and immediately noticed that Firefox 3's navigation bar wasn't functioning.
I checked Help -> About, and found that the browser was reporting it's version number as 2.0.0.14.  So I checked:

.oO(jdyer@onosendai ~/Apps) dpkg -l | grep firefox
ii  firefox                                                                   3.0+nobinonly-0ubuntu0.8.04.1      meta package for the popular mozilla web bro
rc  firefox-2                                                                 2.0.0.14+2nobinonly-0ubuntu1       lightweight web browser based on Mozilla
ii  firefox-3.0                                                               3.0+nobinonly-0ubuntu0.8.04.1      safe and easy web browser from Mozilla
ii  firefox-3.0-venkman                                                       3.0+nobinonly-0ubuntu0.8.04.1      dummy upgrade package for firefox-3.0-venkma
rc  firefox-themes-ubuntu                                                     0.5.4.4                            Firefox themes matching the Ubuntu desktop l
.oO(jdyer@onosendai ~/Apps) sudo apt-get remove firefox-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package firefox-2 is not installed, so not removed

I even tried tracing back the executable within the firefox3 package and running it, no dice.  I downloaded the Linux FF3 tarball and fired it up from a drectory under home; it also reports 2!  Has the planet gone mad?

---

### Post by Het Irv on 2008-06-20
Have you tried removing every instance of Firefox from your system, 2 or 3, and then reinstalling.  You should be okay if you save you preferences (which will save all of you add-on and bookmarks), located at /home/username/.mozilla, but try removing everything else and then reinstalling.

---

