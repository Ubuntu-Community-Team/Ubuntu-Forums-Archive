---
title: "Can't install openoffice.org 2.0"
date: 2005-03-28
forum: General Help
---

### Post by gschimek on 2005-03-28
I just finished doing a dist-upgrade to hoary.  After doing that, I tried installing openoffice.org 2 from Synaptic and got the error when I tried to select it.

openoffice.org2:
 Depends: openoffice.org2-core but it is not going to be installed
 Depends: openoffice.org2-writer but it is not going to be installed
 Depends: openoffice.org2-calc but it is not going to be installed
 Depends: openoffice.org2-impress but it is not going to be installed
 Depends: openoffice.org2-draw but it is not going to be installed
 Depends: openoffice.org2-math but it is not going to be installed

I tried selecting all the openoffice.org2 files at once but it gave me the same eror.  
What am I doing wrong?

---

### Post by splatg on 2005-03-28
Try selecting the package in synaptic and then going: Package > Force Version. Then make sure that the hoary package is selected and not the one for warty.

---

### Post by gschimek on 2005-03-28
Force version is greyed out and unselectable.  Any other ideas?

---

