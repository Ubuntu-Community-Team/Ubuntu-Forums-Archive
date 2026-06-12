---
title: "clean up?"
date: 2007-05-27
forum: General Help
---

### Post by ZiVvmO on 2007-05-27
is there an easy (or even not easy) way to find installed packages that are not being used.  or find packages that were installed as a dependency but the program it needed is no longer installed?

basically, how do i get rid of junk i dont use/need?

---

### Post by drs305 on 2007-05-27
Open synaptic. If you select Status In the left pane, you get a list of options. Two are Not Installed and Not Installed Residual. That's a start of programs on your drive but not being used. Most if not all the deb files used to install programs are kept in the var/cache/apt/archives directory until you delete them. They are not needed but many people back them up to CD or keep them so they can restore the programs without access to the internet (if needed). However, if you need the space, the deb files in this directory can be safely removed without impacting ubuntu.

You remove them with:
```
apt-get clean
```

You can learn more about this command by typing:
```
man apt-get
```
and looking at the ' clean ' option    >> edited: and autoremove (mentioned below by Znupi)

For more agressive cleaning, also do a search for deborphan

---

### Post by ZiVvmO on 2007-05-27
thanks.  checking it out right now.

---

### Post by Znupi on 2007-05-27
I usually use
```

sudo apt-get autoremove

```

---

