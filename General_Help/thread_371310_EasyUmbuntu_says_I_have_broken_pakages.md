---
title: "EasyUmbuntu says I have broken pakages"
date: 2007-02-26
forum: General Help
---

### Post by impediment on 2007-02-26
I have been in the Absolute Beginners forum and searching previous posts  but can't get a handel on this situation- I just did anothier complete uninstall of EasyU and got this msg. "dpkg - warning..../usr/lib/easyumbuntu/conf not empty so not removed".  I have an idea it might be ATI stuff as the computer hung when EasyU was trying to install ATI drivers. After reinstalling EasyUmbuntu it still won't install pakages. It says I have broken packages that must be repaired first.  Synaptic says I have no broken pakages(I had it do a repair anyway). Can I backup the problem folder and deleate It?  If so, can someone direct me to the proper tutorial.  TKS for any sugestions.   BTW. my system is updated.

---

### Post by zvacet on 2007-02-27
Try this
```
sudo -i
```
and than go to the /usr/lib and delete easy package with 
```
rm -r filename
```
After that try to install again.

---

