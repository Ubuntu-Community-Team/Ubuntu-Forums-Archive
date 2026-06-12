---
title: "mozilla-mplayer some symlinks broken"
date: 2007-01-20
forum: General Help
---

### Post by TrinitronX on 2007-01-20
I have recently upgraded to edgy, and was having slight troubles with the mplayer plugin in firefox, so I decided to remove the package and reinstall it.  As far as I know it fixed things, but there are 2 broken symlinks in /usr/lib/firefox/plugins that I'm wondering about.
I have removed the package again and have seen that they are removed, and when reinstalled, they come back... still broken.
They are:
```
lrwxrwxrwx 1 root root      43 2007-01-20 03:31 mplayerplug-in-gmp.so -> ../../mozilla/plugins/mplayerplug-in-gmp.so
lrwxrwxrwx 1 root root      44 2007-01-20 03:31 mplayerplug-in-gmp.xpt -> ../../mozilla/plugins/mplayerplug-in-gmp.xpt
```

They link to nonexistent files in /usr/lib/mozilla/plugins.
Just pointing it out in case this breaks support for some type of file in mplayer.  I'm not sure what the gmp suffix is for though, all the others like rm=real media, wmp=windows media player, etc... are all there, and seem to work.

Using package version: 3.31-1

---

