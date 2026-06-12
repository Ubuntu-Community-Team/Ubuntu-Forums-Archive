---
title: "Beryl not starting, cant log in. URGeNT"
date: 2007-01-22
forum: General Help
---

### Post by mattmagician on 2007-01-22
whenever i try to log in, excepth through terminal, it says BERYL, then goes to a black screen, then back to my login screen. please help, i need it desperatly.
I just installed Beryl today, and all i can run through is terminal. please help
](*,) ](*,) ](*,)

(ps: I'm using edgy)

---

### Post by evilghost on 2007-01-22
```

sudo dpkg -l|grep -i beryl
sudo dpkg --purge [name of listed package] [name of next package] [name of next package] [etc etc]

```

Example:

```

luser@ids-m8cj4:~$ sudo dpkg -l|grep -i beryl
Password:
ii  beryl                                      0.2.0+svn20070119-r2891+3v1ubuntu0   Compositing window manager, decorator and theme suppor
ii  beryl-core                                 0.2.0+svn20070119-r2891+3v1ubuntu0   Compositing window manager - Beryl Project
ii  beryl-manager                              0.2.0+svn20070118-r2812+3v1ubuntu1   Tray application launcher tool - Beryl Project
ii  beryl-plugins                              0.2.0+svn20070119-r2900+3v1ubuntu0   Collection of plugins for Beryl
ii  beryl-plugins-data                         0.2.0+svn20070119-r2900+3v1ubuntu0   Plugins data - Beryl Project
ii  beryl-settings                             0.2.0+svn20070119-r2864+3v1ubuntu0   Plugin and configuration tool - Beryl Project
ii  beryl-settings-bindings                    0.1.5+svn20070119-r2863+3v1ubuntu0   Plugin and configuration tool - Beryl Project
ii  emerald                                    0.2.0+svn20070118-r2833+3v1ubuntu1   Decorator for beryl
ii  libberyldecoration0                        0.2.0+svn20070119-r2891+3v1ubuntu0   Settings library for plugins - Beryl Project
ii  libberylsettings0                          0.2.0+svn20070119-r2891+3v1ubuntu0   Settings library for plugins - Beryl Project
ii  libemeraldengine0                          0.2.0+svn20070118-r2833+3v1ubuntu1   Decoration engines for beryl
luser@ids-m8cj4:~$ clear

luser@ids-m8cj4:~$ sudo dpkg -l|grep -i beryl
ii  beryl                                      0.2.0+svn20070119-r2891+3v1ubuntu0   Compositing window manager, decorator and theme suppor
ii  beryl-core                                 0.2.0+svn20070119-r2891+3v1ubuntu0   Compositing window manager - Beryl Project
ii  beryl-manager                              0.2.0+svn20070118-r2812+3v1ubuntu1   Tray application launcher tool - Beryl Project
ii  beryl-plugins                              0.2.0+svn20070119-r2900+3v1ubuntu0   Collection of plugins for Beryl
ii  beryl-plugins-data                         0.2.0+svn20070119-r2900+3v1ubuntu0   Plugins data - Beryl Project
ii  beryl-settings                             0.2.0+svn20070119-r2864+3v1ubuntu0   Plugin and configuration tool - Beryl Project
ii  beryl-settings-bindings                    0.1.5+svn20070119-r2863+3v1ubuntu0   Plugin and configuration tool - Beryl Project
ii  emerald                                    0.2.0+svn20070118-r2833+3v1ubuntu1   Decorator for beryl
ii  libberyldecoration0                        0.2.0+svn20070119-r2891+3v1ubuntu0   Settings library for plugins - Beryl Project
ii  libberylsettings0                          0.2.0+svn20070119-r2891+3v1ubuntu0   Settings library for plugins - Beryl Project
ii  libemeraldengine0                          0.2.0+svn20070118-r2833+3v1ubuntu1   Decoration engines for beryl
luser@ids-m8cj4:~$ dpkg --purge beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings beryl-settings-bindings emerald libberyldecoration0 libberylsettings0 libemeraldengine0
dpkg: requested operation requires superuser privilege
luser@ids-m8cj4:~$ sudo dpkg --purge beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings beryl-settings-bindings emerald libberyldecoration0 libberylsettings0 libemeraldengine0
dpkg: dependency problems prevent removal of emerald:
 emerald-themes depends on emerald (>= 0.1).
dpkg: error processing emerald (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libemeraldengine0:
 emerald depends on libemeraldengine0.
dpkg: error processing libemeraldengine0 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of beryl-plugins:
 emerald depends on beryl-plugins.
dpkg: error processing beryl-plugins (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of beryl-plugins-data:
 beryl-plugins depends on beryl-plugins-data.
dpkg: error processing beryl-plugins-data (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libberylsettings0:
 beryl-plugins depends on libberylsettings0.
dpkg: error processing libberylsettings0 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of beryl-core:
 beryl-plugins depends on beryl-core.
dpkg: error processing beryl-core (--purge):
 dependency problems - not removing
(Reading database ... 96887 files and directories currently installed.)
Removing beryl-manager ...
Removing beryl ...
Removing beryl-settings ...
Removing beryl-settings-bindings ...
Removing libberyldecoration0 ...
Purging configuration files for libberyldecoration0 ...
Errors were encountered while processing:
 emerald
 libemeraldengine0
 beryl-plugins
 beryl-plugins-data
 libberylsettings0
 beryl-core
luser@ids-m8cj4:~$ sudo dpkg --purge beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings beryl-settings-bindings emerald libberyldecoration0 libberylsettings0 libemeraldengine0 emerald-themes
dpkg - warning: ignoring request to remove beryl which isn't installed.
dpkg - warning: ignoring request to remove beryl-manager which isn't installed.
dpkg - warning: ignoring request to remove beryl-settings which isn't installed.
dpkg - warning: ignoring request to remove beryl-settings-bindings which isn't installed.
dpkg - warning: ignoring request to remove libberyldecoration0 which isn't installed.
(Reading database ... 96756 files and directories currently installed.)
Removing emerald-themes ...
Removing libemeraldengine0 ...
Purging configuration files for libemeraldengine0 ...
Removing emerald ...
***
* Updating MIME database in /usr/share/mime...
Wrote 482 strings at 20 - 2818
Wrote aliases at 2818 - 29cc
Wrote parents at 29cc - 33ac
Wrote literal globs at 33ac - 3410
Wrote suffix globs at 3410 - 67f8
Wrote full globs at 67f8 - 681c
Wrote magic at 681c - be64
Wrote namespace list at be64 - be74
***
Purging configuration files for emerald ...
***
* Updating MIME database in /usr/share/mime...
Wrote 482 strings at 20 - 2818
Wrote aliases at 2818 - 29cc
Wrote parents at 29cc - 33ac
Wrote literal globs at 33ac - 3410
Wrote suffix globs at 3410 - 67f8
Wrote full globs at 67f8 - 681c
Wrote magic at 681c - be64
Wrote namespace list at be64 - be74
***
Removing beryl-plugins ...
Removing beryl-plugins-data ...
Removing beryl-core ...
Removing libberylsettings0 ...
Purging configuration files for libberylsettings0 ...
luser@ids-m8cj4:~$ sudo dpkg -l|grep -i beryl
luser@ids-m8cj4:~$ exit

```

---

