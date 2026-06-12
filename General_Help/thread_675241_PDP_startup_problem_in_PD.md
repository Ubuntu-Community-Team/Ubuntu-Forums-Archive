---
title: "PDP startup problem in PD"
date: 2008-01-22
forum: General Help
---

### Post by diPSy on 2008-01-22
Hi. I install Pure Data and two extensions (pdp,gem) from Synaptic. When i try startup Pure Data with PDP lib enabled, i always get this- ```
PDP INIT ERROR: pd symbol clash adding symbol pdp: new=8a46b210 old=00811300
try loading pdp before other libraries
```

I trying to load it before gem, after gem and without gem- nothing happens. I think, it's Ubuntu Gutsy bug.

---

### Post by rudlavibizon on 2008-02-03
I have the same problem, did you find the solution yet?

---

### Post by loneshark on 2008-05-18
Hi There,

You are better off installing pd-extended from [http://puredata.info/downloads](http://puredata.info/downloads)
I have run this with my pdp VJ application for some time.
So, open a terminal window and type
sudo apt-get remove pdp pd
then
sudo dpkg -i Pd-0.39.3-extended-debian-testing-i386.deb
This will work on Gutsy Gibbon (7.10). Don't upgrade to Hardy Heron though - it broke the video output. I'm still trying to work out how to fix this (I have a gig on Thursday -aaah!)

---

