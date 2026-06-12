---
title: "software center error on startup"
date: 2012-11-01
forum: General Help
---

### Post by kurja on 2012-11-01
when I launch ubuntu software center, it says that it "closed unexpectedly" when in fact it's up and running, I just dismiss the error and it works... weird. In terminal, I get ```
-desktop:~$ software-center
2012-11-01 20:05:16,252 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-11-01 20:05:16,261 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-11-01 20:05:16,378 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2012-11-01 20:05:17,148 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-11-01 20:05:17,566 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-11-01 20:05:17,745 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/rnr.py", line 183, in _on_review_stats_data
    self.save_review_stats_cache_file()
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 315, in save_review_stats_cache_file
    t.run()
  File "/usr/lib/python2.7/threading.py", line 504, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 326, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 357, in _dump_bsddbm_for_unity
    flags=bdb.DB_CREATE)
MemoryError: (12, 'Cannot allocate memory -- Lock table is out of available locker entries')
2012-11-01 20:05:29,992 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2012-11-01 20:05:35,518 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 0
2012-11-01 20:05:35,519 - softwarecenter.db.database - INFO - reopen() database
2012-11-01 20:05:35,519 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True


```

running latest lts version of ubuntu.

---

### Post by Bashing-om on 2012-11-01
hi ! kurja;

Here is my full output (12.04.1 version):
```

 sudo software-center
[sudo] password for sysop1: 
2012-11-01 16:23:32,263 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-11-01 16:23:32,299 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-11-01 16:23:32,806 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-11-01 16:23:33,026 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-11-01 16:23:33,031 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

```Noting several differences...problems with dependents ?? geo clue ? init _,py ? memory allocation ???

my thoughts are to re-install software -center and see if the errors remain. . Suggest re-install from terminal and watch for errors generated.[INDENT]hth <==BDQ

[/INDENT]

---

### Post by Henne91 on 2012-11-30
Having the same problem. I think it's the same bug as [https://bugs.launchpad.net/software-center/+bug/1054070](https://bugs.launchpad.net/software-center/+bug/1054070). Seems to be a regression.

---

