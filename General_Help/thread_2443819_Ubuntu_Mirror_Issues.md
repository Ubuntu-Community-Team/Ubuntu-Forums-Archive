---
title: "Ubuntu Mirror Issues"
date: 2020-05-20
forum: General Help
---

### Post by listener1379 on 2020-05-20
How can I force do-release-upgrade when Ubuntu mirrors are not synced properly? For example I just did an `apt update` and there is a package with mismatched versions published in the index:
```
$ sudo apt upgrade libodbc1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libodbc1 : Breaks: libodbc1:i386 (!= 2.3.7) but 2.3.6-0.1build1 is to be installed
 libodbc1:i386 : Breaks: libodbc1 (!= 2.3.6-0.1build1) but 2.3.7 is to be installed
E: Broken packages
```

I imagine 1) mirrors should be syncing from a controlled source that has done thorough dependency checking. Maybe main mirror web server can build a coherent package index in a seperate dir then ln -s to the new index if there is some sort of race condition that is producing indexes with this problem?

2) There should be a force flag in do-release-upgrade since I don't really care about some unimportant 19.10 packages when upgrading to 20.04 which is going to use new packages anyway?

---

### Post by grahammechanical on 2020-05-20
Have you reviewed the man page for apt? If you want to force an upgrade for a specific package then check out the man page under install, reinstall, remove, purge. There might be information there that will do what you want. I do not understand how do-release-upgrade comes into this.  Or what the repository mirrors have to do with it either.

Regards.

---

### Post by deadflowr on 2020-05-20
What does
```
apt policy libodbc1
```
show?
There is no version 2.3.7 in any Ubuntu archive so not sure where it's coming from.
The above output should show something.

---

### Post by listener1379 on 2020-08-19
IIRC the offending package was from another repository. I was later able to remove it and upgrade to 20.04.1.

---

