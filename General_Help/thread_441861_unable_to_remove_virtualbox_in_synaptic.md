---
title: "unable to remove virtualbox in synaptic"
date: 2007-05-13
forum: General Help
---

### Post by booljayj on 2007-05-13
I recently installed VirtualBox forceably onto my AMD64 computer in order to test out its capabilities. I didn't like it, and so tried to uninstall it. Unfortunately, there is no 'virtualbox' package that shows up in synaptic. The program is installed, I can still run it, but it seems as if I would have to hunt down every last file in order to completely remove it. Is there any reason why it would not show up in synaptic?

---

### Post by taurus on 2007-05-13
What happens if you remove it from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude --purge remove virtualbox
```

---

### Post by booljayj on 2007-05-13
Removing using a terminal does nothing new, it still insists that the package does not exist. The weird thing is that I had to install and remove VirtualBox a few times to get the installation right, and this is the only time it has done this. Maybe feisty is just confused?

---

