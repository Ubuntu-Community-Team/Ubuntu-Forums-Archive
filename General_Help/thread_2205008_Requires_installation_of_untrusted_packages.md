---
title: "Requires installation of untrusted packages?"
date: 2014-02-11
forum: General Help
---

### Post by MagisterDixit on 2014-02-11
Every update that I get in the update manager gives me the same error when I try to install it:

[COLOR=#ff0000]Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.[/COLOR]

What is going on and how do I fix it? Adobe and Mozilla both have updates that I can't seem to use. I am on Ubuntu 12.04 LTS.

---

### Post by slickymaster on 2014-02-11
Try to rebuild your cache:```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean 
sudo apt-get update
```

---

### Post by MagisterDixit on 2014-02-11
Thanks, Slickymaster!

---

