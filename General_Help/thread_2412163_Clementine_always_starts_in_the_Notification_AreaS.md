---
title: "Clementine always starts in the Notification Area/System Tray"
date: 2019-02-08
forum: General Help
---

### Post by lsutiger on 2019-02-08
When I start Clementine, it puts an icon in the notification area/system tray. In order to get it to run as a GUI I have to click on that icon and select Activate.
Is there a way, like a command line option, to show the gui? I have tried the -o option, but it throws errors:
```
WARN  unknown                          QPixmap: It is not safe to use pixmaps outside the GUI thread
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: Permission denied
WARN  unknown                          QFileSystemWatcher: failed to add paths: /home/Music/lost+found
WARN  unknown                          QPainter::begin: Paint device returned engine == 0, type: 2
WARN  unknown                          QSortFilterProxyModel: invalid inserted rows reported by source model

```
And then does nothing.

---

### Post by TheFu on 2019-02-08
Those are warnings, not errors.  

I think that is the expected behavior.
You can test if it is a config error for the userid by making another userid, logout and log into that new userid, then run clementine. A fresh config if often very helpful.

I'm getting a warning 
```
WARN  unknown                          No systemtrayicon available
```, but I don't have a DE, no tray, so that is expected.  The GUI does come up with a single invocation.

---

### Post by Holger_Gehrke on 2019-02-08
Menu: "Tools"->"Preferences" Tab "Behavior" Setting "When Clementine Starts" Option "Always show the main window". At least that's the way for Clementine 1.3.1, the version that is in the repositories for Ubuntu 18.04. The warnings are unrelated, they are mostly about the root owned "lost+found"-directory in a directory you've set as part of your music library (you've probably mounted an ext2/ext3/ext4 filesystem into /home/music; that directory is where fsck puts file-fragments when cleaning up that kind of filesystem).

Holger

---

### Post by lsutiger on 2019-02-08
Thanks, I'll try that.

---

### Post by lsutiger on 2019-02-08
I have v 1.2.3 and it does not have that setting. 16.04.

---

### Post by again? on 2019-02-09
You could update from this ppa.
[https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine](https://launchpad.net/~me-davidsansome/+archive/ubuntu/clementine)

---

