---
title: "Software updater"
date: 2014-07-04
forum: General Help
---

### Post by leopheard on 2014-07-04
Hi all,

I have an issue after running Bleachbit as root (yes I know!), which has caused massive probs with Software Updater. The taskbar now shows an exclamation bar and clicking 'show updates' gives the following note:

Failed to load the package list:

This is serious problem. Try again later. If this problem appears again, please report and error to the developers.

W:Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free amd64 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-amd64_Packages), W:Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free i386 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-i386_Packages), E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%%5fUS, E:The package lists or status file could not be parsed or opened.

If I start package manager, is states:

An error occurred
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_i18n_Translation-en%5fUS
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free amd64 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free i386 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-i386_Packages)

Any ideas anyone?

---

### Post by leopheard on 2014-07-04
Sorry all, this I've just solved it, thread here:

[http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)

---

