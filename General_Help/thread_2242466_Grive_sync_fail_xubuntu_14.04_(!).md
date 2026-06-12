---
title: "Grive sync fail xubuntu 14.04 (!)"
date: 2014-09-01
forum: General Help
---

### Post by bluelegend on 2014-09-01
I've been unable to sync my Google Drive directory with grive recently, despite several attempts.

When I try I just get this error message:
exception: boost::filesystem::status: Too many levels of symbolic links: "./drs-plankningar_fingerstyle_mm/dfsprojects"

'dfsprojects' was a symlink in '~' leading to the directory 'gdrive/drs-plankningar_fingerstyle_mm/' (gdrive is the directory in home that I've designated as my Google Drive directory).
I tried removing the symlink 'dfsprojects' and then syncing again, but no luck (+the order of the directories as stated in the error messages looks suspiciously ass backwards(?)).

I've searched for similar threads elsewhere, but no luck + I've got quite some amount of work not synced for a couple of days on the gdrive.
Help much(!) appreciated.
Thank you.

---

