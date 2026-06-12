---
title: "Installation / Uninstallation doesn't work"
date: 2014-01-21
forum: General Help
---

### Post by Martin_Horvath on 2014-01-21
Hi everyone,

when executing sudo apt-get install or similar commands, I'm getting this message: 

```
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 postgresql-client-9.1 : Breaks: postgresql-9.1 (< 9.1.11-1.pgdg12.4+1) but 9.1.10-1.pgdg12.4+1 is to be installed
 postgresql-contrib-9.1 : Depends: postgresql-9.1 (= 9.1.11-1.pgdg12.4+1) but 9.1.10-1.pgdg12.4+1 is to be installed
 synaptic : Depends: libvte9 (>= 1:0.24.0) but it is not going to be installed
            Recommends: rarian-compat but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Ubuntu Software Center and Update Manager doesn't work either - Software center keeps trying to repair, but it is never succesful, apt-get -f install doesn't help (the repairing is cancelled because of those packages). All error messages has something to do with these packages.

Is there something I can do to get it working?

---

### Post by jeanjd63 on 2014-01-21
.

---

