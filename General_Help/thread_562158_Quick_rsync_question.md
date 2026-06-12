---
title: "Quick rsync question"
date: 2007-09-28
forum: General Help
---

### Post by Bachstelze on 2007-09-28
Hi, people ^^

I have a quick question about the syntax of the .rsync-filter files used by rsync's -F option. I'm currently making a mirror of the Ubuntu archives and when I reach for example the pool/main/k dir :

[ftp://archive.ubuntu.com/ubuntu/pool/main/k/](ftp://archive.ubuntu.com/ubuntu/pool/main/k/)

there's all the kde-i18n-* directories which I do not want to have to download. What should I put in my .rsync-filter and where should I put it if I want to fetch only the kde-i18n-fr dir ? I've managed to do that with *--include="kde-i18n-fr**" --exclude="kde-i18n-*"* but surely there must be a most elegant way.

---

