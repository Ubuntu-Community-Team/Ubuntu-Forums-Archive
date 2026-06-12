---
title: "libdvdcss2"
date: 2008-07-09
forum: General Help
---

### Post by trevh on 2008-07-09
I warn you, I'm a newbie.

I'm trying to install libdvdcss2 in Ubuntu 8.04.
I guess from the About, I'm using Hardy Heron.
None of the instructions seem to work for me, when I enter

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

I get message

gpg: no valid OpenPGP data found.

---

### Post by Titan8990 on 2008-07-09
It would be much easier for you to use something that is already prepackaged in a .deb. Is that a codec for video?

---

### Post by oscarsfriend on 2008-07-09
Try this:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by plucky on 2008-07-09
If adding the key fails using the previous link,try this to add the key.
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


Good Luck

---

