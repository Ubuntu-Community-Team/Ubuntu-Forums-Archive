---
title: "Kodi-standalone not able to run from xession kodi.desktop"
date: 2015-02-07
forum: General Help
---

### Post by apokkalyps on 2015-02-07
This started after the upgrade from xbmc to kodi.

I can switch to gdm, and launch gnome, and from there run 'kodi-standalone' which launches kodi just fine.  So kodi works, and kodi-standalone works, when run from inside a regular desktop environment.  

However, being my htpc, I like this to boot into xbmc (kodi now) automatically like a kiosk.  I have an xbmc user which is and always has been configured with autologin.  I've always in the past used this lightdm.conf

```
[SeatDefaults]
autologin-user=xbmc
autologin-user-timeout=0
user-session=XBMC
greeter-session=lightdm-gtk-greeter
```

After the kodi update there were a couple problems, effectively amounting to lightdm just booting to a blinking terminal cursor.  
I figured out lightdm-gtk-greeter was just gone somehow, no longer even installed.  After apt-get install lightdm-gtk-greeter, now it boots to the lightdm-gtk-greeter.  

The updater tried to do some magic creating a link from /usr/share/xsessions/XBMC.desktop > kodi.desktop but to make things clear I have deleted that and am just working with the new kodi.desktop

lightdm.conf
```
[SeatDefaults]
autologin-user=xbmc
autologin-user-timeout=0
user-session=Kodi
greeter-session=lightdm-gtk-greeter
```

/usr/share/xsessions/kodi.desktop
```
[Desktop Entry]
Name=Kodi
Comment=This session will start Kodi Media Center
Exec=kodi-standalone
TryExec=kodi-standalone
Type=Application

```

Lightdm is trying to start kodi-standalone automatically like it is supposed to.  But somehow the process exits out (even though it works when I run it in gnome) and it returns back to the lightdm-gtk-greeter. 

```
[+2.17s] DEBUG: Got signal from X server :0
[+2.17s] DEBUG: Connecting to XServer :0
[+2.18s] DEBUG: Automatically logging in user xbmc
[+2.18s] DEBUG: Started session 1328 with service 'lightdm-autologin', user
name 'xbmc'
[+2.34s] DEBUG: Session 1328 authentication complete with return value 0: Success
[+2.34s] DEBUG: Autologin user xbmc authorized
[+2.39s] DEBUG: Autologin using session kodi
[+2.49s] DEBUG: Dropping privileges to uid 1001
[+2.49s] DEBUG: Restoring privileges
[+2.52s] DEBUG: Dropping privileges to uid 1001
[+2.52s] DEBUG: Writing /home/xbmc/.dmrc
[+2.52s] DEBUG: Restoring privileges
[+2.53s] DEBUG: Starting session kodi as user xbmc
[+2.53s] DEBUG: Session 1328 running command /usr/sbin/lightdm-session kodi-standalone
[+2.58s] DEBUG: New display ready, switching to it
[+2.58s] DEBUG: Activating VT 7
[+2.58s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+5.74s] DEBUG: Session 1328 exited with return value 0
[+5.74s] DEBUG: User session quit
[+5.74s] DEBUG: Stopping display
[+5.74s] DEBUG: Sending signal 15 to process 1197
[+6.06s] DEBUG: Process 1197 exited with return value 0
[+6.06s] DEBUG: X server stopped
[+6.06s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+6.06s] DEBUG: Releasing VT 7
[+6.06s] DEBUG: Display server stopped
[+6.06s] DEBUG: Display stopped
[+6.06s] DEBUG: Active display stopped, switching to greeter
[+6.06s] DEBUG: Switching to greeter
[+6.06s] DEBUG: Starting new display for greeter
```

 Same thing happens if I manually select Kodi as the session and login with xbmc user.  It tries to load kodi-standalone for about 2 seconds and returns to the greeter.

```
[+926.25s] DEBUG: Continue authentication
[+926.32s] DEBUG: Session 2043 authentication complete with return value 0: Success
[+926.32s] DEBUG: Authenticate result for user xbmc: Success
[+926.35s] DEBUG: User xbmc authorized
[+926.36s] DEBUG: Greeter requests session kodi
[+926.36s] DEBUG: Using session kodi
[+926.36s] DEBUG: Stopping greeter
[+926.36s] DEBUG: Session 1844: Sending SIGTERM
[+926.40s] DEBUG: Greeter closed communication channel
[+926.40s] DEBUG: Session 1844 exited with return value 0
[+926.40s] DEBUG: Greeter quit
[+926.45s] DEBUG: Dropping privileges to uid 1001
[+926.45s] DEBUG: Restoring privileges
[+926.49s] DEBUG: Dropping privileges to uid 1001
[+926.49s] DEBUG: Writing /home/xbmc/.dmrc
[+926.49s] DEBUG: Restoring privileges
[+926.49s] DEBUG: Starting session kodi as user xbmc
[+926.49s] DEBUG: Session 2043 running command /usr/sbin/lightdm-session kodi-standalone
[+926.54s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session1
[+928.79s] DEBUG: Session 2043 exited with return value 0
[+928.79s] DEBUG: User session quit
[+928.79s] DEBUG: Stopping display
[+928.79s] DEBUG: Sending signal 15 to process 1841
[+929.11s] DEBUG: Process 1841 exited with return value 0
[+929.11s] DEBUG: X server stopped
[+929.11s] DEBUG: Removing X server authority /var/run/lightdm/root/:0
[+929.11s] DEBUG: Releasing VT 7
[+929.11s] DEBUG: Display server stopped
[+929.11s] DEBUG: Display stopped
[+929.11s] DEBUG: Active display stopped, switching to greeter

```

Anyone have any ideas about this?  kodi-standalone works.  Lightdm works, it can give me a gnome session.  But it can't run kodi-standalone as the session.  A similar failure happens if I select the Kodi session from the unity greeter, and whatever greeter gdm uses.

---

### Post by durb999 on 2015-05-28
Hi apokkalyps
Did you manage to solve this? I have a similar problem although the error is different: lightdm appears to ignore the user-session and load an ubuntu session.

BR
Phil

---

### Post by QDR06VV9 on 2015-05-28
Maybe Related to this [http://forum.kodi.tv/showthread.php?tid=202142](http://forum.kodi.tv/showthread.php?tid=202142) Post#5

---

### Post by papu2 on 2015-06-18
i have the same problem and im using vivid 15.04. lightdm just wont login to the Kodi session in [SeatDefaults] and proceeds into xfce/ubuntu session

---

### Post by Jan_Kuijdenberg on 2015-08-27
Same issue here. 
I used Kodibuntu that autostarted Kodi before.
 Now, after upgrading to vivid 15.04 the autostart is not working anymore. Who knows what to do? suggestions appreciated.

---

