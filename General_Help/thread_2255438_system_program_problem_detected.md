---
title: "system program problem detected"
date: 2014-12-05
forum: General Help
---

### Post by kirtan_parmar on 2014-12-05
For the past two weeks, there's been a few messages popping up when I boot saying system program problem detected. I click on the report now button every time to no avail. Also I can't figure out if the problem has been solved or not. The ```
/var/crash
``` directory has the following sub-directories: ```
_usr_bin_apt-get.0.crash
```, ```
_usr_bin_do-release-upgrade.0.crash
```, ```
_usr_bin_update-manager.1000.crash
```, ```
_usr_lib_update-notifier_apt_check.py.1000.crash
```, ```
_usr_sbin_aptd.0.crash
```, ```
_usr_share_apport_apport-gtk.0.crash
``` and ```
_usr_share_apport_apport-gtk.1000.crash
```. So should i just ignore these messages or is there any way I can fix this? I am newbie user. Please help.

---

### Post by veddox on 2014-12-05
1. What version of Ubuntu are you using?
  	2. Next time the error message comes up, click on the &quot;More details&quot; button (or whatever its called) and tell us whatever it says.
  	3. _usr_bin_apt-get.0.crash, etc., are not directories, they are files containing crash reports that probably contain very useful information. Attach some of them to your next post (or use Pastebin) so we can have a look at them.
  	 
  	Just a random guess: Have you in any way changed or manipulated anything to do with Python on your system? Many Ubuntu system helper programs are written in Python 2.7, so if that is not available anymore in /usr/bin for any reason, you will get a plethora of error messages like that.

---

### Post by kirtan_parmar on 2014-12-05
I'm using ubuntu 14.04.
I'm currently learning python 2.7 but I'm quite sure that I haven't intentionally messed with some system programs or their like.
When i click on the 'show details' when the error message pops up it says executable path->usr/bin/update-manager, executable path->/usr/lib/update-notifier/apt_check.py and executable path-> /usr/share/apport/apport-gtk and then the window disappears altogether.
I am unable to attach the files here as it says invalid file.

---

### Post by kirtan_parmar on 2014-12-06
anyone please ?

---

### Post by ibjsb4 on 2014-12-06
Are you actually experiencing a problem?  If no system problem exist, then my solution is to disable "Apport".

[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

[https://www.google.com/search?client=ubuntu&channel=fs&q=disable+apport+ubuntu&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=disable+apport+ubuntu&ie=utf-8&oe=utf-8)

---

### Post by matt_symes on 2014-12-06
Hi

Another option:

You can also delete the crash reports and keep apport enabled. Then you can upload future crashes as long as apport does not crash.

```
sudo rm /var/crash/*
```

Kind regards

---

### Post by eight.coffee.beans on 2014-12-06
I had the same problem, but fixed it with the command that user above me gave.
Thanks for that matt_symes :)

---

