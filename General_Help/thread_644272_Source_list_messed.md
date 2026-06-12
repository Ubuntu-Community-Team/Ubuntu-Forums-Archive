---
title: "Source list messed"
date: 2007-12-18
forum: General Help
---

### Post by Shininggg on 2007-12-18
Tried to add some repository but now the gnome-app-install won't open saying line 2 has a problem :

    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to
upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted
multiverse
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main
multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multi-
verse restricted
# Dépôt de Medibuntu
deb [http://fr.packages.medibuntu.org/](http://fr.packages.medibuntu.org/) gutsy free non-free
# Dépôt de Ahser256
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french
# Dépôt de pok3D
deb [http://pok3d.net/gutsy](http://pok3d.net/gutsy) ./

Now i tried to put # in front of it but then the problem is the multiverse on line 5 

At least i had backed up the original source list... 

Anyone can help ?
Thx

---

### Post by diatribe on 2007-12-18
your entires sources.lst is broken, all the multiverse/gutsy/whatever instances need to be on the deb line; fix this and it will work

---

### Post by Shininggg on 2007-12-20
YEp, you're right! 

I took those from the simple like Ubuntu guide, turns out there was a warning a the beginning of the book stating command were usually one liner  unless told otherwise.

---

