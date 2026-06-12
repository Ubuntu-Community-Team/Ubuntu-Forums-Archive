---
title: "can't open software center nor download updates"
date: 2015-09-12
forum: General Help
---

### Post by markulin-zagreb on 2015-09-12
Dear sir,
this is what I get when trying to open software-center:
Please help,
Regards

```
emgejac@emgejac:~$ gksudo software-center
2015-09-12 22:46:37,491 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2015-09-12 22:46:37,492 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2015-09-12 22:46:37,538 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2015-09-12 22:46:38,598 - softwarecenter.backend.reviews - WARNING - error creating bsddb: '(22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')' (corrupted?)
2015-09-12 22:46:38,598 - softwarecenter.backend.reviews - ERROR - trying to repair DB failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 358, in _save_review_stats_cache_blocking
    self._dump_bsddbm_for_unity(outfile, outdir)
  File "/usr/share/software-center/softwarecenter/backend/reviews/__init__.py", line 377, in _dump_bsddbm_for_unity
    0600)
DBInvalidArgError: (22, 'Invalid argument -- BDB0054 illegal flag combination specified to DB_ENV->open')
/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py:535: Warning: Source ID 67 was not found when attempting to remove it
  return super(MainContext, self).iteration(may_block)
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 261, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 107, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 151, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
2015-09-12 22:46:39,609 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
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
emgejac@emgejac:~$
```

---

### Post by deadflowr on 2015-09-12
Open a terminal and run
```
sudo apt-get update
```
and post the results.

Please use code tags in you reply
excellent code tags primer here:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by markulin-zagreb on 2015-09-12
Thanks for prompt reply! Heres what I get:
```

emgejac@emgejac:~$ sudo apt-get update
[sudo] password for emgejac: 
Hit http://repo.steampowered.com precise InRelease
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://repo.steampowered.com precise/steam Sources                         
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Ign http://archive.canonical.com trusty InRelease                              
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty Release                                
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://security.ubuntu.com trusty-security InRelease                       
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:2 http://security.ubuntu.com trusty-security Release [63,5 kB]             
Ign http://us.archive.ubuntu.com trusty-security InRelease                     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://us.archive.ubuntu.com trusty-proposed InRelease                     
Ign https://private-ppa.launchpad.net trusty InRelease                         
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit https://private-ppa.launchpad.net trusty Release.gpg
Get:3 http://security.ubuntu.com trusty-security/restricted i386 Packages [8846 B]
Get:4 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]          
Get:5 http://us.archive.ubuntu.com trusty-security Release.gpg [933 B]         
Get:6 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3830 B]
Hit https://private-ppa.launchpad.net trusty Release                           
Get:7 http://security.ubuntu.com trusty-security/main i386 Packages [327 kB]   
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                
Get:8 http://us.archive.ubuntu.com trusty-proposed Release.gpg [933 B]       
Hit http://us.archive.ubuntu.com trusty Release                                
Hit https://private-ppa.launchpad.net trusty/main i386 Packages                
Get:9 http://us.archive.ubuntu.com trusty-updates Release [63,5 kB]            
Get:10 http://us.archive.ubuntu.com trusty-security Release [63,5 kB]          
Get:11 http://security.ubuntu.com trusty-security/universe i386 Packages [116 kB]
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Get:12 http://security.ubuntu.com trusty-security/main Translation-en [187 kB] 
Get:13 http://us.archive.ubuntu.com trusty-proposed Release [211 kB]
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Get:14 http://security.ubuntu.com trusty-security/universe Translation-en [67,8 kB]
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US      
Hit http://us.archive.ubuntu.com trusty/restricted Sources
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Ign https://private-ppa.launchpad.net trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/main Sources
Hit http://us.archive.ubuntu.com trusty/universe Sources
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:15 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4725 B] 
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5143 B] 
Get:17 http://us.archive.ubuntu.com trusty-updates/main Sources [234 kB]       
Get:18 http://us.archive.ubuntu.com trusty-updates/universe Sources [135 kB]   
Get:19 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15,1 kB]
Get:20 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [601 kB] 
Get:21 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [313 kB]
Get:22 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12,1 kB]
Get:23 http://us.archive.ubuntu.com trusty-updates/main Translation-en [300 kB]
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Get:24 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [166 kB]
Get:25 http://us.archive.ubuntu.com trusty-security/restricted Sources [2061 B]
Get:26 http://us.archive.ubuntu.com trusty-security/multiverse Sources [2330 B]
Get:27 http://us.archive.ubuntu.com trusty-security/main Sources [94,1 kB]     
Get:28 http://us.archive.ubuntu.com trusty-security/universe Sources [30,5 kB] 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:29 http://us.archive.ubuntu.com trusty-proposed/restricted Sources [28 B]  
Get:30 http://us.archive.ubuntu.com trusty-proposed/multiverse Sources [28 B]  
Get:31 http://us.archive.ubuntu.com trusty-proposed/main Sources [131 kB]      
Get:32 http://us.archive.ubuntu.com trusty-proposed/universe Sources [25,4 kB] 
Get:33 http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Get:34 http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:35 http://us.archive.ubuntu.com trusty-proposed/main i386 Packages [126 kB]
Get:36 http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages [27,6 kB]
Get:37 http://us.archive.ubuntu.com trusty-proposed/main Translation-en [49,2 kB]
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en     
Get:38 http://us.archive.ubuntu.com trusty-proposed/universe Translation-en [19,9 kB]
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 3409 kB in 20s (164 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
emgejac@emgejac:~$

```

---

