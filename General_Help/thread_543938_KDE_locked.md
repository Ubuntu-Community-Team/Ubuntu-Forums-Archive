---
title: "KDE locked??"
date: 2007-09-05
forum: General Help
---

### Post by Russty of Oz on 2007-09-05
I have just reinstalled Ubuntu Feisty and all seems to be working OK but some programs wont open, Kaffeine for example and when I tried to boot into KDE it wouldn't work.  I checked the .KDE file and it seems to be locked. (see attachment) 

How do I get access to KDE and does this have anything to do with Kaffeine not working?

Russty

---

### Post by chrono310 on 2007-09-05
It looks like there may be some weird permissions set on that folder... can you do an **ls -la** and paste the output here? I don't know what would have made that folder get created with the permissions set incorrectly.

Here's what my permissions look like on it:
```
devin@melchior:~$ ls -la
...
drwx------   5 devin devin    4096 2007-07-07 20:38 .kde
...
```

---

### Post by Russty of Oz on 2007-09-06
This is what I got with that command.  The KDE bit says root root rather than russty russty.???  I installed KDE via Synaptic just like I have done before and this has never happened.  

russty@russty-desktop:~$ ls -la
total 24044
drwxr-xr-x 59 russty russty     4096 2007-09-06 15:59 .
drwxr-xr-x  4 root   root       4096 2007-09-05 21:47 ..
-rw-r--r--  1 root   root          0 2007-09-05 19:45 1
drwxr-xr-x 25 russty russty     4096 2007-09-05 13:55 .amaya
srwx------  1 russty russty        0 2007-09-05 13:55 .amaya-check-instance
-rw-------  1 russty russty        6 2007-09-05 13:55 .amaya-russty
drwx------  9 russty russty     4096 2007-09-05 13:10 .amsn
drwx------  2 russty russty     4096 2007-09-05 13:05 amsn_received
drwxr-xr-x  2 russty root       4096 2007-09-05 19:51 .automatix
-rw-------  1 russty russty      601 2007-09-06 08:10 .bash_history
-rw-r--r--  1 russty russty      220 2007-09-05 21:47 .bash_logout
-rw-r--r--  1 russty russty     2298 2007-09-05 21:47 .bashrc
drwx------  7 russty russty     4096 2007-09-06 15:59 .beagle
drwxr-xr-x  2 russty russty     4096 2007-09-06 08:30 .beryl
-rw-r--r--  1 russty russty      185 2007-09-06 08:30 .beryl-managerrc
drwx------  5 russty russty     4096 2007-09-05 23:51 .config
drwxr-xr-x  2 russty russty     4096 2007-09-06 08:57 Desktop
-rw-------  1 russty russty       24 2007-09-06 08:03 .dmrc
drwxr-xr-x  4 russty russty     4096 2007-09-05 17:37 Documents
-rw-r--r--  1 russty russty    12772 2005-12-02 07:40 dvb-fe-or51132-qam.fw
-rw-r--r--  1 russty russty    17532 2005-12-02 07:40 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 russty russty     8518 2005-12-02 07:40 dvb-fe-or51211.fw
-rw-r--r--  1 russty russty   239956 2005-12-02 07:40 dvb-ttpci-01.fw
-rw-r--r--  1 russty russty    10757 2005-12-02 07:40 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 russty russty     9180 2005-12-02 07:40 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 russty russty     7558 2005-12-02 07:40 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 russty russty     7431 2005-12-02 07:40 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 russty russty     4286 2005-12-02 07:40 dvb-usb-umt-010-02.fw
-rw-r--r--  1 russty russty    10752 2005-12-02 07:40 dvb-usb-vp702x-01.fw
-rw-r--r--  1 russty russty    10752 2005-12-02 07:40 dvb-usb-vp7045-01.fw
-rw-r--r--  1 russty russty     8581 2005-12-02 07:40 dvb-usb-wt220u-01.fw
drwxr-xr-x  4 russty russty     4096 2007-09-05 18:50 .emerald
-rw-------  1 russty russty       16 2007-09-05 12:54 .esd_auth
lrwxrwxrwx  1 russty russty       26 2007-09-05 21:47 Examples -> /usr/share/example-content
drwxr-xr-x  8 russty russty     4096 2007-09-05 11:39 firefox
drwxr-xr-x  2 russty russty     4096 2007-09-05 14:47 .fontconfig
drwxr-xr-x  4 russty russty     4096 2007-09-05 20:03 .frostwire
drwxr-xr-x  3 russty russty     4096 2007-09-05 14:34 .fullcircle
drwx------  2 russty russty     4096 2007-09-05 22:41 .gambas
drwx------  5 russty russty     4096 2007-09-06 15:59 .gconf
drwx------  2 russty russty     4096 2007-09-06 15:59 .gconfd
-rw-r--r--  1 russty russty      368 2007-09-05 23:05 gendiapo.sh
drwxr-xr-x 21 russty russty     4096 2007-09-05 18:25 .gimp-2.2
-rw-r-----  1 russty russty        0 2007-09-06 07:54 .gksu.lock
drwxr-xr-x  4 russty russty     4096 2007-09-05 19:46 .gnome
drwx------ 14 russty russty     4096 2007-09-06 13:39 .gnome2
drwx------  2 russty russty     4096 2007-09-05 12:54 .gnome2_private
-rwxrwxrwx  1 russty russty       60 2007-09-05 21:47 .gnomerc
lrwxrwxrwx  1 russty russty       38 2007-09-05 19:45 googleearth -> /home/russty/google-earth//googleearth
drwx------  5 russty russty     4096 2007-09-05 21:53 .googleearth
drwxr-xr-x  9 russty russty     4096 2007-09-05 19:46 google-earth
-rwxr-xr-x  1 russty russty 23852601 2007-08-23 17:53 GoogleEarthLinux.bin
drwxr-xr-x  2 russty russty     4096 2007-09-05 14:43 .gstreamer-0.10
-rw-r--r--  1 russty russty      135 2007-09-05 12:54 .gtkrc-1.2-gnome2
-rw-------  1 russty russty      700 2007-09-06 15:59 .ICEauthority
drwxr-xr-x  2 russty russty     4096 2007-09-05 13:07 .icons
drwxr-xr-x  2 russty russty     4096 2007-09-05 20:03 Incomplete
drwx------  6 root   root       4096 2007-09-06 08:08 .kde
drwxr-xr-x  4 russty russty     4096 2007-09-05 19:31 .listen
drwx------  3 russty russty     4096 2007-09-05 13:31 .local
drwx------  3 russty russty     4096 2007-09-05 19:46 .loki
drwxr-xr-x  2 russty russty     4096 2007-09-05 19:22 .lyrics
drwx------  3 russty russty     4096 2007-09-05 13:30 .macromedia
-rw-r--r--  1 russty russty        2 2007-09-05 23:01 .mandvdconfig
drwx------  3 russty russty     4096 2007-09-05 12:54 .metacity
drwx------  3 russty russty     4096 2007-09-05 14:34 .mozilla
drwxr-xr-x  2 russty russty     4096 2007-09-05 23:26 .mplayer
drwxr-xr-x  3 russty russty     4096 2007-09-06 13:39 .nautilus
-rw-r--r--  1 russty russty     1031 2007-09-05 22:01 .nvidia-settings-rc
drwxr-xr-x  3 russty russty    20480 2007-09-05 11:39 Other
drwxr-xr-x  4 russty russty     4096 2007-09-05 18:28 Pictures
-rw-r--r--  1 russty russty      566 2007-09-05 21:47 .profile
drwxr-xr-x  2 russty russty     4096 2007-09-05 23:22 .qt
-rw-------  1 russty russty     1896 2007-09-06 08:57 .recently-used
-rw-r--r--  1 russty russty    23063 2007-09-06 13:37 .recently-used.xbel
drwxr-xr-x  2 russty russty     4096 2007-09-05 19:59 Shared
drwx------  3 russty russty     4096 2007-09-05 14:55 .Skype
-rw-r--r--  1 russty russty      247 2007-09-05 23:07 slideshow_23:05:11.xml
drwxr-xr-x 13 russty russty     4096 2007-09-05 22:36 Software
-rw-r--r--  1 russty russty        0 2007-09-05 12:54 .sudo_as_admin_successful
drwxr-xr-x  3 russty russty     4096 2007-09-05 17:56 .themes
drwx------  4 russty russty     4096 2007-09-05 14:46 .thumbnails
drwxr-xr-x  8 russty russty     4096 2007-09-05 11:39 thunderbird
drwx------  3 russty russty     4096 2007-09-05 14:34 .thunderbird
drwx------  2 russty russty     4096 2007-09-06 08:57 .Trash
drwx------  2 russty russty     4096 2007-09-05 19:30 .tvtime
drwxr-xr-x  2 russty russty     4096 2007-09-05 13:02 .update-manager-core
drwx------  2 russty russty     4096 2007-09-05 13:00 .update-notifier
drwxr-xr-x  7 russty russty     4096 2007-09-05 11:39 v4l-dvb
drwxr-xr-x  3 russty russty     4096 2007-09-05 23:46 vids
drwxr-xr-x  3 russty russty     4096 2007-09-05 19:32 .vlc
drwxr-xr-x  2 russty russty     4096 2007-09-06 15:59 .wapi
drwxr-xr-x  4 russty russty     4096 2007-09-05 23:58 .wine
-rw-------  1 russty russty      125 2007-09-06 15:59 .Xauthority
drwxr-xr-x  2 russty russty     4096 2007-09-05 14:46 .xine
drwxr-xr-x  4 russty russty     4096 2007-09-05 19:33 .xmms
-rw-r--r--  1 russty russty     1015 2007-09-06 15:59 .xsession-errors
russty@russty-desktop:~$

