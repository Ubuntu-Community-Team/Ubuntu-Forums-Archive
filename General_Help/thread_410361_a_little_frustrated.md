---
title: "a little frustrated"
date: 2007-04-15
forum: General Help
---

### Post by ale52 on 2007-04-15
1. When downloading an application from a repository, where does it download to?  Is it the same location each time?  What is that location?

2. When downloading from a location other than a repository, where does it go?  

I know that to remove an application you go to Applications - Add/Remove... yet a couple of the applications I've downloaded from other than a repository are put in different places on the drive, and they are not always the same place.  

3.  Finally, how do you go about removing those applications as they do not show up in Add/Remove...

Thank you for your kind help.


Alan <>< :)

---

### Post by christhemonkey on 2007-04-15
1. All .deb files downloaded by apt go to /var/cache/apt/archives/

2. See above/ ah i get what you mean now, where do all the individual files go to?
Try right clicking on the name in synaptic package manager and viewing installed files.

3. Synaptic package manager can aid you to remove these files.
System > Administration > Synaptic Package Manager

---

### Post by aysiu on 2007-04-15
To launch an application, you don't have to know where it is.

Usually, there's a menu entry for graphical applications. When there isn't, the name of the application usually launches it. For example, if you install Inkscape, press Alt-F2 and type ```
inkscape
``` The application will start, then.

In case you're curious, though, executables are usually in /usr/bin and installer files are usually kept in /var/cache/apt/archives

---

### Post by orb9220 on 2007-04-15
And right-click properties on installed packages in synaptic will show you were everything for that app is installed.

---

### Post by Maestro23 on 2007-04-15
Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

