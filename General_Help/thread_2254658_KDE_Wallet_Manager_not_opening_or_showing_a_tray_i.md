---
title: "KDE Wallet Manager not opening or showing a tray icon"
date: 2014-11-29
forum: General Help
---

### Post by joomla1 on 2014-11-29
I'm on the latest Kubuntu, fully updated. I'm trying to open the kwallet manager to have a look at some passwords and I just can't get it to open!
I've gone to the wallet configuration program and reset the settings there to default, applied it and tried again. Nothing happens.

I've tried to open it by typing in wallet manager in the bar that appears when alt+f2 is pressed, selecting it from the list.
I've tried to open it by typing kwalletmanager in a terminal but nothing, no tray icon, no window appears.

Here's the output of kwalletmanager -v
```
Qt: 4.8.6
KDE Development Platform: 4.13.3
KDE Wallet Manager: 2.0

```
I get the following when I try to start the manager by typing kwalletmanager.
```
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.

```
If I try a killall kwalletmanager first and then try starting it via the commandline I get this:
```
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)

```

What's wrong?

---

### Post by carl4926 on 2014-11-29
You could always just delete the hidden .kde files and folders for kwallet and start again

---

