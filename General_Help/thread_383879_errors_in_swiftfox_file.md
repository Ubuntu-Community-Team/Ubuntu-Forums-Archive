---
title: "errors in swiftfox file??"
date: 2007-03-13
forum: General Help
---

### Post by DougieFresh4U on 2007-03-13
While doing updates the following errors appeared in terminal and could some one please guide me to fix. Thanks:;[B]File '/usr/share/applications/Swiftfox.desktop' contains invalid MIME type '' that is missing a slash
File '/usr/share/applications/Swiftfox.desktop' contains invalid MIME type '' that is missing a slash[/B]

---

### Post by taurus on 2007-03-13
What does it look from a terminal?

```
cat /usr/share/applications/Swiftfox.desktop
```

---

### Post by DougieFresh4U on 2007-03-13
In my Applications>Network menu there are two Swiftfox also. One is "Swiftfox" and the other "Swiftfox Browser" and here is my terminal output::[B]dougie@DougiesToyBox:~$ cat /usr/share/applications/Swiftfox.desktop
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Swiftfox
Comment=Web Browser
Comment[en_US]=Web Browser
Exec=swiftfox %u
GenericName=Swiftfox
GenericName[en_US]=Swiftfox
Icon=/usr/share/pixmaps/swiftfox.png
MimeType=;
Name[en_US]=Swiftfox
Path=
StartupNotify=true
Terminal=false
TerminalOptions=
Type=Application
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=
Categories=Application;Network;
dougie@DougiesToyBox:~$ [/B]

---

### Post by Stirling on 2007-03-14
For some reason you have a stray semi-colon after MimeType.  Delete that from the file.  I checked the [Swiftfox.desktop]("http://getswiftfox.com/builds/installer/Swiftfox.desktop") the Swiftfox installer uses and it doesn't have this problem.  How did you install Swiftfox?

---

### Post by DougieFresh4U on 2007-03-14
> **Stirling said:**
> For some reason you have a stray semi-colon after MimeType.  Delete that from the file.  I checked the [Swiftfox.desktop]("http://getswiftfox.com/builds/installer/Swiftfox.desktop") the Swiftfox installer uses and it doesn't have this problem.  How did you install Swiftfox?

I installed using Automatix  a while back (4 months ago) when Edgy was on this machine. How do I delete? Thanks for the reply.

---

### Post by taurus on 2007-03-14
```
sudo nano -w /usr/share/applications/Swiftfox.desktop
```
Save and exit with <Ctrl>o and <Ctrl>x.

---

