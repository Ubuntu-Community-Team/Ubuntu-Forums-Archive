---
title: "apt-get problem"
date: 2008-07-02
forum: General Help
---

### Post by woopud on 2008-07-02
When I try to install something I get the following error.

woopud@woopud-desktop:~$ sudo apt-get install googleearth-4.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth-4.2
woopud@woopud-desktop:~$ 

What to do ?
Bert

---

### Post by soccerboy on 2008-07-02
try ```
sudo apt-get install googleearth-package
```
EDIT: strike that.  that's not it.

---

### Post by drs305 on 2008-07-02
Do you have the medibuntu repository installed and enabled?

If not, for hardy:
```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

Also, the package "googleearth" is a meta package and should install the most recent version and dependencies in the repository.

---

### Post by woopud on 2008-07-02
> **drs305 said:**
> Do you have the medibuntu repository installed and enabled?

If not, for hardy:
```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
```

Also, the package "googleearth" is a meta package and should install the most recent version and dependencies in the repository.

Thank you !
That did the trick.

Bert

---

