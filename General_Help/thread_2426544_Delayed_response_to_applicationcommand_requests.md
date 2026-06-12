---
title: "Delayed response to application/command requests"
date: 2019-09-10
forum: General Help
---

### Post by gus_zernial on 2019-09-10
I'm on Kubuntu 19.04/Plasma 5.16.5/kernel5.0.0-27 and have been experiencing delayed responses to application/command startup requests. Monitoring CPU/memory/disk use including watching top and iotop doesn't seem to show anything unusual. Network testing on speedtest.net is good, and I'm accessing disk on the Kubuntu box only, not on a LAN/network.

Performance once an app is running is generally better, tho there can be delays there as well. Anyway, I started using the time command, for example: 

$ sudo /usr/bin/time -f "Elapsed Time = %E, Inputs %I, Outputs %O" systemsettings5
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
QStandardPaths: XDG_RUNTIME_DIR not set, defaulting to '/tmp/runtime-root'
kf5.kservice.sycoca: Parse error in  "/home/rbroman/.config/menus/applications-merged/xdg-desktop-menu-dummy.menu" , line  1 , col  1 :  "unexpected end of file"
file:///usr/share/kpackage/genericqml/org.kde.systemsettings.sidebar/contents/ui/CategoriesPage.qml:66:21: QML Action: LayoutDirection attached property only works with Items and Windows
KActivities: Database connection:  "kactivities_db_resources_140455786235584_readonly" 
    query_only:          QVariant(qlonglong, 1) 
    journal_mode:        QVariant(QString, "wal") 
    wal_autocheckpoint:  QVariant(qlonglong, 100) 
    synchronous:         QVariant(qlonglong, 0)
Nothing to load - the client id is empty
Nothing to load - the client id is empty
[Error at ResultSetPrivate::initQuery]:  QSqlError("1", "Unable to execute statement", "no such column: rl.initiatingAgent")
[Error at ResultSetPrivate::initQuery]:  QSqlError("1", "Unable to execute statement", "no such column: rl.initiatingAgent")
Closing SQL connection:  "kactivities_db_resources_140455786235584_readonly"
Elapsed Time = 0:54.40, Inputs 27920, Outputs 4600

This is my first experience with the time command, and I'm probably using it wrong, but by observation I think that systemsettings is in fact taking 54 seconds
to start, and  Inputs 27920, Outputs 4600 seems like a lot to me.

Can someone help/advise me how to troubleshoot my app startup/delays?

Thx, Gus

---

