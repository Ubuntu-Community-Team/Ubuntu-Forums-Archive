---
title: "Tried installing automatix2, serious error has messed up my system!"
date: 2007-01-25
forum: General Help
---

### Post by stephentyler20 on 2007-01-25
On Ubuntu 6.10, I attempted to install automatix2 per the code instructions on their website. Something went wrong, and now it says there's a fatal error with python-vte... something about it's a dependency and won't be installed. I tried downloading python-vte, but it won't go in synaptics (another error). In addition, a lot of my menu icons are missing, and the whole desktop seems a bit screwy. What am I supposed to do here?

---

### Post by oldmanstan on 2007-01-25
dont use automatix? hehe :)

did you try completely removing the offending packages? then get rid of automatix and reinstall the ubuntu-desktop package maybe? i dunno, sounds like some files just got overwritten or corrupted so that might work

---

### Post by Tomosaur on 2007-01-25
Try:
```

sudo dpkg-reconfigure ubuntu-desktop
```

If that doesn't work, try:
```

sudo aptitude reinstall ubuntu-desktop

```

The latter SHOULD fix your problems, but it may take a while if you've used Ubuntu for a while and cleaned up any excess crap.

---

### Post by jackrobinson on 2007-01-26
> **stephentyler20 said:**
> On Ubuntu 6.10, I attempted to install automatix2 per the code instructions on their website. Something went wrong, and now it says there's a fatal error with python-vte... something about it's a dependency and won't be installed. I tried downloading python-vte, but it won't go in synaptics (another error). In addition, a lot of my menu icons are missing, and the whole desktop seems a bit screwy. What am I supposed to do here?
just try the following:
```
sudo apt-get -f install
```
and paste the results here.
and do not get too worked up. Its probably just one of the official repositories not enabled. Are you on Kubuntu 6.10?

---

