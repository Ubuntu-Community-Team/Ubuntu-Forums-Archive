---
title: "Upgrading Errors"
date: 2005-07-13
forum: General Help
---

### Post by jamberu on 2005-07-13
Is anyone else having problems installing updates (from both Synaptic and using apt-get) I seem to keep getting MD5Sum mismatch errors. Im using the repositories from the Unofficial Ubuntu starter guide.

Thanks,

Duncan

---

### Post by arnieboy on 2005-07-13
```
sudo gedit /etc/apt/sources.list
``` 
change all the urls from "us.archive.ubuntu.com" to "archive.ubuntu.com". That will solve your problems.
for example the following line:
```
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
```
 will look like :
```
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
```
Change all the relevant lines in the same manner and save and close the file.
Then do a 
```
sudo apt-get update
```

That shd have u all set.

---

