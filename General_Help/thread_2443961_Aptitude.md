---
title: "Aptitude"
date: 2020-05-22
forum: General Help
---

### Post by yegnal on 2020-05-22
At terminal:  

me@Ubuntu-Home-PC:~$ [B]aptitude search ~icinnamon
[/B]i A cinnamon-control-center                      - configuration applets for the Cinnamon desktop        
i A cinnamon-control-center-data                 - configuration applets for Cinnamon - data files       
i A cinnamon-control-center-goa                  - configuration applets for the Cinnamon desktop - Gnome
i A cinnamon-desktop-data                        - Common files for Cinnamon desktop apps                
i A cinnamon-l10n                                - Translation files for the Cinnamon desktop            
i A cinnamon-screensaver                         - Cinnamon screen saver and locker                      
i A cinnamon-session                             - Cinnamon Session Manager - Minimal runtime            
i A cinnamon-session-common                      - Cinnamon Session Manager - common files               
i A cinnamon-settings-daemon                     - daemon handling the Cinnamon session settings         
i A gir1.2-cinnamondesktop-3.0                   - Introspection data for CinnamonDesktop                
i A libcinnamon-control-center1                  - library used by configuration applets for Cinnamon    
i A libcinnamon-desktop4                         - Cinnamon library for loading .desktop files           
i A libcinnamon-menu-3-0                         - Cinnamon implementation of the freedesktop menu specif
me@Ubuntu-Home-PC:~$ 

So apparently cinnamon is on the system.  

However:
me@Ubuntu-Home-PC:~$ **sudo aptitude remove cinnamon**
Package c**innamon is not installed**, so it will not be removed
Package **cinnamon is not installed**, so it will not be removed
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
or

me@Ubuntu-Home-PC:~$ **sudo aptitude remove cinnamon***
Couldn't find any package whose name or description matched "cinnamon*"
Unable to apply some actions, aborting

Finally:
me@Ubuntu-Home-PC:~$ **sudo aptitude remove ~icinnamon***
The following packages will be REMOVED:  
  cinnamon-control-center cinnamon-control-center-data{u} cinnamon-control-center-goa{u} 
  cinnamon-desktop-data{u} cinnamon-l10n{u} cinnamon-screensaver{u} cinnamon-session 
  cinnamon-session-common{u} cinnamon-settings-daemon{u} gettext{u} gir1.2-cinnamondesktop-3.0 
  gir1.2-cvc-1.0{u} gir1.2-gkbd-3.0{u} gir1.2-xapp-1.0{u} gir1.2-xkl-1.0{u} gist{u} hddtemp{u} 
  hwdata{u} inxi{u} iso-flags-png-320x240{u} libcinnamon-control-center1 libcinnamon-desktop4 
  libcinnamon-menu-3-0 libcpanel-json-xs-perl{u} libcroco3{u} libcscreensaver0{u} libcvc0{u} 
  libmuffin0{u} libxapp1{u} muffin{u} muffin-common{u} python3-psutil{u} python3-setproctitle{u} 
  python3-tinycss{u} python3-xapp{u} python3-xlib{u} ruby-json{u} tree{u} xapps-common{u} 
0 packages upgraded, 0 newly installed, 39 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 58.7 MB will be freed.
Do you want to continue? [Y/n/?] 





Am I interpreting this correctly, that by adding the **~i**, the package name and the **wildcard**, I would be forcing the removal of these items and **should I be removing them** is the big question ?

---

