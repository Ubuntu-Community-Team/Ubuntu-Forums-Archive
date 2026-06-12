---
title: "KDEInit Error - Konsole (Kubuntu)"
date: 2014-07-15
forum: General Help
---

### Post by Damien_Duran on 2014-07-15
Hello there, I am running a kubuntu-desktop environment on Ubuntu 14.04 LTS and everytime I try to open up my Konsole, I get an error with the matching string of : KDEInit could not launch '/usr/lib/kde4/libexec/kdesu'

Could anyone tell me how to fix this?

---

### Post by ibjsb4 on 2014-07-16
Do you have kdesudo installed?

Also try opening it in terminal and see if it gives you and more info.
```
konsole
```

---

### Post by Damien_Duran on 2014-07-16
Yes I do have kdesudo installed.

Also, booting up konsole by typing 'konsole' into terminal (konsole) the following output (along with the bootup of another konsole application) is displayed :

QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
root@user-X502CA:/home/user# QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /root/.config/ibus/bus
Bus: open : Can not get ibus-daemon's address. 
IBusInputContext::createInputContext: no connection to ibus-daemon 

however doing it this way doesn't bring up the KDEInit error. Still doesn't solve the problem.

---

### Post by ibjsb4 on 2014-07-17
There is a system dependent limit to the number of files and directories that can be monitored simultaneously. If this limit has been reached, path will not be added to the file system watcher, and a warning message will be printed to stderr, which is failed to add paths.

[http://developer.blackberry.com/native/reference/cascades/qfilesystemwatcher.html](http://developer.blackberry.com/native/reference/cascades/qfilesystemwatcher.html)

Another suggestion is to create a new user.

[https://forum.kde.org/viewtopic.php?f=63&t=107784](https://forum.kde.org/viewtopic.php?f=63&t=107784)

---

