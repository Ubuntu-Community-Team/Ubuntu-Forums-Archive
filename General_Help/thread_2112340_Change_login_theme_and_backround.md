---
title: "Change login theme and backround?"
date: 2013-02-04
forum: General Help
---

### Post by einstein**-7 on 2013-02-04
Ok, so I've tried just about every thing a google search would turn up on this and nothing works!  I havn't tried manually swapping the actual image that the greeter uses or editing the config that tells it where the path to the image is simply because i also want to change the theme.
Both 'simple lightdm manager' and 'ubuntu tweak' appear to work but no change!
I'm a little confused as to what window manager is actually being used tdm, lightdm etc..
My desktop is using unity.

thanks!
thanks!

---

### Post by grahammechanical on 2013-02-04
So, what is your question? If you are using a standard/default Ubuntu with Unity, then the login  will be controlled by LightDM. 

What is tdm? Do you mean GDM? Gnome Display Manager? That is not installed by default in standard Ubuntu. A person would have to download it through the Software Centre and then use the command-line to stop lightdm and then start gdm.

Have you downloaded GDM? Open Ubuntu Software Centre and search for gdm. If there is a green circle with a white tick mark icon set against the search result then you have downloaded GDM. No green icon = not downloaded. Lightdm is the login display manager. Unless of course you have installed some other display manager.

When we select a static background wallpaper, then Lightdm uses that as its background also. If we set the desktop background to change images through the day, then Lightdm uses the default image called warty-final-ubuntu.png. You can find in /usr/share/backgrounds.

It would help if you told us the version of Ubuntu that you are using. Things change from version to version. Things are done differently in different versions.

Regards.

---

### Post by einstein**-7 on 2013-02-04
Checked in synaptic and gdm and lightdm are both installed however no lightdm- greeter package is installed.
My version of ubuntu is 12.04.

---

