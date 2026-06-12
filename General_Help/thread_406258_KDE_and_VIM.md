---
title: "KDE and VIM"
date: 2007-04-10
forum: General Help
---

### Post by shofetim on 2007-04-10
Well I have been beating my head against a wall for the last half an hour or so, trying to get VIM in Kubuntu to spell check.
I couldn't find the answer here, and I couldn't find a bug, and I couldn't find any settings that where wrong, but I finally got it, so I thought I'd post the solution.

The problem: no spell check or highlighting in VIM on Kubuntu Edgy Eft.

Solution: Kubuntu only installs a minimalist version of VIM, which doesn't have everything, and there seems to be no way of noticing that... just install the full version with synaptic. System > Synaptic or ```
 sudo apt-get install vim 
``` should do it.

---

### Post by taurus on 2007-04-10
```
sudo aptitude update
sudo aptitude install vim-full
```

---

