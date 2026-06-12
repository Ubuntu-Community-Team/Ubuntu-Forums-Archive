---
title: "Cannot install VLC, Beagle, Amraok, etc."
date: 2007-08-26
forum: General Help
---

### Post by Adamaeus on 2007-08-26
Every time I try to install any of the aforementioned pieces of software, I get the same error. Observe: 

[I]sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: libdc1394-13 but it is not installable
       Depends: libdvdnav4 (>= 0.1.9) but it is not installable
       Depends: libdvdread3 but it is not installable
       Depends: libgsm1 (>= 1.0.10) but it is not installable
       Depends: libid3tag0 (>= 0.15.1b) but it is not installable
       Depends: libmad0 (>= 0.15.1b) but it is not installable
       Depends: libmodplug0c2 (>= 1:0.7-4.1) but it is not installable
       Depends: libmpcdec3 but it is not installable
E: Broken packages
[/I]

What on Earth is going on, and how do I fix it? Any help would be greatly appreciated.

---

### Post by por100pre1 on 2007-08-26
Try this:

```
sudo apt-get install -f
```

---

### Post by r4ik on 2007-08-26
Did you enable extra repositories ?

If not,

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

Might help.

Good luck !

---

### Post by Adamaeus on 2007-08-27
> **por100pre1 said:**
> Try this:

```
sudo apt-get install -f
```


Hey, that was simple. Did the trick quite nicely. Thanks a million!

---

