---
title: "Help me! I can't install Gstreamer."
date: 2006-11-02
forum: General Help
---

### Post by realtiger on 2006-11-02
Help me :(  :(  :( 

I can't install anything.
This is the error message: ***files list file for package `xmodmap' is missing final newline***.

What's the problem?

Thank you very much!

---

### Post by Architeuthis on 2006-11-02
Is this in your synaptic package manager? And are you using edgy eft? Can you please give us some more information (your problem is a bit vague)?

---

### Post by buckrodgers on 2006-12-22
try this:
```

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-old
sudo gedit /var/lib/dpkg/status #look for the broken package and remove that package.
sudo rm /var/cache/apt/*.bin
sudo apt-get upgrade
sudo apt-get -f install

```

---

