---
title: "qt application misbehavior?"
date: 2014-03-19
forum: General Help
---

### Post by princeofnam on 2014-03-19
I suddenly began having this error with every KDE based application.

>  

xxxx:~$ kate &
[1] 2724
xxxxxx:~$ QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.
uint DBusMenuExporterDBus::GetLayout(int, int, const QStringList&, DBusMenuLayoutItem&): Condition failed: menu 





---

### Post by slooksterpsv on 2014-03-19
Found this via kde.org
[https://forum.kde.org/viewtopic.php?f=66&t=102251](https://forum.kde.org/viewtopic.php?f=66&t=102251) - saying the first error just to ignore, as for the unit DBusMenu.... see below

Found this via Launchpad

[https://answers.launchpad.net/appmenu-qt/+question/183966](https://answers.launchpad.net/appmenu-qt/+question/183966)
[quote=Ritesh Raj Sarraf (rrs) said on 2012-01-17:	 #1]
Answering myself. The appmenu plasma widget needs to be added to the panel. Thanks.
[/quote]

I don't know if any of this helps, but thought I'd point it out just in case.

---

### Post by princeofnam on 2014-03-20
Hmm.  Don't see anything called "appmenu" but I did already have the file menu widget on a panel.  Didn't fix the issue unfortunately.

---

### Post by slooksterpsv on 2014-03-20
it looks like this is a bug. Try the following:

Open ~/.kde/share/config/nepomukserverrc and set &#8220;Start Nepomuk&#8221; to false.

[Basic Settings]
Start Nepomuk=false
Open ~/.kde/share/config/kdedrc and set &#8220;autoload&#8221; to false for nepomuksearchmodule:

[Module-nepomuksearchmodule]
autoload=false

Restart, try again. Taken from: 
[http://ubuntuku.org/16/how-to-disable-nepomuk-akonadi/](http://ubuntuku.org/16/how-to-disable-nepomuk-akonadi/)

EDIT: [https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/959151](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/959151) - is the bug report location

---

### Post by princeofnam on 2014-03-20
Weird.  I think all my values were already false 

> [$Version]
update_info=nepomukstrigiservice-migrate.upd:nepomukstrigiservice-migrate

[Service-nepomukfileindexer]
autostart=false

[Service-nepomukstrigiservice]
autostart[$d]

[main Settings]
GraphMigrationRequired=false
Port=1113
Storage Dir[$e]=$HOME/.kde/share/apps/nepomuk/repository/main/
Used Soprano Backend=virtuosobackend



---

