---
title: "ttf-opensymbol issue -edited /var/lib/dpkg/status"
date: 2008-06-21
forum: General Help
---

### Post by maestrobwh1 on 2008-06-21
For the life of me, I could not get rid of this package without some serious issues -exit status 139 from dpkg.  It is keeping me from doing a distribution upgrade gutsy--> hardy.

The touch method described in several posts simply made the error go away, but as soon as something involved updating/upgrading this package, it would interrupt the update.

This might be ugly, but I need a confirmation that this might be a solution for me:

I 'removed' it by removing its entry in 

/var/lib/dpkg/status

Now in synaptic/adept, it shows as not installed... so I assume it will be "ignored" as if it does not exist on my system.

Just for good measure I deleted the /usr/share/fonts/openoffice folder and contents.

I also ran 
sudo defoma-reconfigure

Any perceived issues from what I have done?  I don't use openoffice.

The other thing is that I want to upgrade from gutsy to hardy, so will a distribution upgrade reinstall openoffice?  I don't want ttf-opensymbol.  This is not the first time this stupid package caused issues for me.  It was an issue on another computer when I had feisty.

---

