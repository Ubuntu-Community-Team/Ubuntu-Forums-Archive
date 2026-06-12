---
title: "Help! KDM Ate my login screen!"
date: 2007-03-09
forum: General Help
---

### Post by b0ng0 on 2007-03-09
I installed a new KDM Login Theme for Kubuntu Edgy and for some reason it overwrote the default one that comes with Kubuntu without asking..

I was wondering how I could get the original one back (it's not on KDE-Look.org), presumably it's on the LiveCD but I have no idea how to get it back really.

Thanks for any help.

---

### Post by bettlebrox on 2007-03-09
1st I'd try and reinstall it:

sudo apt-get install --reinstall kdm

If that doesn't work, remove it then install it:

sudo apt-get remove --purge kdm
sudo apt-get install kdm

But, some other packages might get removed, so you may need to reinstall those too.

---

