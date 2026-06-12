---
title: "apt-get Unable to locate package"
date: 2013-08-14
forum: General Help
---

### Post by rieuk on 2013-08-14
Hey guys, 

 I'm trying to install package "libhdf5-mpich-dev". I've installed this once before, then I did "apt-get remove" to it. Now I want to reinstall it, but it can't even locate the package. I didn't change anything in my sources.list. What in the world??

---

### Post by deadflowr on 2013-08-14
What Ubuntu release are you running?

Lucid and Precise use that version, but the other releases run a different version.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=libhdf5-mpich&searchon=names](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=libhdf5-mpich&searchon=names)

---

### Post by rieuk on 2013-08-14
I'm running 12.04.

---

### Post by deadflowr on 2013-08-14
The package should be in your repos, because they're in mine.
They're in the universe repositories.
You can try running
```
sudo apt-get clean && sudo apt-get update
```
To try to clear and refresh the package list you have.

If that doesn't help, you can also download the package from the link I provided earlier.

---

### Post by rieuk on 2013-08-17
I ended up using the software manager to download and install the synaptic package manager. Then I used this to get the package. Honestly I can't be bothered solving this problem anymore :( my patience has been worn thin with Ubuntu

---

### Post by ibjsb4 on 2013-08-17
Your still using apt-get, synaptic is just a gui for it.

---

