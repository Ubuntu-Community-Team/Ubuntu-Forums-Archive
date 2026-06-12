---
title: "APT-GET and Synaptic problems"
date: 2008-06-18
forum: General Help
---

### Post by Megacherv on 2008-06-18
I REALLY need help with this one. I recently got rid of KDE from my system (alot slower than GNOME), and I was marking all the programs for removal. Part way through, it failed to delete 'kio-unmountwrapper', and the whole uninstallation stopped. Now, I can't install or uninstall anything, not even updates. I've tried both synaptic, and I even learnt the basics of how to use apt and that didn't work either. Please, as I said, I REALLY need help with this.

---

### Post by robert.cooper on 2008-06-18
you can log into gnome, right? what is the output from an apt-get cmd?

---

### Post by Megacherv on 2008-06-19
I have no idea what that means. The problem is that it can't remove kio_unmountwrapper because it's not on the PC any longer, and I can't install it for it to be uninstalled because it does the uninstalls first.

---

### Post by forestpixie on 2008-06-19
It means to open a terminal in gnome - which you can boot and run an apt-get command like

```
sudo apt-get update
```

---

### Post by Megacherv on 2008-06-19
That command doesn't solve anything. It still tries to remove kio-unmountwrapper.

---

### Post by russlar on 2008-06-19
> **Megacherv said:**
> That command doesn't solve anything. It still tries to remove kio-unmountwrapper.

try these:

```
sudo apt-get purge
sudo apt-get autoremove
sudo apt-get remove -f

```

---

### Post by Megacherv on 2008-06-19
Thanks for them. I'll try those later since I've switched over to my Windows partition.

---

