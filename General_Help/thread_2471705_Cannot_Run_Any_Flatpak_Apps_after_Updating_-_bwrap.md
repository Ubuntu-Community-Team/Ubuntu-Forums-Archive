---
title: "Cannot Run Any Flatpak Apps after Updating - bwrap Bind Mount Error"
date: 2022-02-07
forum: General Help
---

### Post by el-viejo on 2022-02-07
Hello everyone, any insight into this is very much appreciated as the only documentation or reference to this problem all points to Void Linux users who are using Musl, which is very far from what I'm on...

Kubuntu 21.10
5.13 kernel
GCC 4:11.2

After running "flatpak update" and rebooting, I am unable to launch any Flatpak applications. There was no error when running the update, however I now receive the following error when launching any Flaptak I have installed:

```
[FONT=monospace][COLOR=#00D7FF]**flatpak run com.github.iwalton3.jellyfin-media-player**[/COLOR][COLOR=#00D7FF]                                                                   [/COLOR][COLOR=#00D7FF]**   **[/COLOR][COLOR=#000000] [/COLOR]
bwrap: Can't bind mount /oldroot/media on /newroot/media: No such device[COLOR=#00D7FF]                                                                            [/COLOR][COLOR=#000000] [/COLOR]
[COLOR=#FF5454]**error: **[/COLOR][COLOR=#000000]Failed to sync with dbus proxy[/COLOR]
[/FONT]
```

This seems to point to an issue with bwrap, and when attempting to test I get the same error:
```
[FONT=monospace][COLOR=#00D7FF]**bwrap --bind / / true**[/COLOR][COLOR=#00D7FF]                                                                   [/COLOR][COLOR=#00D7FF]**                                   **[/COLOR][COLOR=#000000] [/COLOR]
bwrap: Can't bind mount /oldroot/ on /newroot/: No such device
```

I really have no idea what could be causing this, this behavior all started after just running "flatpak update". Things seemed fine until I rebooted and started the machine back up this morning. If any more information is needed please let me know.[/FONT]

---

### Post by el-viejo on 2022-02-07
I attempted to remove Bubblewrap and Flatpak, rebooted, and reinstalled both utilities, but the same exact behavior is persisting.

Searching online isn't pulling up anything relevant to my system, really weird that any instance of this issue or even small variations of it all mention it as an issue with Musl which I have never used or installed.

---

### Post by el-viejo on 2022-02-07
Gooby pls.

I'm not sure where else to ask, really hoping someone here has an idea. I'm unable to launch several apps since it's affecting everything out of Flatpak.

---