### Post by deadflowr on 2015-09-12
Try
```
sudo rm -rf /var/lib/apt/list/*
```
then re run the update command, and see if this helps.
It normally will.
If it returns without errors at the end, you can try running an an updater, or run the updates  with the command
```
sudo apt-get upgrade
```
hope it helps

---

### Post by markulin-zagreb on 2015-09-12
Unfortuately, it didn't solve the problem:
```

emgejac@emgejac:~$ sudo rm -rf /var/lib/apt/list/*
emgejac@emgejac:~$ sudo apt-get update
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://archive.canonical.com trusty InRelease                              
Ign http://extras.ubuntu.com trusty InRelease                                  
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]           
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Get:2 http://security.ubuntu.com trusty-security Release [63,5 kB]             
Hit http://archive.canonical.com trusty Release                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://archive.canonical.com trusty/partner Sources                        
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:3 http://archive.canonical.com trusty/partner Translation-en [4588 B]      
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:4 http://security.ubuntu.com trusty-security/restricted i386 Packages [8846 B]
Ign http://us.archive.ubuntu.com trusty InRelease                              
Get:5 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3830 B]
Hit http://ppa.launchpad.net trusty Release.gpg                                
Get:6 http://security.ubuntu.com trusty-security/main i386 Packages [327 kB]   
Hit http://repo.steampowered.com precise InRelease                             
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://us.archive.ubuntu.com trusty-security InRelease                     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://us.archive.ubuntu.com trusty-backports InRelease                    
Get:7 http://security.ubuntu.com trusty-security/universe i386 Packages [116 kB]
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign https://private-ppa.launchpad.net trusty InRelease                         
Ign http://us.archive.ubuntu.com trusty-proposed InRelease                     
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit https://private-ppa.launchpad.net trusty Release.gpg                
Get:8 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Get:9 http://us.archive.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://repo.steampowered.com precise/steam amd64 Packages
Hit https://private-ppa.launchpad.net trusty Release             
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg          
Get:10 http://us.archive.ubuntu.com trusty-proposed Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty Release             
Hit https://private-ppa.launchpad.net trusty/main i386 Packages        
Hit http://repo.steampowered.com precise/steam i386 Packages           
Get:11 http://us.archive.ubuntu.com trusty-updates Release [63,5 kB]
Get:12 http://us.archive.ubuntu.com trusty-security Release [63,5 kB]     
Hit http://us.archive.ubuntu.com trusty-backports Release
Get:13 http://us.archive.ubuntu.com trusty-proposed Release [211 kB]   
Hit http://us.archive.ubuntu.com trusty/restricted Sources               
Hit http://us.archive.ubuntu.com trusty/multiverse Sources
Hit http://us.archive.ubuntu.com trusty/main Sources             
Hit http://us.archive.ubuntu.com trusty/universe Sources          
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages  
Hit http://us.archive.ubuntu.com trusty/main i386 Packages        
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages    
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages  
Ign https://private-ppa.launchpad.net trusty/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty/main Translation-en       
Ign https://private-ppa.launchpad.net trusty/main Translation-en  
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en  
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en  
Hit http://us.archive.ubuntu.com trusty/universe Translation-en    
Get:14 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4725 B]
Get:15 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5143 B]
Get:16 http://us.archive.ubuntu.com trusty-updates/main Sources [234 kB]
Ign http://repo.steampowered.com precise/steam Translation-en_US       
Get:17 http://us.archive.ubuntu.com trusty-updates/universe Sources [135 kB]
Ign http://repo.steampowered.com precise/steam Translation-en                  
Get:18 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15,1 kB]
Get:19 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [601 kB]
Get:20 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [313 kB]
Get:21 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12,1 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Get:22 http://us.archive.ubuntu.com trusty-security/restricted Sources [2061 B]
Get:23 http://us.archive.ubuntu.com trusty-security/multiverse Sources [2330 B]
Get:24 http://us.archive.ubuntu.com trusty-security/main Sources [94,1 kB]     
Get:25 http://us.archive.ubuntu.com trusty-security/universe Sources [30,5 kB] 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:26 http://us.archive.ubuntu.com trusty-proposed/restricted Sources [28 B]  
Get:27 http://us.archive.ubuntu.com trusty-proposed/multiverse Sources [28 B]  
Get:28 http://us.archive.ubuntu.com trusty-proposed/main Sources [131 kB]      
Get:29 http://us.archive.ubuntu.com trusty-proposed/universe Sources [25,4 kB] 
Get:30 http://us.archive.ubuntu.com trusty-proposed/restricted i386 Packages [28 B]
Get:31 http://us.archive.ubuntu.com trusty-proposed/multiverse i386 Packages [28 B]
Get:32 http://us.archive.ubuntu.com trusty-proposed/main i386 Packages [126 kB]
Get:33 http://us.archive.ubuntu.com trusty-proposed/universe i386 Packages [27,6 kB]
Hit http://us.archive.ubuntu.com trusty-proposed/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-proposed/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-proposed/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-proposed/universe Translation-en       
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 2624 kB in 14s (184 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
emgejac@emgejac:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
emgejac@emgejac:~$ 

```

---

### Post by deadflowr on 2015-09-13
Can you open Software and Updates?
If so, open it and go to other software and uncheck the steam entry.
Close and let the system reload.

From time to time, as I understand it, the steam ppa has problems and disabling it, (if only briefly; like a couple of days)
will allow you to update the rest of the system, at least.

---

### Post by markulin-zagreb on 2015-09-13
Thanks a lot, it works!
I unchecked   "...steam"  and  "...steam (source code)" , which are the 2 last items in "other software" list.

---

