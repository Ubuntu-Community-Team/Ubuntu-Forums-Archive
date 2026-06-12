---
title: "Login can't connect to X server display :0 first time after boot"
date: 2007-04-30
forum: General Help
---

### Post by baslow on 2007-04-30
I'm running Kubuntu under Feisty but my problem began under Edgy. Whenever I login to either KDE (my default) or Gnome, immediately after the machine has booted, my screen goes blank for about four minutes and finally returns me to the login screen.  After that login works properly until I reboot.  The problem is not particular to a single user; I created a new user which showed the same problem as soon as it was created. When I did a console login from the login screen after the first login my .xsession-errrors file read as follows:

```
]Xsession: X session started for baslow at Mon Apr 30 17:58:17 EDT 2007
xrdb: Connection refused
xrdb: Can't open display ':0'
xrdb: Connection refused
xrdb: Can't open display ':0'
Couldn't connect to X server.
/usr/bin/xmodmap:  unable to open display ':0'
xset:  unable to open display ":0"
xset:  unable to open display ":0"
xsetroot:  unable to open display ':0'
startkde: Starting up...
ksplash: cannot connect to X server :0
xprop:  unable to open display ':0'
usage:  xprop [-options ...] [[format [dformat]] atom] ...

where options include:
    -grammar                       print out full grammar for command line
    -display host:dpy              the X server to contact
    -id id                         resource id of window to examine
    -name name                     name of window to examine
    -font name                     name of font to examine
    -remove propname               remove a property
    -set propname value            set a property to a given value
    -root                          examine the root window
    -len n                         display at most n bytes of any property
    -notype                        do not display the type field
    -fs filename                   where to look for formats for properties
    -frame                         don't ignore window manager frames
    -f propname format [dformat]   formats to use for property of given name
    -spy                           examine window properties forever

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
kded: cannot connect to X server :0
DCOP aborting call from 'anonymous-7593' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
kcminit_startup: cannot connect to X server :0
ksmserver: cannot connect to X server :0
startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
xprop:  unable to open display ':0'
usage:  xprop [-options ...] [[format [dformat]] atom] ...

where options include:
    -grammar                       print out full grammar for command line
    -display host:dpy              the X server to contact
    -id id                         resource id of window to examine
    -name name                     name of window to examine
    -font name                     name of font to examine
    -remove propname               remove a property
    -set propname value            set a property to a given value
    -root                          examine the root window
    -len n                         display at most n bytes of any property
    -notype                        do not display the type field
    -fs filename                   where to look for formats for properties
    -frame                         don't ignore window manager frames
    -f propname format [dformat]   formats to use for property of given name
    -spy                           examine window properties forever

startkde: Done
```

So, I'm having problems with the X server the first time I log in after booting which seem to be solved the second and subsequent times I login, until the next reboot.  I don't know a lot about X server and the books I've consulted ("Linux Administration Handbook (2002 edition", "How Linux Works") have been surprisingly little help.  Can anyone figure out what's going on or point me to a resource that might provide me with enough information to figure it out myself?

Thanks!

Baslow

---

### Post by zvacet on 2007-05-01
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

