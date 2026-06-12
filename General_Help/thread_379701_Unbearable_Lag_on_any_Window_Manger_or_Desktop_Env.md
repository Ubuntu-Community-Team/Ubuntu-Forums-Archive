---
title: "Unbearable Lag on any Window Manger or Desktop Environment"
date: 2007-03-08
forum: General Help
---

### Post by finferflu on 2007-03-08
Hi all,
today it's been a very frustrating day. I've been switching DEs and WMs, restarting sessions and rebooting the whole day. I don't know what's going on, but my system starts loading something I don't know, and it loads forever and ever. At times I can't even move the pointer anymore, I tried to wait even about 20 mins with no improvement of the situation. The only thing to do was restarting the session, but then again it happens... The weird thing is that I have the same problem everywhere, no matter which DE or WM I choose, Gnome, KDE, XFCE, E17, IceWM, OpenBox, no difference... 
The other weird thing is that I can't see any very busy process running with top..

Does anybody have any suggestion? Any debugging hint to know where this problem is coming from?
It's getting really really frustrating, and the system non productive and useless.

Thanks a lot!

---

### Post by kerry_s on 2007-03-08
With all those on 1 system did you not expect problems?

Try nano'ing in to your open box startup and comment out any apps you have auto starting, It's most likely your mixing apps from the different systems and one of them is having problems starting and gets caught in a loop. Try looking at your .xsession-errors file and see if there's any clue, if that doesn't help, try looking through your logs.

Sometimes it's best to install different setups on separate partions, so you don't get interference and you will always have a backup system.

---

### Post by finferflu on 2007-03-08
Thanks!
Actually I've been using them from a long time, and had no problems.. It just started today, out of the blue, while I was using XFCE, I was doing some upgrades (but it started before they were complete) with update_notifier... since then, it lags unpredictably whenever I open an app sometimes, but it doesn't do the same thing twice with the same app...

Thanks for the hints anyway, I'll look into them!

---

### Post by kerry_s on 2007-03-08
Have you found anything in your logs?

---

### Post by finferflu on 2007-03-08
This is my xsession-errors:

