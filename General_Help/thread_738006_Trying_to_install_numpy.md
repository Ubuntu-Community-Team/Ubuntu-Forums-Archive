---
title: "Trying to install numpy"
date: 2008-03-28
forum: General Help
---

### Post by bearlevi on 2008-03-28
Why does synaptic only have python-numeric and no python-numpy? Also when try to download and install it from numpy.org it doesn't complete the install. Is it because I am using Dapper? Any suggestions?

---

### Post by justleen on 2008-03-28
it is avail in apt?
```

leen@leen-laptop:/var/log$ apt-cache search numpy
...
python-numpy - Numerical Python adds a fast array facility to the Python language
python-numpy-dbg - Numerical Python adds a fast array facility to the Python language (debug extension)
python-numpy-dev - Numerical Python adds a fast array facility to the Python language
python-numpy-doc - Numpy documentation
python-numpy-ext - Numerical Python adds a fast array facility to the Python language
...

```
make sure you have all the repositories enabled.

How do you install it? when checking sourceforge, there is no .deb package, only the source and an .egg binary.. you should use the source.

---

### Post by bearlevi on 2008-03-28
it is not available in apt. all I have in the apt-cache that comes up when searching for numpy is numeric, scientific, and numarray. when i tried to install it, I was trying to install it from a .tar file and following the readme instructions which just say to type 'python setup.py install'. thanks. any other suggestions?

---

### Post by justleen on 2008-03-28
and what error are you getting?

---

### Post by bearlevi on 2008-03-28
i am getting a system error, "failed to test configuration."

---

### Post by bearlevi on 2008-03-28
are there specific repositories that need to be enabled, besides the multi and uni-verse?

---

### Post by justleen on 2008-03-28
hm.. quite generic message...

Actually, youre right, its not in the Dapper repros.. 
you could try to grab the feisty or gutsy packages, see if that installs?

---

### Post by bearlevi on 2008-03-28
yeah i thought that might be a problem, but I can't install the fiesty or gutsy distros on my laptop. some weird hardware software issue i'm not completely aware of. 

can i use the repros for feisty or gutsy while running dapper? and if so how do i go about doing that?

---

### Post by justleen on 2008-03-28
i wouldt use the whle repro, i'd just download this one package from a ubuntu mirror

---

### Post by bearlevi on 2008-03-28
ok cool, i think i found one thanks for all your help

---

### Post by justleen on 2008-03-28
np. sorry for the typo's! (just reread my own reply...oops)

---

