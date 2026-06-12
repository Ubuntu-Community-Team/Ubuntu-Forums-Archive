---
title: "Problem getting wget to exclude certain directories"
date: 2006-08-21
forum: General Help
---

### Post by jamadagni on 2006-08-21
For some reasons, I need to download the KDE 3.5.4 updates for Kubuntu manually. So I am using

```
wget --recursive --tries=inf --level=inf -nH --cut-dirs=7 --exclude-directories=``arts/'',``extra/'',``kde-i18n/'' --accept ``*i386.deb'',``*all.deb'' --reject ``*-dev*.deb'',``*-dbg*.deb'' -np -N ftp://ibiblio.org/pub/mirrors/kde/stable/3.5.4/kubuntu/pool-dapper/
```

Now this does not exclude the arts, extra (already downloaded) and kde-i18n (not needed) directory as it is supposed to. Or am I doing something wrong with the command?

Thanks.

---

