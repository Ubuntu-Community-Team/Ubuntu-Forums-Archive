---
title: "Ubuntu Software Center doesn't open"
date: 2015-01-03
forum: General Help
---

### Post by Urbanmasque on 2015-01-03
Everytime I try to open it - the window opens and then immediately closes.  The same happens when I attempt to "show details" on the crash so that I can post the results here.  I've restarted a few times, but I still have the same issue.  Any ideas, or links to where I should start looking?

Thanks in advance!

---

### Post by bapoumba on 2015-01-03
Which version of Ubuntu are you running ?
What do return the following commands :
```
apt-cache policy software-center
software-center
```
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ajgreeny on 2015-01-03
Start in terminal with command **software-center** and see if you get any helpful errors.

---

### Post by Urbanmasque on 2015-01-04
> **bapoumba said:**
> Which version of Ubuntu are you running ?
What do return the following commands :
```
apt-cache policy software-center
software-center
```

```

software-center:
  Installed: 13.10-0ubuntu4.1
  Candidate: 13.10-0ubuntu4.1
  Version table:
 *** 13.10-0ubuntu4.1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     13.10-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```

> **bapoumba said:**
> 
```
sudo apt-get update
sudo apt-get upgrade
```
Done. ..a bunch of updates  unpacked. and now it works!  Thanks for the suggestion!.. but I feel  foolish for not trying this first :(

> **ajgreeny said:**
> Start in terminal with command **software-center** and see if you get any helpful errors.
```
2015-01-04 11:16:41,309 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-01-04 11:16:41,831 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-01-04 11:16:41,833 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-01-04 11:16:41,866 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-01-04 11:16:42,095 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-01-04 11:16:42,095 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 74 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
No bp log location saved, using default.
[000:000] Cpu: 6.60.3, x8, 3101Mhz, 3907MB
[000:000] Computer model: Not available
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:002] Using Gtk2 toolkit
[000:003] Warning(optionsfile.cc:30): Load: Could not open file, err=2
[000:003] No bp log location saved, using default.
[000:003] Cpu: 6.60.3, x8, 3101Mhz, 3907MB
[000:003] Computer model: Not available
[000:003] Browser XEmbed support present: 1
[000:003] Browser toolkit is Gtk2.
[000:003] Using Gtk2 toolkit
No bp log location saved, using default.
[000:000] Cpu: 6.60.3, x8, 3101Mhz, 3907MB
[000:000] Computer model: Not available
[000:004] Warning(optionsfile.cc:30): Load: Could not open file, err=2
[000:004] No bp log location saved, using default.
[000:005] Cpu: 6.60.3, x8, 3101Mhz, 3907MB
[000:005] Computer model: Not available
2015-01-04 11:16:43,101 - softwarecenter.ui.gtk3.views.lobbyview - WARNING - skipping exhibit for: 'u'leadwerks\r\nleadwerks-indie'' not available
/usr/bin/software-center:184: Warning: Source ID 159 was not found when attempting to remove it
  Gtk.main()
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 20 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
2015-01-04 11:16:47,833 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
```

This help?  It works now, but I still see some error messages.

Thanks for your help on this guys/gals!

---

### Post by bapoumba on 2015-01-05
I have looked around but cannot really test or see as some of these files I do not have, for ex anything in /usr/share/software-center (not present here on my system). May be try purging and reinstalling the Software Center ? Some threads here and there usually suggest it :
```
sudo apt-get remove --purge software-center
sudo apt-get install software-center
```

---

