---
title: "Can't get to /home/user"
date: 2014-03-31
forum: General Help
---

### Post by oaxacamatt1 on 2014-03-31
Hi all,
Just this morning I found a disturbing error message when I tried to view my user home directory.
I am running Crunchbang 12.04LTS on a generic Gateway (nothing odd).

I found:
```

Failed to open directory "user".
Error when getting information for file '/home/user/.gvfs': Transport endpoint is not connected.
```

So I went to my terminal and tried to view '/home/user/.gvfs' and got a large amount of junk (what I would call junk)

```

sudo kwrite /home/mcc/.gvfs
[sudo] password for mcc: 
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 103: Having multiple values in <test> isn't supported and may not work as expected
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 138: Having multiple values in <test> isn't supported and may not work as expected
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 103: Having multiple values in <test> isn't supported and may not work as expected
Fontconfig warning: "/etc/fonts/conf.d/65-droid-sans-fonts.conf", line 138: Having multiple values in <test> isn't supported and may not work as expected
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
kbuildsycoca4 running...
kbuildsycoca4(17502) KBuildSycoca::checkTimestamps: checking file timestamps
kbuildsycoca4(17502) KBuildSycoca::checkTimestamps: timestamps check ok
kbuildsycoca4(17502) kdemain: Emitting notifyDatabaseChanged ()
```

What do I do now???
Cheeers

PS Hold it I installed I-Librarian last night....

---

### Post by slickymaster on 2014-03-31
A possible workaround you can try is to manually unmount your _~/.gvfs_, running the following at a terminal window:```
fusermount -u ~/.gvfs
```

Then close/unmount all opened remote locations in Nautilus and log out and back in, again. This will restore the .gvfs-functionality.

Please refer to [this]("http://r3dux.org/2011/08/how-to-workaround-gvfs-transport-endpoint-is-not-connected-errors/").

---

### Post by oaxacamatt1 on 2014-04-03
Thanks, that works for me
Matt

---

