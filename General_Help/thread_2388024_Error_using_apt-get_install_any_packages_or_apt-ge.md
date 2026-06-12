---
title: "Error using apt-get install any packages or apt-get install -f"
date: 2018-03-27
forum: General Help
---

### Post by giobaxx on 2018-03-27
Trying so solve a problem with unity login we breaks something and now we are not able install/remove any packages. if i trying to install a packages with ***apt-get install packages*** or try to install  dependencies  with ***apt-get install -f*** the result is the same and is below[INDENT=2]
[/INDENT]
```
The following packages have unmet dependencies:

 aptitude : Depends: aptitude-common (= 0.6.8.2-1ubuntu4) but it is not going to be installed[INDENT]Depends: libboost-iostreams1.54.0 but it is not going to be installed[/INDENT]
[INDENT]Depends: libcwidget3 but it is not going to be installed[/INDENT]
 libpam-systemd : Depends: systemd-services (= 204-5ubuntu20.27)[INDENT]Breaks: libpam-systemd:i386 (!= 204-5ubuntu20.27) but 204-5ubuntu20.25 is to be installed[/INDENT]
 libpam-systemd:i386 : Depends: libc6:i386 (>= 2.8) but it is not going to be installed[INDENT]Depends: libcap2:i386 (>= 2.10) but it is not going to be installed
                                  Depends: libcgmanager0:i386 but it is not going to be installed
                                  Depends: libdbus-1-3:i386 (>= 1.0.2) but it is not going to be installed
                                  Depends: libnih-dbus1:i386 (>= 1.0.0) but it is not going to be installed
                                  Depends: libnih1:i386 (>= 1.0.0) but it is not going to be installed
                                  Depends: libpam0g:i386 (>= 0.99.7.1) but it is not going to be installed
                                  Breaks: libpam-systemd (!= 204-5ubuntu20.25) but 204-5ubuntu20.27 is to be installed[/INDENT]
 libsystemd-daemon0 :  Breaks: libsystemd-daemon0:i386 (!= 204-5ubuntu20.27) but 204-5ubuntu20.25 is to be installed
 libsystemd-daemon0:i386 : Depends: libc6:i386 (>= 2.8) but it is not going to be installed[INDENT=5]Breaks: libsystemd-daemon0 (!= 204-5ubuntu20.25) but 204-5ubuntu20.27 is to be installed[/INDENT]
 systemd-services:i386 : Depends: libacl1:i386 (>= 2.2.51-8) but it is not going to be installed[INDENT=4]Depends: libc6:i386 (>= 2.17) but it is not going to be installed
                                    Depends: libcap2:i386 (>= 2.10) but it is not going to be installed
                                    Depends: libcgmanager0:i386 but it is not going to be installed
                                    Depends: libdbus-1-3:i386 (>= 1.1.1) but it is not going to be installed
                                    Depends: libnih-dbus1:i386 (>= 1.0.0) but it is not going to be installed
                                    Depends: libnih1:i386 (>= 1.0.0) but it is not going to be installed
                                    Depends: libselinux1:i386 (>= 2.0.65) but it is not going to be installed
                                    Depends: libudev1:i386  (>= 183) but it is not going to be installed
                                    Depends: systemd-shim:i386 (>= 3) but it is not going to be installed[/INDENT]
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)



```

Seems that we broke apt-get install.....we tried to run dpkg-reconfigure -a but nothing.......whai can do??

---

### Post by deadflowr on 2018-03-27
*Thread moved to **General Help***

Please run
```
sudo apt-get update
```
and post back the results.

---

### Post by giobaxx on 2018-03-27
Tomorrow i will post....but if i remember well nothing seems wrong running apt-get update

---

### Post by giobaxx on 2018-03-28
....magically this morning apt-get works again.....and i don't know why...

the only things i did i removed google repository because of a gpg error during the apt-get update, so i didn't realized what magically was fixed...

Then i  run **apt-get install -f** that  removed a lot of packages included Network-Manager and **apt-get autoremove**...

Not without problems but at the end we have reinstalled unity and added Gnome as desktop manager. Seems to works even if there is something strange. In Some profile if you use unity the upper bar is the one used by gnome rather then unity itself.
But we didn't touch.....to worry to broke again something..

---

### Post by deadflowr on 2018-03-28
See if this helps clear up the google gpg issues:
[https://ubuntuforums.org/showthread.php?t=2367994]("https://ubuntuforums.org/showthread.php?t=2367994")

---

### Post by giobaxx on 2018-04-03
tanks to all of you

---

