---
title: "tetex-extra package not in synaptic"
date: 2005-09-05
forum: General Help
---

### Post by nsa_767 on 2005-09-05
Hi there,

I'd like to install the tetex-extra package, but it doesn't seem to be in any of the Ubuntu repositoires....  :-? ODD ISN'T IT?

Maybe I'm missing a repository or for some reason it's not showing up in synaptic.

Please advise.

---

### Post by Manny C on 2005-09-05
Hi NSA,

Tetex-extra package is in the main repositories. Please check to ensure that you have not corrupted your sources.list file. Furthermore, if you haven't you should
```
sudo apt-get update
``` and then ```
sudo apt-get install tetex-extra
```. 

My sources.list file:
```
deb http://au.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://au.archive.ubuntu.com/ubuntu hoary main restricted

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://au.archive.ubuntu.com/ubuntu hoary universe
deb-src http://au.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
``` 

Hope this helps. I have got tetex-extras installed. No problems here.

---

### Post by nsa_767 on 2005-09-05
Hi,

Thanx, I added all the Australian (I assume they are Australian) repositories to my list and it worked.... Downloading tetex-extra now.

Thank you, I really appreciate it.

---

### Post by Manny C on 2005-09-05
[QUOTE=nsa_767]Hi,

Thanx, I added all the Australian (I assume they are Australian) repositories to my list and it worked.... Downloading tetex-extra now.

Thank you, I really appreciate it.[/QUOTE]

No problems.

---

