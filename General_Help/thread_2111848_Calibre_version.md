---
title: "Calibre version"
date: 2013-02-03
forum: General Help
---

### Post by iueras on 2013-02-03
Is it possible to get a newer version (or an older one) of Calibre into the repository that synaptic/software center uses? the version that is in there now (0.8.51) happens to be the ONLY one that has a bug preventing Calibre from handling .LIT files of any kind. The bug was not present in 0.8.50 and is fixed in any version higher than 0.8.51. Thanks guys.

---

### Post by howefield on 2013-02-03
I think the best you can do is download and compile from source, or the much easier route would be to add an external repository, however this would mean going outside the official Ubuntu repositories.

[https://launchpad.net/~n-muench/+archive/calibre](https://launchpad.net/~n-muench/+archive/calibre)

---

### Post by oldos2er on 2013-02-03
This command will download and install the most recent version of calibre from its website: ```
sudo python -c "import sys; py3 = sys.version_info[0] > 2; u = __import__('urllib.request' if py3 else 'urllib', fromlist=1); exec(u.urlopen('http://status.calibre-ebook.com/linux_installer').read()); main()"
```
Or you can use the PPA as noted above.

---

### Post by iueras on 2013-02-03
I understand the solutions you guys posted. I did use the second one and got 0.9.17 downloaded, installed, and it works great. I guess I just meant this as kind of a heads up that the version in the repository, in addition to being over a year old, is also the only version that doesn't work out of the box.

Since ubuntu is going for ease of use and such especially among non-linux users I thought that that might be important.

---

### Post by oldos2er on 2013-02-03
You'd need to contact the developers (who don't normally follow these forums) about that, the best way would be to file a bug against the calibre package in the repository. But since it's easier to just update from calibre's website, maybe that's a moot point.

---

### Post by iueras on 2013-02-04
Gotcha. Didn't realize no one in a position to update the repo would be here. Thanks guys.

---

