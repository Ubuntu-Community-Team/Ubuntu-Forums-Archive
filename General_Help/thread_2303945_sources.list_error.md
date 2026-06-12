---
title: "sources.list error"
date: 2015-11-23
forum: General Help
---

### Post by ben185 on 2015-11-23
[COLOR=#000000][FONT=Consolas]An error occurred, please run Package Manager from the right-clicked menu or apt-get in a terminal to see what is wrong.
the error message was:'Unkown Error:'<class'SystemError'>'(E:Opening /etc/apt/sources.list.d/nodesource.list-ifstrean::ifstream(13: Permissions denied))'. 
this ususaly means that your installed packages have unmet dependencies

How do I solve this?[/FONT][/COLOR]

---

### Post by v3.xx on 2015-11-23
Please post your sources.list.d

```
ls /etc/apt/sources.list.d/*.list
```

---

### Post by Bucky Ball on 2015-11-23
Welcome. What command were you using? Perhaps you didn't put 'sudo' first which is why you have no permissions.

Run the command again, but use sudo. For instance:

```
sudo apt-get update
```

This doesn't change the fact you appear to have unmet dependencies. What happens when you:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by ben185 on 2015-11-23
/etc/apt/sources.list.d/chris-lea-node_js-trusty.list
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/google-talkplugin.list
/etc/apt/sources.list.d/mongodb-org-3.0.list
/etc/apt/sources.list.d/nodesource.list
/etc/apt/sources.list.d/steam.list
/etc/apt/sources.list.d/virtualbox.list
/etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list


@Bucky Ball
dist-upgrade doesn't fix the error

---

### Post by ben185 on 2015-11-23
I am only able to run ubuntu software center as root
sudo software-center.

Otherwise it opens, tries to load, and crashes.

Any way I can make it work from clicking the icon as it was before?

---

### Post by matt_symes on 2015-11-23
Hi

> **ben185 said:**
> I am only able to run ubuntu software center as root
sudo software-center.

Otherwise it opens, tries to load, and crashes.

Any way I can make it work from clicking the icon as it was before?

Don't use *sudo* to run graphical applications. It can mess up permissions in your home folder as those files become owned by root. Use *pkexec* to gain elevated privileges. Elevated privileges used to be granted by *gksudo* but this is being deprecated in Ubuntu.

[https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

Start **software-center** from the terminal under your user and post the terminal output back here. That may give some clues as to what is happening.

**EDIT:**

If you start software-center from the command line using the command below, does it crash ?

```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY software-center
```

Kind regards

---

### Post by deadflowr on 2015-11-23
Disable and remove the nodesource repo.
Then try re-adding it again.
If it fails a second time, then remove it completely.

Preferably open the program called Software and Updates go to the tab marked other software, find the nodesource entries and click the check box to uncheck and disable  and then click the remove to remove.
The system will ask for your password when you do this.
when done pressing the close button should open a dialog asking if you want to reload or not.
If you want to re-run the update command manually, you can simply close it without selecting the reload option. No harm.

---

### Post by ben185 on 2015-11-23
```

2015-11-23 16:03:24,722 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-11-23 16:03:25,007 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-11-23 16:03:25,008 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-11-23 16:03:25,037 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-11-23 16:03:25,283 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-11-23 16:03:25,284 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 68 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 261, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 155, in open
    self._list.read_main_list()
SystemError: E:Opening /etc/apt/sources.list.d/mongodb-org-3.0.list - ifstream::ifstream (13: Permission denied)
No bp log location saved, using default.
[000:000] Cpu: 6.60.3, x8, 3400Mhz, 11948MB
[000:001] Computer model: Not available
[000:001] Browser XEmbed support present: 1
[000:001] Browser toolkit is Gtk2.
[000:002] Using Gtk2 toolkit
[000:003] Warning(optionsfile.cc:30): Load: Could not open file, err=2
[000:003] No bp log location saved, using default.
[000:003] Cpu: 6.60.3, x8, 3400Mhz, 11948MB
[000:004] Computer model: Not available
[000:004] Browser XEmbed support present: 1
[000:004] Browser toolkit is Gtk2.
[000:004] Using Gtk2 toolkit
No bp log location saved, using default.
[000:000] Cpu: 6.60.3, x8, 3400Mhz, 11948MB
[000:000] Computer model: Not available
[000:016] Warning(optionsfile.cc:30): Load: Could not open file, err=2
[000:016] No bp log location saved, using default.
[000:017] Cpu: 6.60.3, x8, 3400Mhz, 11948MB
[000:017] Computer model: Not available
2015-11-23 16:03:25,698 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 281, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
java version "1.7.0_85"
OpenJDK Runtime Environment (IcedTea 2.6.1) (7u85-2.6.1-5ubuntu0.14.04.1)
OpenJDK 64-Bit Server VM (build 24.85-b03, mixed mode)
Traceback (most recent call last):
  File "/usr/bin/software-center", line 183, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1378, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1316, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 150, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 227, in init_view
    self.cache, self.db, self.icons, self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 80, in __init__
    self.build()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 326, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 121, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 255, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 240, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 131, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 330, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 225, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 281, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'[]
```


It doesn't crash using that command:

```
pkexec env DISPLAY=$DISPLAY XAUTHORITY=$XAUTHORITY software-center
```

---

### Post by ben185 on 2015-11-23
I dont see the repo in Software and Updates

---

### Post by matt_symes on 2015-11-23
Hi

What version of Ubuntu are you using ? Can you post the output of the command below please.

```
cat /etc/lsb-release
```

**EDIT**

You have at least one permissions error.

> SystemError: E:Opening /etc/apt/sources.list.d/mongodb-org-3.0.list - ifstream::ifstream (13: Permission denied)

Can you post the output of 

```
ls -l /etc/apt/sources.list.d/
```

Kind regards

---

### Post by deadflowr on 2015-11-23
Odd.
How'd you add the repo in the first place?

---

### Post by matt_symes on 2015-11-23
Hi

> Unkown Error:'<class'SystemError'>'(E:Opening /etc/apt/sources.list.d/nodesource.list-ifstrean::ifstream(13: Permissions denied))

Check the permissions of your sources just in case. Please post the output of

```
ls -l /etc/apt/sources.list.d/
```

Kind regards

---

### Post by ben185 on 2015-11-23
Not sure...

```
-rw-r--r-- 1 root root   0 Nov 22 18:25 chris-lea-node_js-trusty.list
-rw-r--r-- 1 root root   0 Nov 22 18:25 chris-lea-node_js-trusty.list.save
-rw-r--r-- 1 root root 176 Nov 23 01:05 google-chrome.list
-rw-r--r-- 1 root root 176 Nov 23 01:05 google-chrome.list.save
-rw-r--r-- 1 root root 180 Nov 23 01:05 google-talkplugin.list
-rw-r--r-- 1 root root 180 Nov 23 01:05 google-talkplugin.list.save
-rw-r----- 1 root root  73 Nov 23 02:09 mongodb-org-3.0.list
-rw-r----- 1 root root 108 Nov 23 01:05 nodesource.list
-rw-r----- 1 root root 108 Nov 23 01:05 nodesource.list.save
-rw-r--r-- 1 root root 148 Nov 23 01:05 steam.list
-rw-r--r-- 1 root root 148 Nov 23 01:05 steam.list.save
-rw-r--r-- 1 root root 136 Nov 23 01:05 virtualbox.list
-rw-r--r-- 1 root root 136 Nov 23 01:05 virtualbox.list.save
-rw-r--r-- 1 root root 134 Nov 23 01:05 xorg-edgers-ppa-trusty.list
-rw-r--r-- 1 root root 134 Nov 23 01:05 xorg-edgers-ppa-trusty.list.save
```

---

### Post by ben185 on 2015-11-23
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.3 LTS"

[COLOR=#000000]-rw-r--r-- 1 root root 0 Nov 22 18:25 chris-lea-node_js-trusty.list[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 0 Nov 22 18:25 chris-lea-node_js-trusty.list.save[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 176 Nov 23 01:05 google-chrome.list[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 176 Nov 23 01:05 google-chrome.list.save[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 180 Nov 23 01:05 google-talkplugin.list[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 180 Nov 23 01:05 google-talkplugin.list.save[/COLOR]
[COLOR=#000000]-rw-r----- 1 root root 73 Nov 23 02:09 mongodb-org-3.0.list[/COLOR]
[COLOR=#000000]-rw-r----- 1 root root 108 Nov 23 01:05 nodesource.list[/COLOR]
[COLOR=#000000]-rw-r----- 1 root root 108 Nov 23 01:05 nodesource.list.save[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 148 Nov 23 01:05 steam.list[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 148 Nov 23 01:05 steam.list.save[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 136 Nov 23 01:05 virtualbox.list[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 136 Nov 23 01:05 virtualbox.list.save[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 134 Nov 23 01:05 xorg-edgers-ppa-trusty.list[/COLOR]
[COLOR=#000000]-rw-r--r-- 1 root root 134 Nov 23 01:05 xorg-edgers-ppa-trusty.list.save[/COLOR]
```

---

### Post by matt_symes on 2015-11-23
Hi

Try this..

```
cd /etc/apt/sources.list.d/ && sudo chmod 644 mongodb-org-3.0.list nodesource.list nodesource.list.save
```

Then try to run the package manager again.

Any joy ?

Kind regards

---

### Post by matt_symes on 2015-11-23
Hi

Try this from the terminal.

```
cd /etc/apt/sources.list.d/ && sudo chmod 644 mongodb-org-3.0.list nodesource.list nodesource.list.save
```

Then try the package manager from the terminal again under your user. If it crashes then post its terminal output.

**EDIT:**

I've just merged the two threads you created.

Please only create one thread for each problem. It dilutes community effort and creates work for staff.

Kind regards

---

### Post by ben185 on 2015-11-23
I see them in package manager now.

---

### Post by matt_symes on 2015-11-23
Hi

> **ben185 said:**
> I see them in package manager now.

Then your package manager is no longer crashing ? You can install software again ?

If so then would you please mark this thread as [SOLVED] using the thread tools link at the top of the page. It helps others with similar problems search for solutions.

Kind regards

---

