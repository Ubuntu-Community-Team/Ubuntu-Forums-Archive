---
title: "Ubuntu Software Center broken"
date: 2015-04-19
forum: General Help
---

### Post by orrinevergreen on 2015-04-19
New to Xubuntu. Entering codes I found online, I seemed to have messed up Software Center. I've tried uninstalling then reinstalling from Terminal, but no success. The window opens up, then suddenly vanishes. If I try opening it from the terminal by entering "software-center" I end up getting the following terminal Message:

```
* (software-center:3948): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-dXDPyECnuG: Connection refused
2015-04-19 16:18:27,851 - softwarecenter.backend.zeitgeist_logger - WARNING - Support for Zeitgeist disabled
2015-04-19 16:18:27,894 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-04-19 16:18:27,916 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2015-04-19 16:18:27,915 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
2015-04-19 16:18:28,555 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-04-19 16:18:28,557 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-04-19 16:18:28,619 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-04-19 16:18:29,297 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-04-19 16:18:29,297 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:560: Warning: Source ID 61 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 261, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 155, in open
    self._list.read_main_list()
SystemError: E:Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
2015-04-19 16:18:30,378 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 281, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
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
AttributeError: 'NoneType' object has no attribute '__contains__'
```

---

### Post by QIII on 2015-04-19
It would be very helpful if we knew which commands (not "codes") you issued and where you got them.

Otherwise we can't possibly begin to understand the current state of your machine.

---

### Post by orrinevergreen on 2015-04-20
I honestly don't even remember. In fact, now that I think of it, I may have entered those commands on a different machine,,, so maybe I was confused. Not sure what to do about this.

---

### Post by deadflowr on 2015-04-20
> **orrinevergreen said:**
> I honestly don't even remember. In fact, now that I think of it, I may have entered those commands on a different machine,,, so maybe I was confused. Not sure what to do about this.

Luckily all your terminal commands should be saved in a file called .bash_history in your home folder.
The file is hidden by default (that is what the dot in front does, it marks files as hidden. To unhide press ctrl +H)

You can also get a quick list directly from the terminal by running the command
```
history
```

---

### Post by orrinevergreen on 2015-04-20
Ok, thank you so much.

Here is my terminal history, without the commands that I know weren't involved. I think it may have been after entering something to do with medibuntu (which doesn't exist anymore?). I won't try to explain why, just that I feel stupid now for entering commands and not researching them adequately first.

```

 
    7  /usr/local
    8  /bin
    9  chrome://browser
   10  sudo apt-get update
   11  sudo apt-get install pavucontrol
   12  sudo alsa force-reload
   13  sudo apt-get install libdvdread4
   14  sudo /usr/share/doc/libdvdread4/install-css.sh
   15  gconf-editor
   16  sudo apt-get install gconf-editor
   17  gconf-editor
   18  sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list [http://www.medi](http://www.medi)
   19  sudo apt-get --yet --quiet --allow-unauthenticated install medibuntu-keyring
   20  sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
   21  sudo apt-get --quiet update && sudo apt-get -y upgrade
   22  sudo update-apt-xapian-index
   23  sudo apt-get -y install w64codecs ubuntu-restricted-extras
   24  sudo apt-get -y install curl
   25  curl [ftp://ftp.videolan.org/pub/debian/videolan-apt.asc](ftp://ftp.videolan.org/pub/debian/videolan-apt.asc) | sudo apt-key add -
   26  echo "deb [ftp://ftp.videolan.org/pub/debian/stable](ftp://ftp.videolan.org/pub/debian/stable) ./" | sudo tee /etc/apt/sources.list.d/libdvdcss.list && sudo apt-get update
   27  curl [ftp://ftp.videolan.org/pub/debian/videolan-apt.asc](ftp://ftp.videolan.org/pub/debian/videolan-apt.asc) | sudo apt-key add -
   28  echo "deb [ftp://ftp.videolan.org/pub/debian/stable](ftp://ftp.videolan.org/pub/debian/stable) ./" | sudo tee /etc/apt/sources.list.d/libdvdcss.list && sudo apt-get update
   29  sudo apt-get install gstreamer-.10-ffmpeg gstreamer0.10-plugins-ugly gstreamer0.10
```

---

### Post by deadflowr on 2015-04-20
Open the Program Software and Updates.
Go to Other Software and REMOVE the entries for libdvdcss/videolan( whatever it says). And any entry for medibuntu.

Then re-run the sudo apt-get update and sudo apt-get upgrade commands.
See if that helps...

Sidenote: The libdvdcss installation script was updated some time ago, so no need to add a ppa for it.
When you run the upgrade command, if any new version of the script is available, then you will get that script.
The script then downloads the libdvdcss package and installs it from the videolan repo(?)(I do not know what they call it over there)
However, only the libdvdcss package is hosted on videolan, so the other medibuntu packages are scattered elsewhere throughout the web, now.

---

### Post by slickymaster on 2015-04-20
_@orrinevergreen:_
Please don't use QUOTE tags when pasting code into a thread because it may lose its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. Use [CODE tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") instead, which make the post clean, compact and more appealing, thus getting more attention from readers

---

### Post by matt_symes on 2015-04-20
Hi

Purging and reinstalling software-center from the terminal has fixed this error for other people. 

May be a quick fix for you as well.
```

sudo apt-get purge software-center
sudo apt-get install software-center
```

Kind regards

---

### Post by orrinevergreen on 2015-04-20
I tried deleting the intro for vlan. I didn't see one for medibuntu. 

After entering "sudo apt-get update," I received the following terminal message:

```
E: Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
```

Then I entered "sudo apt-get upgrade" 
and then "sudo apt-get dist-upgrade"

My problem remains.

---

### Post by orrinevergreen on 2015-04-20
I also tried purging and reinstalling, no success. Software Center used to open then close quickly. But now, it doesn't show anything at all.

---

### Post by matt_symes on 2015-04-20
Hi

Open a terminal and type

```
sudo mv /etc/apt/sources.list.d/medibuntu.list{,.broken}
```

Then type

```
sudo apt-get update
```

If that returns no errors, try opening the software center from the terminal again.

Post back any errors.

Kind regards

---

### Post by orrinevergreen on 2015-04-20
It opens, and then immediately closes. I guess that's an improvement.... sorta' 
After entering sudo apt-get update, I didn't notice any actual error messages, although it did end with the following:

```

N: Ignoring file 'medibuntu.list.broken' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension

```

---

### Post by matt_symes on 2015-04-21
Hi

That last error message should not be a problem. It just means that it will ignore the file.

Clean the cache and update again

```
sudo rm -r /var/lib/apt/lists/*
sudo apt-get update
```

After that, try purging and reinstalling the software center again
```

sudo apt-get purge software-center
sudo apt-get install software-center
```

Then open it from the terminal again

```
software-center
```

and post back the stack trace if software-center crashes.

Kind regards

---

### Post by orrinevergreen on 2015-04-21
Works now!
Thank you so much Matt (and other friendly folks)

May great things come your way!

---

