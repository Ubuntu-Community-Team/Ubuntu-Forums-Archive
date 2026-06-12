---
title: "Kubuntu 14.04 issues after update"
date: 2015-10-29
forum: General Help
---

### Post by nifhel on 2015-10-29
I have Kubuntu 14.04 (3.13.0-66-generic) and after a recent update I get some serious issues in my system. 
Is a very weird behavior and I can't get ahead of it... I wonder if it happened to someone else and how to solve it, this is how I reproduce it: 
 
* Start the system; 
* Open something like the System Preferences, everything look normal; 
* Open Android Studio; 
* Open something alse like KCalc or and image, and everythig look weird like this: 
 [http://imgur.com/a/HwEzs](http://imgur.com/a/HwEzs) 
 [http://imgur.com/uAmvH53](http://imgur.com/uAmvH53) 
 
So to recap, the apps that I open BEFORE opening Android Studio look fine (even after I open Android Studio), and the apps that I open AFTER Android Studio look weird (even after I close Android Studio). This is affecting mosto of the apps but not all, for example Sublime Text 2 or Chrome have no problem. 
 
I really have no idea what is wrong, or why Android Studio is starting the weird behavior. 
But the problem starter after one of this updates (more likely the last one): 


```
    Start-Date: 2015-10-23  09:39:03
    Commandline: apt-get upgrade                                                                                                                                                                    
    Upgrade: python3-problem-report:amd64 (2.14.1-0ubuntu3.15, 2.14.1-0ubuntu3.16), oxideqt-codecs-extra:amd64 (1.9.5-0ubuntu0.14.04.1, 1.10.3-0ubuntu0.14.04.1), python3.4:amd64 (3.4.3-1ubuntu1~14.04.1, 3.4.3-1ubuntu1~14.04.3), google-chrome-stable:amd64 (46.0.2490.71-1, 46.0.2490.80-1), python-urllib3:amd64 (1.7.1-1ubuntu3, 1.7.1-1ubuntu4), python3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.1, 3.4.3-1ubuntu1~14.04.3), tzdata-java:amd64 (2015f-0ubuntu0.14.04, 2015g-0ubuntu0.14.04), libpython3.4-stdlib:amd64 (3.4.3-1ubuntu1~14.04.1, 3.4.3-1ubuntu1~14.04.3), libpython3.4:amd64 (3.4.3-1ubuntu1~14.04.1, 3.4.3-1ubuntu1~14.04.3), libpython3.4-minimal:amd64 (3.4.3-1ubuntu1~14.04.1, 3.4.3-1ubuntu1~14.04.3), apport-kde:amd64 (2.14.1-0ubuntu3.15, 2.14.1-0ubuntu3.16), apport-gtk:amd64 (2.14.1-0ubuntu3.15, 2.14.1-0ubuntu3.16), apport:amd64 (2.14.1-0ubuntu3.15, 2.14.1-0ubuntu3.16), python3-apport:amd64 (2.14.1-0ubuntu3.15, 2.14.1-0ubuntu3.16), tzdata:amd64 (2015f-0ubuntu0.14.04, 2015g-0ubuntu0.14.04), linux-libc-dev:amd64 (3.13.0-65.106, 3.13.0-66.108)
    End-Date: 2015-10-23  09:39:24
    
    Start-Date: 2015-10-23  09:40:55
    Install: linux-image-extra-3.13.0-66-generic:amd64 (3.13.0-66.108, automatic), linux-image-3.13.0-66-generic:amd64 (3.13.0-66.108, automatic), linux-headers-3.13.0-66:amd64 (3.13.0-66.108, automatic), linux-headers-3.13.0-66-generic:amd64 (3.13.0-66.108, automatic), linux-signed-image-3.13.0-66-generic:amd64 (3.13.0-66.108, automatic)
    Upgrade: linux-headers-generic:amd64 (3.13.0.65.71, 3.13.0.66.72), linux-signed-generic:amd64 (3.13.0.65.71, 3.13.0.66.72), linux-signed-image-generic:amd64 (3.13.0.65.71, 3.13.0.66.72), linux-image-generic:amd64 (3.13.0.65.71, 3.13.0.66.72), linux-generic:amd64 (3.13.0.65.71, 3.13.0.66.72)
    End-Date: 2015-10-23  09:42:32
    
    Start-Date: 2015-10-28  09:46:01
    Install: libsctp1:amd64 (1.0.15+dfsg-1, automatic), lksctp-tools:amd64 (1.0.15+dfsg-1, automatic)
    Upgrade: python3-problem-report:amd64 (2.14.1-0ubuntu3.16, 2.14.1-0ubuntu3.18), mysql-server-core-5.5:amd64 (5.5.44-0ubuntu0.14.04.1, 5.5.46-0ubuntu0.14.04.2), mysql-client-core-5.5:amd64 (5.5.44-0ubuntu0.14.04.1, 5.5.46-0ubuntu0.14.04.2), openjdk-7-jdk:amd64 (7u79-2.5.6-0ubuntu1.14.04.1, 7u85-2.6.1-5ubuntu0.14.04.1), openjdk-7-jre-headless:amd64 (7u79-2.5.6-0ubuntu1.14.04.1, 7u85-2.6.1-5ubuntu0.14.04.1), mysql-common:amd64 (5.5.44-0ubuntu0.14.04.1, 5.5.46-0ubuntu0.14.04.2), apport-kde:amd64 (2.14.1-0ubuntu3.16, 2.14.1-0ubuntu3.18), libmysqlclient18:amd64 (5.5.44-0ubuntu0.14.04.1, 5.5.46-0ubuntu0.14.04.2), libmysqlclient18:i386 (5.5.44-0ubuntu0.14.04.1, 5.5.46-0ubuntu0.14.04.2), openjdk-7-jre:amd64 (7u79-2.5.6-0ubuntu1.14.04.1, 7u85-2.6.1-5ubuntu0.14.04.1), apport-gtk:amd64 (2.14.1-0ubuntu3.16, 2.14.1-0ubuntu3.18), apport:amd64 (2.14.1-0ubuntu3.16, 2.14.1-0ubuntu3.18), icedtea-7-jre-jamvm:amd64 (7u79-2.5.6-0ubuntu1.14.04.1, 7u85-2.6.1-5ubuntu0.14.04.1), python3-apport:amd64 (2.14.1-0ubuntu3.16, 2.14.1-0ubuntu3.18), ntpdate:amd64 (4.2.6.p5+dfsg-3ubuntu2.14.04.3, 4.2.6.p5+dfsg-3ubuntu2.14.04.5)
    End-Date: 2015-10-28  09:46:15

```

 
Any clue? :'-(

[COLOR=#000000][FONT=sans-serif]Update, I believe is a kwin issue:[/FONT][/COLOR]

[COLOR=#000000][FONT=sans-serif]```
$ kwin --replace[/FONT][/COLOR][COLOR=#000000][FONT=sans-serif]QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]QCoreApplication::sendPostedEvents: Cannot send posted events for objects in another thread[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]QCoreApplication::sendPostedEvents: Cannot send posted events for objects in another thread[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]QCoreApplication::sendPostedEvents: Cannot send posted events for objects in another thread[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]QCoreApplication::sendPostedEvents: Cannot send posted events for objects in another thread[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]OpenGL vendor string:                   Intel Open Source Technology Center[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]OpenGL renderer string:                 Mesa DRI Intel(R) Ivybridge Mobile [/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]OpenGL version string:                  3.3 (Core Profile) Mesa 10.1.3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]OpenGL shading language version string: 3.30[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Driver:                                 Intel[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]GPU class:                              IvyBridge[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]OpenGL version:                         3.3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]GLSL version:                           3.30[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Mesa version:                           10.1.3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X server version:                       1.15.1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Linux kernel version:                   3.13[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Direct rendering:                       yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Requires strict binding:                no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]GLSL shaders:                           yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Texture NPOT support:                   yes[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]Virtual Machine:                        no[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]^CX Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x9e[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01ac5[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01ac5[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01ac5[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01af7[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01af7[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x9e[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01aac[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01aac[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01aac[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006e1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006e1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006e1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006d1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006d1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006d1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01a8f[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01a8f[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01a8f[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006c1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006c1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x9e[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01ade[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01ade[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a01ade[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006b0[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006b0[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: RenderBadPicture (invalid Picture parameter) 143[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Extension:    139 (RENDER)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Minor opcode: 7 (RenderFreePicture)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006b0[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 18 (X_ChangeProperty)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006f1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]X Error: BadWindow (invalid Window parameter) 3[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Major opcode: 4 (X_DestroyWindow)[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]  Resource id:  0x4a006f1[/FONT][/COLOR]
[COLOR=#000000][FONT=sans-serif]
```[/FONT][/COLOR]

---

### Post by nifhel on 2015-10-29
Ok, the problem was in "openjdk", I installed oracle-java following this tutorial and now everything seens to be working fine...
[https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get)

---

