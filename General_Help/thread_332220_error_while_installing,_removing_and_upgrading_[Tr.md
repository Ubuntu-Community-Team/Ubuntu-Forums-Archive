---
title: "error while installing, removing and upgrading [Translated]"
date: 2007-01-05
forum: General Help
---

### Post by Cholito on 2007-01-05
I made [this post]("http://www.ubuntuforums.org/showthread.php?t=331985") before, but some text was in Spanish so I decided to change my system's language and repost it but this time in English and better documented ;)

So this is what is happening:

```
alejandro@matos:~$ sudo aptitude install ffmpeg
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libavahi-qt3-1 
The following packages have been kept back:
  avahi-daemon dbus dbus-1-utils firefox firefox-gnome-support 
  libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 
  libavahi-glib1 libdbus-1-3 libnspr4 libnss3 mozilla-thunderbird w3m 
The following NEW packages will be installed:
  ffmpeg 
0 packages upgraded, 1 newly installed, 0 to remove and 16 not upgraded.
Need to get 0B/180kB of archives. After unpacking 627kB will be used.
Writing extended state information... Done
(Reading database ... dpkg: error processing /var/cache/apt/archives/ffmpeg_3%3a0.cvs20060823-3.1ubuntu1_i386.deb (--unpack):
[COLOR="Red"] unable to open files list file for package `cdrecord': Input/output error[/COLOR]
Errors were encountered while processing:
 /var/cache/apt/archives/ffmpeg_3%3a0.cvs20060823-3.1ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
alejandro@matos:~$ 
```

then I tried this:
```
alejandro@matos:~$ dpkg -L cdrecord
dpkg-query: unable to open files list file for package `cdrecord': Input/output error
```
and this just to check
```
alejandro@matos:~$ dpkg -L xine-ui
/.
/usr
/usr/share
/usr/share/man
/usr/share/man/fr
/usr/share/man/fr/man1
/usr/share/man/fr/man1/xine.1.gz
/usr/share/man/es
/usr/share/man/es/man1
(more files...)
```
so cdrecord is broken? I tried to reinstall it
```
alejandro@matos:~$ sudo apt-get install --reinstall cdrecord
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 16 not upgraded.
Need to get 0B/581kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Preconfiguring packages ...
Selecting previously deselected package cdrecord.
(Reading database ... dpkg: error processing /var/cache/apt/archives/cdrecord_4%3a2.01+01a03-5ubuntu2_i386.deb (--unpack):
 unable to open files list file for package `cdrecord': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/cdrecord_4%3a2.01+01a03-5ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
No luck, lets keep going. Next step: remove it and reinstall it:
```
alejandro@matos:~$ sudo apt-get remove cdrecord
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libk3b2 kcontrol cdrecord vcdimager kdebase-data ubuntu-desktop kicker k3b
  nautilus-cd-burner
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  cdrecord k3b nautilus-cd-burner ubuntu-desktop
0 upgraded, 0 newly installed, 4 to remove and 16 not upgraded.
Need to get 0B of archives.
After unpacking 12.6MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... dpkg: error processing ubuntu-desktop (--remove):
 unable to open files list file for package `cdrecord': Input/output error
Errors were encountered while processing:
 ubuntu-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
alejandro@matos:~$
```
And this is how everthing ends, I have no more ideas. Can anyone know something about this? Any kind of help will be well received

---

### Post by Cholito on 2007-01-05
Uhmm, this is my last chance to fix it before I reinstall ubuntu...so any ideas? ](*,)

---

### Post by nikinostyler on 2007-01-05
have a look at this.. it will maybe help....

[http://www.ubuntuforums.org/archive/index.php/t-249474.html](http://www.ubuntuforums.org/archive/index.php/t-249474.html)


nikin

---

### Post by Cholito on 2007-01-06
I have a new error message now, maybe you know about it? (it doesn't matter which package I want to install, the error is always the same)

```
alejandro@matos:~$ i ffmpeg
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libavahi-qt3-1 
The following packages have been kept back:
  avahi-daemon dbus dbus-1-utils firefox firefox-gnome-support libavahi-client3 libavahi-common-data 
  libavahi-common3 libavahi-core4 libavahi-glib1 libdbus-1-3 libnspr4 libnss3 mozilla-thunderbird w3m 
The following NEW packages will be installed:
  ffmpeg 
0 packages upgraded, 1 newly installed, 0 to remove and 16 not upgraded.
Need to get 0B/180kB of archives. After unpacking 627kB will be used.
Writing extended state information... Done
(Reading database ... dpkg: error processing /var/cache/apt/archives/ffmpeg_3%3a0.cvs20060823-3.1ubuntu1_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libecore1-dbus': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/ffmpeg_3%3a0.cvs20060823-3.1ubuntu1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

---

