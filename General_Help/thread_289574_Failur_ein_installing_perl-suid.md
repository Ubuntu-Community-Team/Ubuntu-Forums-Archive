---
title: "Failur ein installing perl-suid"
date: 2006-10-31
forum: General Help
---

### Post by glave on 2006-10-31
I'm trying to get perl-suid going, but hitting an error I've not seen before.
```

root@arcade:~# sudo apt-get install perl-suid
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
  perl-suid: Depends: perl (= 5.8.7-5ubuntu1) but 5.8.7-5ubuntu1.2 is to be installed
             Depends: libperl5.8 (= 5.8.7-5ubuntu1) but it is not going to be installed
E: Broken packages
root@arcade:~#

```

I'm not real sure where to proceed, as I've not seen this before, googling hasn't picked anything up either, and I didn't immediately see anything related on the forums.

---

### Post by glave on 2006-10-31
I've tried doing apt-get update perl, and even install perl, but I get errors telling me that its up to date.

---

### Post by glave on 2006-11-07
I'm still trying to hash this one out, any thoughts?

---