```

Xsession: X session started for mmanu at Fri Mar  9 00:54:51 GMT 2007
/etc/X11/Xsession.d/40guidance-displayconfig_restore: line 11: /usr/bin/displayconfig-restore: No such file or directory
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
ESTART: 0.00001 [0.00001] - begin
ESTART: 0.00015 [0.00014] - signals done
ESTART: 0.00032 [0.00017] - determine prefix
DYNAMIC DETERMINED PREFIX: /usr
ESTART: 0.03833 [0.03801] - prefix done
ESTART: 0.03847 [0.00014] - intl init
ESTART: 0.03859 [0.00012] - parse args
ESTART: 0.03861 [0.00002] - arg parse done
ESTART: 0.06469 [0.02607] - edje init
ESTART: 0.06491 [0.00023] - ecore init
ESTART: 0.06544 [0.00053] - ecore_file init
ESTART: 0.06565 [0.00021] - more ecore
ESTART: 0.06570 [0.00004] - x connect
ESTART: 0.07477 [0.00907] - xinerama
E17 INIT: XINERAMA CHOSEN: [0], 1024x768+0+0
ESTART: 0.07534 [0.00057] - x hints
ESTART: 0.07579 [0.00045] - x hints done
ESTART: 0.07582 [0.00003] - ecore_con
ESTART: 0.07588 [0.00005] - ecore_desktop
ESTART: 0.30028 [0.22440] - ecore_desktop done
ESTART: 0.30033 [0.00005] - ecore_desktop paths
ESTART: 0.30061 [0.00028] - ecore_desktop paths done
ESTART: 0.30062 [0.00001] - ecore_evas init
ESTART: 0.39620 [0.09557] - test file format support
ESTART: 0.51024 [0.11404] - test done
ESTART: 0.51029 [0.00006] - thumb init
ESTART: 0.51031 [0.00002] - sys init
ESTART: 0.51033 [0.00002] - dirs
ESTART: 0.58292 [0.07259] - filereg
ESTART: 0.58297 [0.00005] - config
ESTART: 0.58765 [0.00468] - path
ESTART: 0.58781 [0.00016] - intl post
ESTART: 0.72503 [0.13722] - actions
ESTART: 0.73838 [0.01334] - bindings
ESTART: 0.73850 [0.00012] - popup
ESTART: 0.73853 [0.00003] - font
ESTART: 0.73868 [0.00016] - theme
ESTART: 0.74722 [0.00853] - bg
ESTART: 0.74729 [0.00007] - splash
ESTART: 0.90686 [0.15957] - screens
ESTART: 0.90693 [0.00007] - screens: atoms
ESTART: 0.90778 [0.00085] - screens: manager
ESTART: 0.90786 [0.00009] - screens: container
ESTART: 0.90789 [0.00003] - screens: zone
ESTART: 0.90790 [0.00001] - screens: desk
ESTART: 0.90791 [0.00001] - screens: menu
ESTART: 0.90793 [0.00001] - screens: exehist
ESTART: 0.90795 [0.00002] - screens: get roots
ESTART: 0.90796 [0.00002] - screens: focus
ESTART: 0.90797 [0.00001] - screens: border
ESTART: 0.90800 [0.00003] - screens: win
ESTART: 0.90801 [0.00001] - screens: manage roots
ESTART: 0.99702 [0.08901] - screens: sync
ESTART: 0.99713 [0.00010] - apps
ESTART: 0.99835 [0.00122] - remember
ESTART: 0.99839 [0.00004] - container freeze
ESTART: 0.99842 [0.00003] - ipc
INFO: E_IPC_SOCKET=/tmp/enlightenment-mmanu/disp-:0.0-11094
ESTART: 1.02173 [0.02331] - fm2
ESTART: 1.02221 [0.00049] - msg
ESTART: 1.02225 [0.00004] - dnd
ESTART: 1.02227 [0.00002] - grabinput
ESTART: 1.02228 [0.00001] - modules
ESTART: 1.02229 [0.00001] - winlist
ESTART: 1.02230 [0.00001] - colorclasses
ESTART: 1.02232 [0.00001] - load modules
ESTART: 1.14887 [0.12656] - gadcon
ESTART: 1.14893 [0.00006] - shelves
ESTART: 1.14894 [0.00001] - exebuf
ESTART: 1.14896 [0.00002] - dpms
ESTART: 1.15541 [0.00645] - screensaver
ESTART: 1.15547 [0.00006] - desklock
ESTART: 1.15549 [0.00002] - add idle enterers
ESTART: 1.15558 [0.00009] - init properites
ESTART: 2.10285 [0.94726] - test code
ESTART: 2.10291 [0.00006] - shelf config init
ESTART: 2.49540 [0.39249] - MAIN LOOP AT LAST
[ecore_dbus] ecore_dbus_server: 0x81d78a8 ecore_con_server: 0x81d78d8 sent 1 of 1 bytes
[ecore_dbus] ecore_dbus_server: 0x81d78a8 ecore_con_server: 0x81d78d8 sent 6 of 6 bytes
[ecore_dbus] begining auth process
[ecore_dbus] auth type EXTERNAL started
[ecore_dbus] ecore_dbus_server: 0x81d78a8 ecore_con_server: 0x81d78d8 sent 24 of 24 bytes
ESTART: 3.36079 [0.86539] - SLEEP
[ecore_dbus] auth type EXTERNAL successful
[ecore_dbus] ecore_dbus_server: 0x81d78a8 ecore_con_server: 0x81d78d8 sent 7 of 7 bytes
[ecore_dbus] ecore_dbus_server: 0x81d78a8 ecore_con_server: 0x81d78d8 sent 128 of 128 bytes
[ecore_dbus] received server data, 260 bytes
[ecore_dbus] unmarshaling
[ecore_dbus] dbus message length 90 bytes, still 170
Got unique name: :1.30
[ecore_dbus] unmarshaling
[ecore_dbus] dbus message length 170 bytes, still 0
[ecore_dbus] ecore_dbus_server: 0x81d78a8 ecore_con_server: 0x81d78d8 sent 168 of 168 bytes
[ecore_dbus] received server data, 84 bytes
[ecore_dbus] unmarshaling
[ecore_dbus] dbus message length 84 bytes, still 0
E FM: DBus Add listener for devices
[ecore_dbus] ecore_dbus_server: 0x81d78a8 ecore_con_server: 0x81d78d8 sent 267 of 267 bytes
[ecore_dbus] received server data, 72 bytes
[ecore_dbus] unmarshaling
[ecore_dbus] dbus message length 72 bytes, still 0
E FM: DBus Should be listening for device changes!
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/Applications-kmag.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/Applications-kmousetool.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/gyachi.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-adept_manager.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-akregator.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-digikam.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-groupwarewizard.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-gwenview.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-juk.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-kaffeine.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-karm.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-katapult.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-kaudiocreator.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-kbtobexclient.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-kbtserialchat.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-kcron.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-keep.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-knotes.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-Kontact.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-konversation.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-kooka.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-kopete.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-kpdf.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-Kppp.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-krdc.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-krfb.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-krita.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-kscd.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-ksnapshot.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-ksystemlog.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-ktorrent.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/kde-wlassistant.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/Mozilla-mail-composer.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/Mozilla-mail.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/Mozilla-news.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/Office-kpresenter.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/Office-KThesaurus.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/speedcrunch.desktop
ERROR: Cannot Open File /home/mmanu/.e/e/applications/all/Utilities-skim.desktop

```