---

### Post by chrono310 on 2007-09-06
Ok, try running these commands to change the ownership and group membership:
```

sudo chown russty .kde
sudo chgrp russty .kde

```
Then try logging in to a KDE session and see if that works.

---

### Post by Russty of Oz on 2007-09-06
I have done that but it still won't load KDE.  I get this message:  **could not start kstartupconfig.  Check your installation**

the ls -la command now reads:

drwxrwxrwx  6 russty russty     4096 2007-09-06 08:08 .kde


The .kde folder now does not have the lock and "no entry" signs on it but the folders inside it do!

---

### Post by Russty of Oz on 2007-09-06
I have now done the above commands to all the folders inside the .kde folder and now I just get a blue screen when I try to boot into KDE.  Should I just uninstall KDE and reinstall again?

---

### Post by chrono310 on 2007-09-06
oh, oops... try doing it recursively so it changes everything in the subdirectories:
```

sudo chown -R russty .kde
sudo chgrp -R russty .kde

```

---

### Post by Russty of Oz on 2007-09-07
Many Thanks to you!  IT WORKED!  :):guitar:

I wonder why it was like  that?  I have done quite a few installs of Ubuntu over the past year or so and that has never happened before. 

So thank you again, now I can get on!

Russty.):P

---

### Post by chrono310 on 2007-09-07
Yeah, that was pretty strange... I've never seen it do that before.

Glad I could help!

---

### Post by bogdan_5844 on 2007-09-07
please mark the thread as solved
thanks ;-) :KS

---

