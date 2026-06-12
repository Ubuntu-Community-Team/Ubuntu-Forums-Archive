---
title: "Login hangs with NFS mount and doesn't load programs"
date: 2013-09-17
forum: General Help
---

### Post by morrcahn on 2013-09-17
I am experiencing a very curious issue in my computer lab. I believe this began after a regular apt-get update/upgrade on ubuntu 12.04.3 desktop.
I have an nfs server set up storing a hundred or so user accounts. We are using ldap to authenticate and create user accounts, and autofs for mounting to each of the eight lab workstations. 
We have different environments set up, and I'll list them along with the symptoms:
[LIST]
[*]ubuntu 2D, ubuntu, gnome, gnome classic, cinnamon, xterm, and xfce all show the 'fail whale' in the syslog upon login.
[LIST]
[*]> Sep 17 15:55:02 spartan gnome-session[22493]: WARNING: Application 'gnome-settings-daemon.desktop' failed to register before timeout
Sep 17 15:55:02 spartan gnome-session[22493]: [COLOR=#ff0000]CRITICAL: We failed, but the fail whale is dead. Sorry....[/COLOR]
Sep 17 15:55:32 spartan gnome-session[22493]: WARNING: Application 'compiz.desktop' failed to register before timeout
Sep 17 15:55:32 spartan NetworkManager[1052]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 17 15:55:33 spartan NetworkManager[1052]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 17 15:55:47 spartan NetworkManager[1052]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Sep 17 15:55:47 spartan goa[22636]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Sep 17 15:55:52 spartan gnome-session[22493]: WARNING: Could not launch application 'cinnamon-screensaver.desktop': Unable to start application: Failed to execute child process "cinnamon-screensaver" (No such file or directory)
Sep 17 15:56:53 spartan NetworkManager[1052]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
[*]Ubuntu will, upon login, SLOWLY load to a black screen, then SLOWLY load to the wallpaper, and then hang. After sitting the screen lock will activate. No panels load. Only the mouse. The above excerpt is from tail -f /var/log/syslog while this all took place. 
[*]Cinnamon does similarly but will load gnome-do 
[*]The rest load up what seems to be normally, but then won't run programs when selected, whether in gui or command line. 
[/LIST]
     
[/LIST]
If I create a user account local to the workstation, everything works fine. As soon as I mount something, it works as said above. 
If I ssh into a workstation, I can roam around there just fine as any user, with my files/folders all present. Even doing xterm from there, with gnome-session-fallback, it'll login, but programs won't load when called.
I turned off autofs and mounted nfs directly, yet that made no changes.

I've combed around in many log files, but I'm sure there are others I should check that I haven't yet discovered. I'm open for suggestions, because I really need this lab running within the next week and a half. Thank you in advance.

---