### Post by Frogs Hair on 2013-02-04
If you have noticed Ubuntu Tweak will allow choose a different wallpaper than the desktop. As stated above the procedure for changing the greeter will vary depending on Ubuntu version. The link may be related.     [http://askubuntu.com/questions/75755/how-to-change-the-lightdm-theme-greeter](http://askubuntu.com/questions/75755/how-to-change-the-lightdm-theme-greeter)

---

### Post by einstein**-7 on 2013-02-04
I just looked at the lightdm config files explained in the link and all is correct lightdm uses 
unity- greeter  for greeter session and the unity-greeter config shows the correct backround "not current one".
So maybe gdm is running at login? how can i check which is running??

---

### Post by kanikilu on 2013-02-04
> **einstein**-7 said:**
> So maybe gdm is running at login? how can i check which is running?? Just check the running processes, either with the System Monitor, or in the terminal. Something like this would work: ```
ps -ef | grep dm
```

---

### Post by einstein**-7 on 2013-02-04
> **kanikilu said:**
> Just check the running processes, either with the System Monitor, or in the terminal. Something like this would work: ```
ps -ef | grep dm
```
Did this and all ref's were for gdm processes no lightdm,  confirmed this by switching to runtime1 and after login doing sudo gdm start and sudo lightdm start.
Lightdm shows the custom login with correct backround -- gdm shows the current login!
A couple months ago I was having login  issues and switched to gdm just didn't remember what i did-- just followed directions.
This was happening at the time [login bounces back]("http://ubuntuforums.org/showthread.php?t=2003976") still happens when starting lightdm and logging in.  Is there any way to reset lightdm's config files to fix this?

---

### Post by einstein**-7 on 2013-02-04
Here are the logs from
lightdm
```
[+0.00s] DEBUG: Logging to /var/log/lightdm/lightdm.log
[+0.00s] DEBUG: Starting Light Display Manager 1.2.1, UID=0 PID=1266
[+0.00s] DEBUG: Loaded configuration from /etc/lightdm/lightdm.conf
[+0.00s] DEBUG: Using D-Bus name org.freedesktop.DisplayManager
[+0.00s] DEBUG: Registered seat module xlocal
[+0.00s] DEBUG: Registered seat module xremote
[+0.00s] DEBUG: Adding default seat
[+0.00s] DEBUG: Starting seat
[+0.00s] DEBUG: Starting new display for greeter
[+0.00s] DEBUG: Starting local X display
[+0.00s] DEBUG: X server :0 will replace Plymouth
[+0.02s] DEBUG: Using VT 7
[+0.02s] DEBUG: Activating VT 7
[+0.02s] DEBUG: Logging to /var/log/lightdm/x-0.log
[+0.03s] DEBUG: Writing X server authority to /var/run/lightdm/root/:0
[+0.03s] DEBUG: Launching X Server
[+0.03s] DEBUG: Launching process 1285: /usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none
[+0.03s] DEBUG: Waiting for ready signal from X server :0
[+0.03s] DEBUG: Acquired bus name org.freedesktop.DisplayManager
[+0.03s] DEBUG: Registering seat with bus path /org/freedesktop/DisplayManager/Seat0
[+2.12s] DEBUG: Got signal 10 from process 1285
[+2.12s] DEBUG: Got signal from X server :0
[+2.12s] DEBUG: Stopping Plymouth, X server is ready
[+2.14s] DEBUG: Connecting to XServer :0
[+2.28s] DEBUG: Starting greeter
[+2.28s] DEBUG: Started session 1600 with service 'lightdm', username 'lightdm'
[+2.39s] DEBUG: Session 1600 authentication complete with return value 0: Success
[+2.39s] DEBUG: Greeter authorized
[+2.39s] DEBUG: Logging to /var/log/lightdm/x-0-greeter.log
[+2.39s] DEBUG: Session 1600 running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+2.65s] DEBUG: Greeter connected version=1.2.1
[+2.65s] DEBUG: Greeter connected, display is ready
[+2.65s] DEBUG: New display ready, switching to it
[+2.65s] DEBUG: Activating VT 7
[+3.54s] DEBUG: Greeter start authentication for crush
[+3.54s] DEBUG: Started session 1968 with service 'lightdm', username 'crush'
[+3.55s] DEBUG: Session 1968 got 1 message(s) from PAM
[+3.55s] DEBUG: Prompt greeter with 1 message(s)
[+14.99s] DEBUG: Greeter start authentication for temp
[+14.99s] DEBUG: Session 1968: Sending SIGTERM
[+14.99s] DEBUG: Started session 2123 with service 'lightdm', username 'temp'
[+15.00s] DEBUG: Session 2123 got 1 message(s) from PAM
[+15.00s] DEBUG: Prompt greeter with 1 message(s)
[+19.98s] DEBUG: Continue authentication
[+20.21s] DEBUG: Session 2123 authentication complete with return value 0: Success
[+20.21s] DEBUG: Authenticate result for user temp: Success
[+20.22s] DEBUG: User temp authorized
[+20.22s] DEBUG: Greeter requests session ubuntu
[+20.22s] DEBUG: Using session ubuntu
[+20.22s] DEBUG: Stopping greeter
[+20.22s] DEBUG: Session 1600: Sending SIGTERM
[+20.26s] DEBUG: Session 1600 exited with return value 0
[+20.26s] DEBUG: Greeter quit
[+20.28s] DEBUG: Dropping privileges to uid 1001
[+20.28s] DEBUG: Restoring privileges
[+20.29s] DEBUG: Dropping privileges to uid 1001
[+20.29s] DEBUG: Writing /home/temp/.dmrc
[+20.35s] DEBUG: Restoring privileges
[+20.39s] DEBUG: Starting session ubuntu as user temp
[+20.39s] DEBUG: Session 2123 running command /usr/sbin/lightdm-session gnome-session --session=ubuntu
[+20.41s] DEBUG: Registering session with bus path /org/freedesktop/DisplayManager/Session0
[+20.44s] DEBUG: Greeter closed communication channel
```

And
unity-greeter

```
** (process:1699): WARNING **: unity-greeter.vala:808: Error starting the at-spi registry: Failed to execute child process "/usr/lib/at-spi2-core/at-spi-bus-launcher" (No such file or directory)
[+0.00s] DEBUG: unity-greeter.vala:816: Starting unity-greeter 0.2.8 UID=116 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:819: Setting cursor
[+0.01s] DEBUG: unity-greeter.vala:823: Creating background surface
[+0.01s] DEBUG: unity-greeter.vala:826: Loading command line options
[+0.01s] DEBUG: unity-greeter.vala:854: Setting GTK+ settings
[+0.05s] WARNING: Theme parsing error: gtk.css:17:45: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:18:45: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:19:43: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:20:43: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:21:52: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:22:52: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:24:51: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:25:51: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:27:52: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:28:52: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:29:42: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:31:59: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:32:59: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:34:58: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:35:58: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:37:49: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:38:49: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:39:49: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:41:44: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:42:55: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:43:58: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:44:58: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:46:52: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:47:52: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:50:48: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:51:49: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:53:47: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:54:51: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:56:62: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:57:62: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:58:56: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:60:58: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:62:50: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:63:51: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:64:51: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:65:51: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:67:49: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:68:52: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:70:56: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:72:67: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:74:48: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:76:61: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:77:61: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:79:46: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:80:46: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:82:40: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:84:53: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:85:53: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:88:52: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:90:39: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:91:42: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:92:40: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:93:42: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:104:47: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:105:47: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:106:56: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:107:56: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:109:44: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:110:44: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:112:53: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:113:53: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:115:41: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk.css:116:41: Expected ',' in color definition
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:19:14: Not using units is deprecated. Assuming 'px'.
[+0.05s] WARNING: Theme parsing error: gtk-widgets.css:63:21: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:117:15: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:120:19: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:121:20: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:153:20: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:163:14: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:186:36: Junk at end of value
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:188:19: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:189:20: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:203:14: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:216:20: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:228:20: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:240:14: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:305:19: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:306:20: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:337:19: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:338:20: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:348:14: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:354:19: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:367:18: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:368:20: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:376:14: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:398:19: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:432:14: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:432:16: Not using units is deprecated. Assuming 'px'.
[+0.06s] WARNING: Theme parsing error: gtk-widgets.css:475:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:487:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:488:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:499:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:507:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:516:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:524:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:545:44: Expected ')' in color definition
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:567:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:579:14: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:627:14: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:642:14: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:647:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:650:14: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:659:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:683:22: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:712:32: Junk at end of value
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:718:32: Junk at end of value
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:723:36: Junk at end of value
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:728:36: Junk at end of value
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:771:56: Error opening file: No such file or directory
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:802:14: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:845:14: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:867:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:868:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:882:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:883:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:899:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:900:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:915:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:916:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:928:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:929:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:940:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:952:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:959:14: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:963:20: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:964:19: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:973:14: Not using units is deprecated. Assuming 'px'.
[+0.07s] WARNING: Theme parsing error: gtk-widgets.css:977:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:978:19: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:989:14: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:993:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:994:19: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1011:19: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1012:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1021:19: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1022:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1044:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1063:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1077:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1099:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1116:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1131:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1145:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1155:14: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1164:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1170:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1178:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1193:19: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1265:14: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1314:36: Expected ',' in color definition
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1323:47: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1341:40: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1342:52: Missing opening bracket in color definition
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1349:52: Missing opening bracket in color definition
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1350:40: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1356:20: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1359:14: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1367:66: Expected ',' in color definition
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1382:47: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1383:36: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1395:26: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1403:40: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1404:29: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1412:41: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1413:30: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1421:38: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1422:27: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1426:32: Expected ',' in color definition
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1470:31: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1480:36: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1503:19: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1504:31: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1518:19: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1519:40: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1532:19: Not using units is deprecated. Assuming 'px'.
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1533:40: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1550:31: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1555:42: Junk at end of value
[+0.08s] WARNING: Theme parsing error: gtk-widgets.css:1560:31: Junk at end of value
[+0.08s] DEBUG: unity-greeter.vala:877: Creating Unity Greeter
[+0.08s] DEBUG: Connecting to display manager...
[+0.08s] DEBUG: Wrote 17 bytes to daemon
[+0.08s] DEBUG: Read 8 bytes from daemon
[+0.08s] DEBUG: Read 120 bytes from daemon
[+0.08s] DEBUG: Connected version=1.2.1 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true
[+0.10s] WARNING: unity-greeter.vala:130: Failed to load state from /var/lib/lightdm/.cache/unity-greeter/state: Key file contains line '&#65533;' which is not a key-value pair, group, or comment

[+0.12s] DEBUG: menubar.vala:318: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.30s] CRITICAL: g_error_free: assertion `error != NULL' failed
[+0.30s] DEBUG: get entries
[+0.30s] DEBUG: menubar.vala:511: Adding indicator object 0x2446078 at position 0
[+0.30s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.30s] DEBUG: Checking against 2 possible times
[+0.64s] DEBUG: Guessing max time width: 62
[+0.64s] DEBUG: get entries
[+0.64s] DEBUG: menubar.vala:511: Adding indicator object 0x24ba1a8 at position 1
[+0.64s] WARNING: IndicatorObject class does not have an accessible description.
[+0.64s] WARNING: IndicatorObject class does not have an accessible description.
[+0.64s] DEBUG: get entries
[+0.64s] DEBUG: get entries
[+0.64s] DEBUG: menubar.vala:511: Adding indicator object 0x2435ed8 at position 2
[+0.64s] DEBUG: menubar.vala:335: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/gnome-fallback.desktop (GNOME Classic (No effects), This session logs you into GNOME with the traditional panel without any graphical effect.)
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/ubuntu-2d.desktop (Ubuntu 2D, This session logs you into Ubuntu 2D Mode)
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock-fallback.desktop (Cairo-Dock (Gnome No effects), This session logs you into GNOME with Cairo-Dock and without any graphical effect.)
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock-unity.desktop (Cairo-Dock (with Unity Panel), This session logs you into GNOME with Cairo-Dock and Unity-2D panel)
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/gnome-shell.desktop (GNOME, This session logs you into GNOME)
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/cairo-dock.desktop (Cairo-Dock (Gnome + Effects), This session logs you into GNOME with Cairo-Dock and with graphical effects.)
[+0.65s] DEBUG: Ignoring session /usr/share/xsessions/gnome.desktop
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/xterm.desktop (Recovery Console, Failsafe session with only xterm)
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/xsession.desktop (User Defined Session, Custom ~/.xsession script)
[+0.65s] DEBUG: Loaded session /usr/share/xsessions/gnome-classic.desktop (GNOME Classic, This session logs you into GNOME with the traditional panel)
[+0.65s] DEBUG: session-chooser.vala:42: Adding session cairo-dock (Cairo-Dock (Gnome + Effects))
[+0.65s] DEBUG: session-chooser.vala:42: Adding session cairo-dock-fallback (Cairo-Dock (Gnome No effects))
[+0.65s] DEBUG: session-chooser.vala:42: Adding session cairo-dock-unity (Cairo-Dock (with Unity Panel))
[+0.65s] DEBUG: session-chooser.vala:42: Adding session gnome-shell (GNOME)
[+0.65s] DEBUG: session-chooser.vala:42: Adding session gnome-classic (GNOME Classic)
[+0.65s] DEBUG: session-chooser.vala:42: Adding session gnome-fallback (GNOME Classic (No effects))
[+0.65s] DEBUG: session-chooser.vala:42: Adding session xterm (Recovery Console)
[+0.65s] DEBUG: session-chooser.vala:42: Adding session ubuntu (Ubuntu)
[+0.65s] DEBUG: session-chooser.vala:42: Adding session ubuntu-2d (Ubuntu 2D)
[+0.65s] DEBUG: session-chooser.vala:42: Adding session xsession (User Defined Session)
[+0.73s] DEBUG: Setting keyboard layout to 'us'
[+0.75s] DEBUG: main-window.vala:98: Screen is 2800x900 pixels
[+0.75s] DEBUG: main-window.vala:104: Monitor 0 is 1360x768 pixels at 0,0
[+0.75s] DEBUG: main-window.vala:104: Monitor 1 is 1440x900 pixels at 1360,0
[+0.75s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.75s] DEBUG: Loading user /org/freedesktop/Accounts/User1000
[+0.76s] DEBUG: Loading user /org/freedesktop/Accounts/User1001
[+0.78s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.78s] DEBUG: unity-greeter.vala:327: Adding/updating user crush (Crush)
[+0.78s] DEBUG: unity-greeter.vala:327: Adding/updating user temp (Temp)
[+0.78s] DEBUG: unity-greeter.vala:184: Adding guest account entry
[+0.97s] DEBUG: unity-greeter.vala:496: Failed to write state: Error writing to file: Bad address
[+0.97s] DEBUG: Starting authentication for user crush...
[+0.97s] DEBUG: Wrote 21 bytes to daemon
[+0.97s] DEBUG: unity-greeter.vala:880: Showing greeter
[+0.97s] DEBUG: unity-greeter.vala:352: Showing main window
[+0.97s] DEBUG: New style for time label
[+0.97s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.97s] DEBUG: Checking against 2 possible times
[+0.97s] DEBUG: Guessing max time width: 62
[+0.98s] DEBUG: background.vala:315: Regenerating backgrounds
[+0.98s] DEBUG: background.vala:67: Making background /usr/share/backgrounds/Ubuntu-Wallpaper-Images.png at 1360x768,1440x900
[+0.98s] DEBUG: New style for time label
[+0.98s] DEBUG: Evaluating bitmask for '%l:%M %p'
[+0.98s] DEBUG: Checking against 2 possible times
[+0.98s] DEBUG: Guessing max time width: 62
[+1.00s] DEBUG: unity-greeter.vala:893: Starting main loop
[+1.00s] DEBUG: Read 8 bytes from daemon
[+1.00s] DEBUG: Read 35 bytes from daemon
[+1.00s] DEBUG: Prompt user with 1 message(s)
[+1.03s] WARNING: Getting layout failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such interface `com.canonical.dbusmenu' on object at path /com/canonical/indicator/users/menu
[+1.03s] DEBUG: Num devices: '0'

[+1.03s] MESSAGE: Couldn't find primary device
[+1.03s] DEBUG: Num devices: '0'

[+1.03s] DEBUG: icon_policy is: 0 (present==0, charge==1, never==2)
[+1.03s] DEBUG: count_batteries found 0 batteries (0 are charging/discharging)
[+1.03s] DEBUG: should_be_visible: no
[+1.03s] DEBUG: menubar.vala:519: Removing indicator object 0x2435d58
[+1.03s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.03s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.03s] WARNING: invalid cast from `GtkMenuItem' to `IndicatorMenuItem'
[+1.03s] WARNING: menubar.vala:531: Indicator object 0x2435d58 not in menubar
[+1.03s] DEBUG: notify visible signal received
[+1.03s] CRITICAL: ido_calendar_menu_item_set_date: assertion `IDO_IS_CALENDAR_MENU_ITEM(menuitem)' failed
[+1.03s] DEBUG: New calendar item
[+1.04s] DEBUG: unity-greeter.vala:310: starting system-ready sound
[+2.36s] DEBUG: background.vala:67: Making background /home/crush/Pictures/mthighwestA.png at 1360x768,1440x900
[+2.36s] DEBUG: Setting keyboard layout to 'us'
[+2.38s] DEBUG: background.vala:116: Render of background /usr/share/backgrounds/Ubuntu-Wallpaper-Images.png complete
[+2.40s] DEBUG: indicator-sound: new_volume_slider_widget
[+2.40s] DEBUG: indicator-sound: new_voip_slider_widget
[+4.21s] DEBUG: background.vala:116: Render of background /home/crush/Pictures/mthighwestA.png complete
[+12.42s] DEBUG: unity-greeter.vala:496: Failed to write state: Error writing to file: Bad address
[+12.42s] DEBUG: Starting authentication for user temp...
[+12.42s] DEBUG: Wrote 20 bytes to daemon
[+12.43s] DEBUG: Read 8 bytes from daemon
[+12.43s] DEBUG: Read 34 bytes from daemon
[+12.43s] DEBUG: Prompt user with 1 message(s)
[+12.79s] DEBUG: Setting keyboard layout to 'us'
[+17.41s] DEBUG: Providing response to display manager
[+17.41s] DEBUG: Wrote 25 bytes to daemon
[+17.65s] DEBUG: Read 8 bytes from daemon
[+17.65s] DEBUG: Read 16 bytes from daemon
[+17.65s] DEBUG: Authentication complete for user temp with return code 0
[+17.65s] DEBUG: Starting session ubuntu
[+17.65s] DEBUG: Wrote 18 bytes to daemon
[+17.65s] DEBUG: Read 8 bytes from daemon
[+17.65s] DEBUG: Read 4 bytes from daemon

```

Any ideas?
thanks

---

### Post by einstein**-7 on 2013-02-05
Fixed the customizing my switching back to lightdm and unity-greeter then fixed the login bouncing back with...
```
sudo chown  -R  $USER:$USER  $HOME
```
THANKS ALL..

---

### Post by hrby on 2013-05-24
Hallo Leute,

bei mir hat geholfen "colord" und "libcolord1" neu zu installieren
----------------------------------------
Hello people,

 has helped me to reinstall "colord" and "libcolord1" 

MfG
hrby

---

