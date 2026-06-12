---
title: "mercury messenger with java"
date: 2008-01-22
forum: General Help
---

### Post by ELD on 2008-01-22
Hi all what is the easiest way to install a working version of java to work with mercury messenger? Can't seem to find a correct guide.

---

### Post by Nibes on 2008-01-24
Hello that's easy to solve. 
go to the web site [http://www.mercury.im/](http://www.mercury.im/) and choose the Ubuntu logo
Download the file .deb and open it with Gdebi package manager.. something like that worked for me. 
I went there and open the file.deb for ubuntu. 
the  instalation was quick
and I was able to find the mercury messenger inside my aplications panel. 
Goodluck  I hope it helps.

---

### Post by ELD on 2008-01-24
I don't think it is using the right java though, as it crashed on opening, and the terminal said something about java.

---

### Post by taurus on 2008-01-24
Can you post the whole error message?  Also, what version of java do you have on your machine?

```
java -version
```
If you need to install Sun java, run
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by ELD on 2008-01-29
Here is what happens via terminal
> 
liam@liam-desktop:~$ mercury
29.01.2008 10:37:14 Mercury/1.9 [20071020]
29.01.2008 10:37:14 Resource Type > General
29.01.2008 10:37:14 Locations > Loading...
29.01.2008 10:37:14 Locations > Loaded OK.
29.01.2008 10:37:14 Main > Loading Global Settings...
29.01.2008 10:37:15 Main > Loading Splash Screen...
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Changeable color
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Status color
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Glass
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Blue Purple
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Blue Green
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Teal Purple
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Self, Yellow Red
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Changeable color
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Status color
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob - Glass
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsDroneV3.zip DRON3 by Rob
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Self Contact
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Default Contact
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Default Contact With Bullet
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Default Contact With Star
29.01.2008 10:37:17 J1.5+ : false&&false -> 1.7.0
29.01.2008 10:37:17 Views > Requirement not OK : 'Java1.5+' for ./resources/AppData/Views/RobsSteam.zip Steam Group


And here is java version
> 
liam@liam-desktop:~$ java -version
java version "1.7.0"
IcedTea Runtime Environment (build 1.7.0-b21)
IcedTea Client VM (build 1.7.0-b21, mixed mode, sharing)


---

