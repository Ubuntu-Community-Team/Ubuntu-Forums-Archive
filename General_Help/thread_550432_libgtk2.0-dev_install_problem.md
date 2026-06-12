---
title: "libgtk2.0-dev install problem"
date: 2007-09-13
forum: General Help
---

### Post by brandonhon on 2007-09-13
I get an error when trying to install libgtk2.0-dev. I searched the forums for help but is looks like all of the posts pertain to dapper not feisty. Below you will find my output from the error. You should know that I have updated, upgraded and -f.

```
bh@bh-mobile:~$ sudo apt-get install libgtk2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages

```

Any ideas?

---

### Post by dcstar on 2007-09-14
> **brandonhon said:**
> I get an error when trying to install libgtk2.0-dev. I searched the forums for help but is looks like all of the posts pertain to dapper not feisty. Below you will find my output from the error. You should know that I have updated, upgraded and -f.

```
bh@bh-mobile:~$ sudo apt-get install libgtk2.0-dev
............
E: Broken packages

```

Any ideas?

Use Synaptic and do the "Fix Broken Packages" function.

---

### Post by brandonhon on 2007-09-14
tried synaptic. it tells me it fixed the problem but it doesn't. anyone else?

---

### Post by Walkboss on 2007-09-14
I am also having this issue. Fix Broken Packages did not remedy the situation.

---

### Post by brandonhon on 2007-09-15
still having issues with install libgtk2.0-dev. tried using synaptics to install it and i get the same error as i posted above. any ideas. is this a faulty package?

---

### Post by brandonhon on 2007-09-19
come on someone has to have this same problem and found a fix. please help i need this package to get gnomad2 working with my gigabeat

---

### Post by brandonhon on 2007-09-20
woohoo, found the answer. if you are having this problem try this.

sudo aptitude install libgtk2.0-dev

it worked for me.

---

