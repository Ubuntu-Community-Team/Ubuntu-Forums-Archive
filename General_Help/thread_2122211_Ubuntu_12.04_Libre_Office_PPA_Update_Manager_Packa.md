---
title: "Ubuntu 12.04 Libre Office PPA Update Manager Packages Held Back Partial Upgrade"
date: 2013-03-04
forum: General Help
---

### Post by fleamour on 2013-03-04
As title above says really. Should I purge Libre Office then try reinstall? Launchpad says built 7 hrs ago...

---

### Post by ManamiVixen on 2013-03-04
Looks like you caught the PPA mid update. Your best bet is to install ppa-purge and have it  remove the ppa and automatically reinstall the Ubuntu provided version. Afterwards, go into the software sources and renable the ppa and, update, then upgrade again to see if they finished with ALL the packages in their repo this time.

---

### Post by fleamour on 2013-03-04
Purged LibreOffice PPA with Y PPA Manager now get this error:

> Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type &#8216;ain&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/libreoffice-ppa-precise.list'

Stuck!

---

### Post by fleamour on 2013-03-04
This fixed:

[http://askubuntu.com/questions/96967/how-do-i-fix-this-etype-is-not-known-on-line-in-source-list-update](http://askubuntu.com/questions/96967/how-do-i-fix-this-etype-is-not-known-on-line-in-source-list-update)

```
gksudo gedit /etc/apt/sources.list.d/libreoffice-ppa-precise.list
```

Then delete "ain" & save file & exit editor.

---

### Post by fleamour on 2013-03-04
Purged PPA then following [this]("http://www.liberiangeek.net/2013/03/libreoffice-4-0-now-available-in-its-official-ppa-for-ubuntu-12-04-12-10/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+LiberianGeek+%28Liberian+Geek%29") guide to get working LibreOffice 4 installed

Thanks!

\\:D/

---

