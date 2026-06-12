---
title: "Issue updating"
date: 2015-10-13
forum: General Help
---

### Post by marlee2 on 2015-10-13
So recently started using my laptop with Ubuntu again and wanted to  update it however got an error message when trying to update...

```
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```

Since the obvious would be to remove steam I tried sudo apt-get purge steam and got the same error. Any help?

---

### Post by slickymaster on 2015-10-13
Hi marlee2, welcome to the forums.

Please try these commands at a terminal window (Ctrl+Alt+T):```
sudo rm /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```

---

