---
title: "Error deb not known"
date: 2007-02-26
forum: General Help
---

### Post by pilot550 on 2007-02-26
Does anyone know why I'm getting this error message, or more importantly, how to fix it? I can't access the repositories.

E: Type '“deb' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

---

### Post by an.echte.trilingue on 2007-02-26
That is a mistake in the configuration file for your package manager

Please post the contents of /etc/apt/sources.list and we'll fix it.

Take care, mat

---

### Post by pilot550 on 2007-02-26
Thanks. Here's what I got:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”

---

### Post by Tesiph on 2007-02-26
Remove the quotes (") on the last two lines.

---

### Post by taurus on 2007-02-26
Remove the " at the beginning and and the end of the second to the last line and remove the last line since it's a duplicate of the one above.

```
gksudo gedit /etc/apt/sources.list
```
Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by pilot550 on 2007-02-26
That fixed it!! Thanks, I really appreciate it.

---

### Post by ech on 2007-03-14
> **pilot550 said:**
> That fixed it!! Thanks, I really appreciate it.

This helped me also thank you!

---