### Post by #&amp;thj^% on 2022-02-07
Not sure  I can help here but this may help us more
```
 flatpak run -vv --command=true org.signal.Signal
``` 
Return the output in Code Tags thanks
If there is anything unusual about your /opt (for example if it's a symbolic link, or some special type of filesystem, or has unusual permissions, or anything like that) then we will also need to know what it is.

---

### Post by el-viejo on 2022-02-07
> **1fallen said:**
> Not sure  I can help here but this may help us more
```
 flatpak run -vv --command=true org.signal.Signal
``` 
Return the output in Code Tags thanks
If there is anything unusual about your /opt (for example if it's a symbolic link, or some special type of filesystem, or has unusual permissions, or anything like that) then we will also need to know what it is.

Thank you for the response

```
[FONT=monospace][COLOR=#00D7FF]**flatpak run -vv --command=true com.github.iwalton3.jellyfin-media-**[/COLOR]
player
F: No installations directory in /etc/flatpak/installations.d. Skipping
F: Opening system flatpak installation at path /var/lib/flatpak
F: Opening user flatpak installation at path /home/viejo/.local/share/flatpak
F: Opening user flatpak installation at path /home/viejo/.local/share/flatpak
F: Opening system flatpak installation at path /var/lib/flatpak
F: Skipping parental controls check for app/com.github.iwalton3.jellyfin-media-player/x86_6
4/stable since parental controls are disabled globally
F: Opening user flatpak installation at path /home/viejo/.local/share/flatpak
F: Opening system flatpak installation at path /var/lib/flatpak
F: Cleaning up unused container id 284108010
F: Allocated instance id 3123957652
F: Add defaults in dir /com/github/iwalton3/jellyfin-media-player/
F: Add locks in dir /com/github/iwalton3/jellyfin-media-player/
F: Allowing wayland access
F: Allowing x11 access
F: Allowing pulseaudio access
F: Pulseaudio user configuration file '/home/viejo/.config/pulse/client.conf': Error openin
g file /home/viejo/.config/pulse/client.conf: No such file or directory
F: bwrap --args 37 = --ro-bind /boot /boot --ro-bind /home /home --ro-bind /etc /etc --ro-b
ind /media /media --bind /var /var --symlink usr/bin /bin --ro-bind /dev /dev --symlink usr
/lib /lib --symlink usr/lib32 /lib32 --symlink usr/lib64 /lib64 --symlink usr/libx32 /libx3
2 --ro-bind /mnt /mnt --ro-bind /opt /opt --ro-bind /proc /proc --ro-bind /root /root --bin
d /run /run --symlink usr/sbin /sbin --ro-bind /srv /srv --ro-bind /sys /sys --bind /tmp /t
mp --ro-bind /usr /usr --ro-bind /cdrom /cdrom --bind /run/user/1000/.dbus-proxy/ /run/user
/1000/.dbus-proxy/ --file 35 /.flatpak-info
F: bwrap --args 40 = --fd=39 unix:path=/run/user/1000/bus /run/user/1000/.dbus-proxy/sessio
n-bus-proxy-HZUJH1 --filter '--own=com.github.iwalton3.jellyfin-media-player.*' '--own=org.
mpris.MediaPlayer2.com.github.iwalton3.jellyfin-media-player.*' --talk=com.canonical.AppMen
u.Registrar --talk=org.freedesktop.ScreenSaver --talk=org.freedesktop.PowerManagement '--ca
ll=org.freedesktop.portal.*=*' '--broadcast=org.freedesktop.portal.*=@/org/freedesktop/port
al/*' unix:path=/var/run/dbus/system_bus_socket /run/user/1000/.dbus-proxy/system-bus-proxy
-FDVJH1 --filter --talk=org.freedesktop.login1 'unix:path=/tmp/dbus-lr9rHWoxoi,guid=c499879
c4fb86d1af22e1ec962014e19' /run/user/1000/.dbus-proxy/a11y-bus-proxy-C94JH1 --filter --slop
py-names --call=org.a11y.atspi.Registry=org.a11y.atspi.Socket.Embed@/org/a11y/atspi/accessi
ble/root --call=org.a11y.atspi.Registry=org.a11y.atspi.Socket.Unembed@/org/a11y/atspi/acces
sible/root --call=org.a11y.atspi.Registry=org.a11y.atspi.Registry.GetRegisteredEvents@/org/
a11y/atspi/registry --call=org.a11y.atspi.Registry=org.a11y.atspi.DeviceEventController.Get
KeystrokeListeners@/org/a11y/atspi/registry/deviceeventcontroller --call=org.a11y.atspi.Reg
istry=org.a11y.atspi.DeviceEventController.GetDeviceEventListeners@/org/a11y/atspi/registry
/deviceeventcontroller --call=org.a11y.atspi.Registry=org.a11y.atspi.DeviceEventController.
NotifyListenersSync@/org/a11y/atspi/registry/deviceeventcontroller --call=org.a11y.atspi.Re
gistry=org.a11y.atspi.DeviceEventController.NotifyListenersAsync@/org/a11y/atspi/registry/d
eviceeventcontroller
F: Running 'bwrap --args 37 xdg-dbus-proxy --args=40'
bwrap: Can't bind mount /oldroot/media on /newroot/media: No such device
error: Failed to sync with dbus proxy
[/FONT]
```[FONT=monospace]

I'm not sure what the standard permissions for /opt are, but I think this looks normal?

[/FONT]```
[FONT=monospace][COLOR=#00D7FF]**ls -ld /opt**[/COLOR]
drwxr-xr-x 1 root root 92 Jan  6 13:18 [COLOR=#5454FF]**/opt**[/COLOR]
[/FONT]
```[FONT=monospace]

[/FONT]```
[FONT=monospace][COLOR=#00D7FF]**stat /opt**[/COLOR]
  File: /opt
  Size: 92              Blocks: 0          IO Block: 4096   directory
Device: 1eh/30d Inode: 275         Links: 1
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2022-02-07 16:22:27.622228073 -0600
Modify: 2022-01-06 13:18:52.097749600 -0600
Change: 2022-01-06 13:18:52.097749600 -0600
 Birth: 2022-01-04 13:09:58.982612767 -0600
[/FONT]
```[FONT=monospace]

[/FONT]```
[FONT=monospace][COLOR=#00D7FF]**ls -l /opt**[/COLOR]
total 0
drwxr-xr-x 1 root root 656 Jan  6 13:19  [COLOR=#5454FF]**balenaEtcher**[/COLOR]
drwxr-xr-x 1 root root  10 Jan  4 13:51  [COLOR=#5454FF]**brave.com**[/COLOR]
drwxr-xr-x 1 root root 622 Jan  4 14:18  [COLOR=#5454FF]**FreeTube**[/COLOR]
drwxrwxr-x 1 root root 634 Feb  2 22:12  [COLOR=#5454FF][B]Signal
[/B][/COLOR][/FONT]
```[FONT=monospace]

[/FONT]

---

### Post by dragonfly41 on 2022-02-07
Stacer offers a dashboard and one view is flatpaks .. might help ..

[https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,sudo%20apt%2Dget%20update](https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,sudo%20apt%2Dget%20update)

[Correction]
Actually I was thinking of snaps ..
to view flatpak processes go to processes panel and type in top filter  flatpak

---

### Post by #&amp;thj^% on 2022-02-07
Yes your /opt looks fine.
Yuck looks like a new/revisted bug: [https://github.com/flatpak/flatpak/issues/3807](https://github.com/flatpak/flatpak/issues/3807)
test patch if you want: [https://github.com/void-linux/void-packages/tree/master/srcpkgs/bubblewrap/patches](https://github.com/void-linux/void-packages/tree/master/srcpkgs/bubblewrap/patches)
But this from your output "**bwrap: Can't bind mount /oldroot/media on /newroot/media: No such device**"
maybe check the **/real/path/**

---

### Post by el-viejo on 2022-02-07
> **1fallen said:**
> Yes your /opt looks fine.
Yuck looks like a new/revisted bug: [https://github.com/flatpak/flatpak/issues/3807](https://github.com/flatpak/flatpak/issues/3807)
test patch if you want: [https://github.com/void-linux/void-packages/tree/master/srcpkgs/bubblewrap/patches](https://github.com/void-linux/void-packages/tree/master/srcpkgs/bubblewrap/patches)
But this from your output "**bwrap: Can't bind mount /oldroot/media on /newroot/media: No such device**"
maybe check the **/real/path/**

Thank you very much. I'll add my own response to that thread soon just to get more momentum behind the bug report.

Thanks Fallen!

---

### Post by #&amp;thj^% on 2022-02-07
> **el-viejo said:**
> Thank you very much. I'll add my own response to that thread soon just to get more momentum behind the bug report.

Thanks Fallen!

Best of Luck ;)

---

