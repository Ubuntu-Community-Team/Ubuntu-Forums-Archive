---
title: "[SOLVED] No sound WINE Feisty Audigy 2 Value"
date: 2007-12-10
forum: General Help
---

### Post by stchman on 2007-12-10
Hello all.

I have WINE installed.  Recently WINE was updated and I lost sound while running Windows apps under WINE.

I have an Audigy 2 Value card under Feisty.

Has anyone else had this problem?  Sound used to work fine.

Thanks.

---

### Post by stchman on 2007-12-11
I solved the problem.

I completely uninstalled WINE

```
sudo apt-get -y autoremove wine
```

I then removed all the residual config files and deleted the ~/.wine folder.

I then reinstalled WINE and all was good again.

---

