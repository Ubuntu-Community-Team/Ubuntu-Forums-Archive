---
title: "Can't install anything!"
date: 2007-11-02
forum: General Help
---

### Post by cvtate on 2007-11-02
For some reason when I try to run updates or install any software I get this error (I'm using Gutsy)

E: /var/cache/apt/archives/libdecoration0_1%3a0.6.0+git20071008-0ubuntu1.1_i386.deb: files list file for package `libgtk1.2-common' is missing final newline

Help!!

---

### Post by hikaricore on 2007-11-02
Hmm... you didn't by any chance use any third party script-based installers such as Automatix did you?

---

### Post by cvtate on 2007-11-02
No, I just installed gutsy two days ago and the only things I've installed since was amarok

---

### Post by hikaricore on 2007-11-02
You may want to try the following:

```
sudo apt-get clean
```

You will need to re-download any packages you were trying to install, but the package manager should do this for you.

---

### Post by cvtate on 2007-11-02
Okay I did that and I'm still getting the same error :-(

---

### Post by cvtate on 2007-11-02
Wow, so nobody else has had this problem??  I'd like to use ubuntu but obviously if I can't install anything then that's a big issue.

---

### Post by Pumalite on 2007-11-02
Try:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by cvtate on 2007-11-02
okay I did those and on the third one I get this error:

(Reading database ... dpkg: error processing /var/cache/apt/archives/libdecoration0_1%3a0.6.0+git20071008-0ubuntu1.1_i386.deb (--unpack):
 files list file for package `libgtk1.2-common' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libdecoration0_1%3a0.6.0+git20071008-0ubuntu1.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Same thing.  GAH :confused:

---

### Post by PmDematagoda on 2007-11-02
Try this command:-

```
sudo dpkg --force-all -i
```

---

### Post by phi1ip on 2007-11-05
> **PmDematagoda said:**
> Try this command:-

```
sudo dpkg --force-all -i
```

i had a similar problem. tried this, get error message below.

dpkg: --install needs at least one package archive file argument

suggestions?

---

### Post by PmDematagoda on 2007-11-05
Try deleting the problem package:-

1) Open up nautilus in sudo mode using 
```

sudo nautilus
```

Then go to the path given in the error, in your case it is:-

/var/cache/apt/archives/libdecoration0_1%3a0.6.0+g it20071008-0ubuntu1.1_i386.deb

and just delete the package and see if that would solve your problem.

---

