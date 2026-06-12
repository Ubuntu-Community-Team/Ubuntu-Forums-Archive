---
title: "ignore kernel in update manager"
date: 2007-03-24
forum: General Help
---

### Post by outtaphase on 2007-03-24
How do I configure Update Manager to ignore kernel updates?

---

### Post by Dr. Nick on 2007-03-25
cant guarantee this will work, but worth a shot.

Open synaptic and search "linux-image-generic", select it then go to the "package" menu and select "lock version"

---

### Post by outtaphase on 2007-03-25
I _think_ this works, but I Synaptic did not acknowledge locking the package version.

---

### Post by Dr. Nick on 2007-03-25
If it didnt work then make sure you locked the "linux-image-generic" and not the linux-image-generic-some-version" package. The linux-image-generic" is just a placeholder of sorts for the newest version.

---

### Post by stmiller on 2007-03-26
Here you go:

[http://ubuntuforums.org/showthread.php?t=161190](http://ubuntuforums.org/showthread.php?t=161190)

Or try this:

# apt-get install wajig
# wajig hold <package_name>

---