Do you see anything in particular in that?
I also don't know where to look for the other logs..

EDIT: Is this file only relating to my current session?

---

### Post by finferflu on 2007-03-09
I'm not sure, but I think I've solved the problem (in a very trivial way), since it seems fine so far...
I've just uninstalled some WMs and DEs, like KDE, IceWM, FVWM, Fluxbox.... and so on..
I guess my testing has come to an end, and I shall stick with XFCE/E17, keeping Gnome as a companion to XFCE, since I haven't got any other use for such a slow DE.

---

### Post by kerry_s on 2007-03-09
You live, you learn. I use to do the same thing back in the day, but now i do separate installs for each WM/DE in it's own partions. You'll aways have one of the working installs to fall back on, just in case you play to hard, plus it leaves you free to try things with out worry. :)

---

### Post by finferflu on 2007-03-09
Well, it doesn't matter anymore I think... I found out that my method didn't work, lost my temper (I know I'm a jerk) and eventually managed to break my HD with a punch (see [here]("http://ubuntuforums.org/showthread.php?t=380237")).
I'm running Knoppix LiveCD at the moment, and fortunately I can still access my files, even though I can't install anything.. I must say that even though it's a LiveCD it's much faster than my Ubuntu install!!! and this makes me even more nervous about the slowness of my *past* system.. that's unbeliavable... I need a HD by the way...

---

### Post by kerry_s on 2007-03-09
LOL, i understand, i got pissed off at mine a long while back and slammed the hd down on the table, i ended up running DSL in ram with a usb key for swap for about 6 months till the rest of the laptop gave out. I always treat my systems as disposable and back up to a external hd any important info.

---

### Post by 3ntity on 2007-03-18
Hey,
I had this very same problem running Edgy, with a basic install; updates and standard things like multimedia codecs, ... See [this]("http://www.ubuntuforums.org/showthread.php?t=305615") link for a topic i started. Noone was able to suggest any solutions, so i switched back to windows for a while. I switched back a little back [windows is hopeless, really, i don't know why i switched back, i guess just laziness]; after only a few days Edgy was showing the same problem again. So, i switched back to Dapper [Gnome], which has been running quite smoothly. 
Just letting you know you're not the only one who's had this problem :)
Anyways, glad to know you solved your hard drive's problem.

---

### Post by finferflu on 2007-03-18
Just don't smash your hard drive :D

On my new install I've installed XFCE, and it's smooooth as ever! You should try it out, it's not that different from Gnome...

---

### Post by finferflu on 2007-03-22
oh NOOOO!!!
I've got the same problem again, with a new install and new hard disk... I guess there must be something dodgy in Xfce, since it happens always while I'm using it. So, I've uninstalled Xfce, but it's still very very laggy. I'm sick of this, and sick of reinstalling. So for now I'll stick with Sidux, and reinstall everything when Feisty comes out...

---

### Post by 3ntity on 2007-04-05
that really sucks man :/
i'm sticking with 6.06 which is running like a charm till 7.04 comes out :) [which shouldn't be long anymore :D]
... is that Sidux any good? i only have experience with Ubuntu and Knoppix...

---

### Post by finferflu on 2007-04-05
Indeed! I've done a clean Xubuntu install, and it seems to work now... *so far*
Sidux is quite fast, it's based on Debian Sid, it is Debian Sid, with some default configuration to make it simpler, anyway I managed to make that slow as well, I guess there's something wrong with GTK, as soon as I touch it, things become messy. But Sidux is quite a pleasant experience, and the nice thing is that you can dist-upgrade daily, and have your system always up to date, without waiting for new releases. By the way, I think it has something to do with Knoppix, the boot up looks even the same...

---

