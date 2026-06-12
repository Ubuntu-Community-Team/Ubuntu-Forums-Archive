---
title: "VLC not working"
date: 2012-10-29
forum: General Help
---

### Post by awdheshgupta1311 on 2012-10-29
ubuntu 10.04 is installed in my computer. VLC media player is not working. when i hit 'vlc' in terminal, the error below showed -
" [COLOR=Red]ubuntu@ubuntu-linux:~$ vlc
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to srand(1351496515)
Warning: call to rand()
[0x84bd67c] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x84e2afc] main interface error: option qt-volume-complete does not exist
[0x84e2afc] skins2 interface error: no suitable dialogs provider found (hint: compile the qt4 plugin, and make sure it is loaded properly)
[0x84e2afc] skins2 interface error: cannot instanciate qt4 dialogs provider
[0x84bd67c] main libvlc error: interface "default" initialization failed"


[/COLOR]

---

### Post by shreepads on 2012-10-29
How did you get this version of VLC installed on 10.04, from the standard repositories?

If so, what happens when you try to start VLC from the app menu?

If not, what steps did you take to install/ build VLC?

---

