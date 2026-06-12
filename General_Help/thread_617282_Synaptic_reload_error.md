---
title: "Synaptic reload error"
date: 2007-11-19
forum: General Help
---

### Post by h377r1d3r on 2007-11-19
When i try to update synaptic with synaptic package manager this error appears:

[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)


Can anyone help me with this?

---

### Post by atlfalcons866 on 2007-11-19
that link is broken so i am guessing the server is down. You can change the server by going to
synaptic package manager
settings>repositorys
where it says download from click the box next to it.
then click other then select best server

---

### Post by por100pre1 on 2007-11-19
Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo dpkg --configure -a
```

---

### Post by h377r1d3r on 2007-11-19
I have changed repo from main server to the closest one - that helped. thanks :)

---

