---
title: "Add/remove programs"
date: 2007-11-30
forum: General Help
---

### Post by DEDb33t on 2007-11-30
I am having some difficulties with the add remove program part of linux ubuntu,  After recently installing ubuntu on my Presario c300 laptop the add remove program part will not seem to work correctly

when i attempt to check the box to the left of the program name or download a program it says i need to refresh the list and than downloads six files.

any help on this matter will be greatly appreciated

---

### Post by navaburo on 2007-12-01
Try going to a terminal and running

```
sudo apt-get update
```

Then see if your problem is resolved.

If not, try installing your applications like this:

```
sudo apt-get install YOUR_PACKAGE_HERE
```

If _that_ doesn't work then there is a problem with your package management. If it does than most likely the problem is with the add/remove app.

Good luck!

---

### Post by DEDb33t on 2007-12-01
yeah that didnt work...

so how would i fix the add.remove programs part?

---

### Post by maybeway36 on 2007-12-01
Check to see if System>Administration>Synaptic will work.

---

