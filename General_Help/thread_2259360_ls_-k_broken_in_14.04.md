---
title: "ls -k broken in 14.04"
date: 2015-01-03
forum: General Help
---

### Post by ofnuts on 2015-01-03
Recently upgraded to 14.04 from 12.10. And a couple of old scripts (written on 10.04 IIRC) just broke because "ls -k" returns a size in bytes as if the "-k" was ignored. Is this a known problem?

---

### Post by schragge on 2015-01-03
It's not a bug, it's a feature. Conversely, previous behaviour of ls is considered a bug. From the changelog for coreutils 8.15 (2012-01-06):
> ls's -k option no longer affects how ls -l outputs file sizes. It now affects only the per-directory block counts written by -l, and the sizes written by -s. This is for compatibility with BSD and with POSIX 2008. Because -k is no longer equivalent to --block-size=1KiB, a new long option --kibibyte stands for -k. [bug introduced in coreutils-4.5.4]
For previous behaviour use *ls -l --block-size=1K*

---

### Post by ofnuts on 2015-01-04
Thanks for the explanation. In the meantime I upgraded these scripts (some come from very early in my script writer career) to use stat instead of ls.

---

