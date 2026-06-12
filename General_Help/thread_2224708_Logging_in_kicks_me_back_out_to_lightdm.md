---
title: "Logging in kicks me back out to lightdm"
date: 2014-05-17
forum: General Help
---

### Post by boast on 2014-05-17
As the title states, logging in flashes the desktop loading a bit but then kicks me back out to lightdm login. I can not figure out how to debug this. Any suggestions on where to look?

On 14.04, all up to date.

```

$ grep -e '(EE)' /var/log/Xorg.0.log
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   383.559] (EE) open /dev/dri/card0: No such file or directory
[   383.560] (EE) open /dev/fb0: No such file or directory

```

```
$ tail /var/log/syslog
May 17 16:12:11 ubox2 NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.system: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.145': no such name
May 17 16:12:11 ubox2 NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.own: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.145': no such name
May 17 16:12:11 ubox2 NetworkManager[788]: <warn> error requesting auth for org.freedesktop.NetworkManager.settings.modify.hostname: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.145': no such name
May 17 16:12:12 ubox2 acpid: client 2737[0:0] has disconnected
May 17 16:12:12 ubox2 acpid: client connected from 2979[0:0]
May 17 16:12:12 ubox2 acpid: 1 client rule loaded
May 17 16:12:14 ubox2 colord: Device added: xrandr-BBY TV-9456
May 17 16:12:14 ubox2 colord: Automatic metadata add icc-3ba16a5f25169ad3ed5bdf6f7f4553ba to xrandr-BBY TV-9456
May 17 16:12:14 ubox2 colord: Profile added: icc-3ba16a5f25169ad3ed5bdf6f7f4553ba
May 17 16:12:14 ubox2 colord: Profile added: icc-dc7e77b789249bab60d9bf191ae47043
```

```
$ sudo tail /var/log/lightdm/lightdm.log
[+402.56s] DEBUG: Session pid=2986: Running command /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/unity-greeter
[+402.56s] DEBUG: Creating shared data directory /var/lib/lightdm-data/lightdm
[+402.56s] DEBUG: Session pid=2986: Logging to /var/log/lightdm/x-0-greeter.log
[+402.57s] DEBUG: Activating VT 7
[+402.57s] DEBUG: Activating login1 session /org/freedesktop/login1/session/c12
[+402.80s] DEBUG: Session pid=2986: Greeter connected version=1.10.1
[+403.01s] DEBUG: Session pid=2986: Greeter start authentication for esmeralda
[+403.01s] DEBUG: Session pid=3046: Started with service 'lightdm', username 'esmeralda'
[+403.02s] DEBUG: Session pid=3046: Got 1 message(s) from PAM
[+403.02s] DEBUG: Session pid=2986: Prompt greeter with 1 message(s)
```

```
$ sudo tail /var/log/lightdm/x-0.log
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension XFree86-VidModeExtension
Initializing built-in extension XFree86-DGA
Initializing built-in extension XFree86-DRI
Initializing built-in extension DRI2
Loading extension GLX
Loading extension NV-GLX
Loading extension NV-CONTROL
Loading extension XINERAMA
```

```
$ sudo grep -i fail x-0-greeter.log
[+1.00s] CRITICAL: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
[+1.00s] CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
[+1.03s] CRITICAL: gtk_icon_info_get_filename: assertion 'icon_info != NULL' failed
[+1.03s] CRITICAL: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** (nm-applet:3936): CRITICAL **: nm_secret_agent_register: assertion 'priv->registered == FALSE' failed
```

---

### Post by bapoumba on 2014-05-17
May be this ?
[https://bbs.archlinux.org/viewtopic.php?id=179031](https://bbs.archlinux.org/viewtopic.php?id=179031)

---

### Post by Bashing-om on 2014-05-17
boast; Hello;

Many times it is a change in authorization to access the desktop.
To look and check:
1. At the login screen, press Ctrl+Alt+F1 to get to the console.
2. Log in there.
3. Check if ".ICEauthority" is owned by you:
```

ls -al .ICEauthority

```
4. If it isn't (but possibly by root), change it to you:
```

sudo chown USERNAME:USERNAME .ICEauthority

```
5. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8
6. Try again to log in.
If it worked, see here about a possible cause:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Better take a look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies .

//
If the above does not address the issue, we

[INDENT][INDENT]keep on drilling around
[/INDENT][/INDENT]

---

### Post by NM5TF on 2014-05-17
I had the same exact problem after I borked my system installing flashback...

the fix was doing this...

```
sudo mv ~/.Xauthority ~/.Xauthority.backup
sudo service lightdm restart

```

tommy

---

### Post by boast on 2014-05-19
> **Bashing-om said:**
> 

Better take a look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies .

//
If the above does not address the issue, we

[INDENT][INDENT]keep on drilling around
[/INDENT][/INDENT]


Thanks a lot!! That fixed it.

Strange because I did the "sudo mv ~/.Xa..." thing as mentioned above, but it seems it still rebuilt it as root.

---

### Post by Bashing-om on 2014-05-19
boast; Great !

Pleased this little hump was not a mountain.

[INDENT][INDENT]we can just
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

