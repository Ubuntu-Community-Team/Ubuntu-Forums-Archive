---
title: "Sudo Nautilus Segmentation Fault"
date: 2008-06-26
forum: General Help
---

### Post by amtur_poet on 2008-06-26
I can no longer open nautilus as root. This is what the output of "sudo nautilus" is:
```
sudo nautilus
Initializing nautilus-share extension
seahorse nautilus module initialized
Initializing nautilus-open-terminal extension
Initializing nautilus-image-converter extension
Segmentation fault

```

I tried removing all the plugins listed, and got this:
```
sudo nautilus
seahorse nautilus module initialized
Segmentation fault

```

Any idea on how to fix this?

---

### Post by manfer on 2008-06-27
I reinstall of nautilus worked just fine for other user with same issue. Look this thread:

[http://ubuntuforums.org/showthread.php?p=5193718#post5193718](http://ubuntuforums.org/showthread.php?p=5193718#post5193718)

---

