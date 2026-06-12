---
title: "Dependency problem while installing emacs"
date: 2008-03-09
forum: General Help
---

### Post by birenderjit on 2008-03-09
Hi,
  i am having a dependency problem while installing emacs. I have posted the msg that i get when i use sudo apt-get.... Any help in this regard will be appreciated.

I have gutsy installed.

sudo apt-get install emacs-snapshot emacs-snapshot-el
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  emacs-snapshot: Depends: emacs-snapshot-bin-common (= 1:20080228-2~gutsy) but it is not going to be installed
                  Depends: libungif4g (>= 4.1.4) but it is not installable
  emacs-snapshot-el: Depends: emacs-snapshot-common (= 1:20080228-2~gutsy) but it is not going to be installed
E: Broken packages

Thanking you in anticipation,
Birender

---

### Post by zvacet on 2008-03-09
To see that you have all repos open system>admin>software sources>check all boxes under Ubuntu software and updates tab.Reload.Go to the synaptic>edit tab>fix bbroken packages.if that doesn´t work 

```
sudo apt-get install libungif4g emacs-snapshot-bin-common emacs-snapshot-common
```

---

