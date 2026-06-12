---
title: "snap apps not working, permission denied"
date: 2021-06-11
forum: General Help
---

### Post by shizow on 2021-06-11
Hey

since a recent updates all my snap apps dont start, seems like some permission error

here an example from syslog

May 29 13:21:20 thinkpad kernel: [430673.141822] audit: type=1400 audit(1622283680.205:3069): apparmor="DENIED" operation="open" profile="snap.signal-desktop.signal-desktop" name="/etc/fstab" pid=186478 comm="signal-desktop" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


what can i do

---

### Post by dddman on 2021-06-11
The above does not mean anything to me, try this in terminal.

> systemctl status snapd.service
edit
It's Apparmor I bet
[https://www.google.com/search?channel=fs&client=ubuntu&q=audit%3A+type%3D1400+audit%281622283680.205%3A3069%29%3A+apparmor%3D%22DENIED%22+operation%3D%22open%22+profile%3D%22snap.signal-desktop.signal-desktop%22+name%3D%22%2Fetc%2Ffstab%22+pid%3D186](https://www.google.com/search?channel=fs&client=ubuntu&q=audit%3A+type%3D1400+audit%281622283680.205%3A3069%29%3A+apparmor%3D%22DENIED%22+operation%3D%22open%22+profile%3D%22snap.signal-desktop.signal-desktop%22+name%3D%22%2Fetc%2Ffstab%22+pid%3D186)

---

### Post by TheFu on 2021-06-11
[https://github.com/snapcrafters/signal-desktop/issues/7](https://github.com/snapcrafters/signal-desktop/issues/7) ?
Signal doesn't like symbolic links.  Could that be it?

If you create a new Linux account, logout, login using the new Linux account, then connect to your normal signal userid, does it work?  This basic troubleshooting will determine if the issue is for 1 userid or all userids on a system.

---

### Post by shizow on 2021-06-12
> **dddman said:**
> The above does not mean anything to me, try this in terminal.


edit
It's Apparmor I bet
[https://www.google.com/search?channel=fs&client=ubuntu&q=audit%3A+type%3D1400+audit%281622283680.205%3A3069%29%3A+apparmor%3D%22DENIED%22+operation%3D%22open%22+profile%3D%22snap.signal-desktop.signal-desktop%22+name%3D%22%2Fetc%2Ffstab%22+pid%3D186](https://www.google.com/search?channel=fs&client=ubuntu&q=audit%3A+type%3D1400+audit%281622283680.205%3A3069%29%3A+apparmor%3D%22DENIED%22+operation%3D%22open%22+profile%3D%22snap.signal-desktop.signal-desktop%22+name%3D%22%2Fetc%2Ffstab%22+pid%3D186)


```

sudo systemctl status snapd.service
[sudo] password for user: 
&#9679; snapd.service - Snap Daemon
     Loaded: loaded (/lib/systemd/system/snapd.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2021-06-12 14:28:16 EEST; 2h 31min ago
TriggeredBy: &#9679; snapd.socket
   Main PID: 995 (snapd)
      Tasks: 26 (limit: 18745)
     Memory: 1.1G
     CGroup: /system.slice/snapd.service
             &#9492;&#9472;995 /usr/lib/snapd/snapd

Jun 12 14:28:15 thinkpad systemd[1]: Starting Snap Daemon...
Jun 12 14:28:15 thinkpad snapd[995]: AppArmor status: apparmor is enabled but some kernel features are missing: dbus, network
Jun 12 14:28:16 thinkpad snapd[995]: AppArmor status: apparmor is enabled but some kernel features are missing: dbus, network
Jun 12 14:28:16 thinkpad snapd[995]: daemon.go:347: started snapd/2.50.1 (series 16; classic; devmode) ubuntu/21.04 (amd64) linux/5.12.0-051200rc3-generic.
Jun 12 14:28:16 thinkpad snapd[995]: daemon.go:440: adjusting startup timeout by 1m45s (pessimistic estimate of 30s plus 5s per snap)
Jun 12 14:28:16 thinkpad systemd[1]: Started Snap Daemon.
Jun 12 14:28:48 thinkpad snapd[995]: autorefresh.go:467: Cannot prepare auto-refresh change due to a permanent network error: persistent network error: Post https://api.snapcraft.io/v2/snaps/refresh: dial tcp: lookup api.snapcraf>
Jun 12 14:29:53 thinkpad snapd[995]: stateengine.go:150: state ensure error: persistent network error: Post https://api.snapcraft.io/v2/snaps/refresh: dial tcp: lookup api.snapcraft.io: Temporary failure in name resolution
Jun 12 14:53:18 thinkpad snapd[995]: storehelpers.go:551: cannot refresh: snap has no updates available: "core", "core18", "fwupd", "gnome-3-28-1804", "gnome-3-34-1804", "gtk-common-themes", "signal-desktop", "skype", "slack", "s>
Jun 12 14:53:45 thinkpad snapd[995]: storehelpers.go:551: cannot refresh: snap has no updates available: "keepassxc", "zoom-client"

```

---

### Post by dddman on 2021-06-12
That error
> stateengine.go:150: state ensure error: persistent network error: Post [https://api.snapcraft.io/v2/snaps/refresh:](https://api.snapcraft.io/v2/snaps/refresh:) dial tcp: lookup api.snapcraft.io: Temporary failure in name resolution
Lead me here
[http://status.snapcraft.io/](http://status.snapcraft.io/)

---

### Post by TheFu on 2021-06-12
snaps don't like it when the system isn't internet connected.  Maybe switching to a similar, different, solution like appimages or flatpaks would solve the issue? Those 2 other solutions aren't as restrictive as snaps.

---

### Post by shizow on 2021-06-14
any idea what i can do now?

```

J]un 14 13:16:36 thinkpad kernel: [81461.134792] audit: type=1400 audit(1623665796.383:79): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/home/user/.config/user-dirs.dirs" pid=10701 comm="head" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Jun 14 13:16:36 thinkpad kernel: [81461.136560] audit: type=1400 audit(1623665796.387:80): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/home/user/Documents/" pid=10703 comm="head" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Jun 14 13:16:36 thinkpad kernel: [81461.225468] audit: type=1400 audit(1623665796.475:81): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/usr/share/icons/" pid=10640 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:16:36 thinkpad kernel: [81461.226166] audit: type=1400 audit(1623665796.475:82): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/var/lib/snapd/desktop/icons/" pid=10640 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:16:36 thinkpad kernel: [81461.255025] audit: type=1400 audit(1623665796.503:83): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/usr/share/glib-2.0/schemas/" pid=10758 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:16:36 thinkpad kernel: [81461.256842] audit: type=1400 audit(1623665796.507:84): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/usr/share/glib-2.0/schemas/" pid=10760 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:16:37 thinkpad kernel: [81462.665843] audit: type=1400 audit(1623665797.915:85): apparmor="DENIED" operation="connect" profile="snap.vlc.vlc" pid=10770 comm="glxinfo" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@/tmp/.X11-unix/X0" peer="unconfined"
Jun 14 13:16:38 thinkpad kernel: [81462.965619] audit: type=1400 audit(1623665798.215:86): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/etc/pulse/client.conf" pid=10640 comm="vlc" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:16:38 thinkpad dbus-daemon[1202]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/DBus" interface="org.freedesktop.DBus" member="RequestName" mask="send" name="org.freedesktop.DBus" pid=10640 label="snap.vlc.vlc" peer_label="unconfined"
Jun 14 13:16:38 thinkpad dbus-daemon[1202]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/DBus" interface="org.freedesktop.DBus" member="RequestName" mask="send" name="org.freedesktop.DBus" pid=10640 label="snap.vlc.vlc" peer_label="unconfined"
Jun 14 13:16:59 thinkpad kernel: [81484.659238] audit: type=1400 audit(1623665819.907:93): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/home/user/.config/user-dirs.dirs" pid=10876 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Jun 14 13:16:59 thinkpad kernel: [81484.668326] audit: type=1400 audit(1623665819.919:94): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/home/user/.config/user-dirs.dirs" pid=10896 comm="head" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Jun 14 13:16:59 thinkpad kernel: [81484.669879] audit: type=1400 audit(1623665819.919:95): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/home/user/Documents/" pid=10898 comm="head" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Jun 14 13:16:59 thinkpad kernel: [81484.703248] audit: type=1400 audit(1623665819.951:96): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/usr/share/icons/" pid=10844 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:16:59 thinkpad kernel: [81484.703265] audit: type=1400 audit(1623665819.951:97): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/var/lib/snapd/desktop/icons/" pid=10844 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:16:59 thinkpad kernel: [81484.720771] audit: type=1400 audit(1623665819.971:98): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/usr/share/glib-2.0/schemas/" pid=10951 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:16:59 thinkpad kernel: [81484.722308] audit: type=1400 audit(1623665819.971:99): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/usr/share/glib-2.0/schemas/" pid=10953 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:17:00 thinkpad kernel: [81485.436030] audit: type=1400 audit(1623665820.683:100): apparmor="DENIED" operation="connect" profile="snap.vlc.vlc" pid=10963 comm="glxinfo" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@/tmp/.X11-unix/X0" peer="unconfined"
Jun 14 13:17:00 thinkpad dbus-daemon[1202]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/DBus" interface="org.freedesktop.DBus" member="RequestName" mask="send" name="org.freedesktop.DBus" pid=10844 label="snap.vlc.vlc" peer_label="unconfined"
Jun 14 13:17:00 thinkpad kernel: [81485.473115] audit: type=1400 audit(1623665820.723:101): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/etc/pulse/client.conf" pid=10844 comm="vlc" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:17:00 thinkpad kernel: [81485.473148] audit: type=1400 audit(1623665820.723:102): apparmor="DENIED" operation="connect" profile="snap.vlc.vlc" pid=10844 comm="vlc" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@/tmp/.X11-unix/X0" peer="unconfined"
Jun 14 13:17:00 thinkpad dbus-daemon[1202]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/DBus" interface="org.freedesktop.DBus" member="RequestName" mask="send" name="org.freedesktop.DBus" pid=10844 label="snap.vlc.vlc" peer_label="unconfined"
Jun 14 13:17:05 thinkpad kernel: [81490.032162] audit: type=1400 audit(1623665825.283:114): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/home/user/.config/user-dirs.dirs" pid=11030 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Jun 14 13:17:05 thinkpad kernel: [81490.041786] audit: type=1400 audit(1623665825.291:115): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/home/user/.config/user-dirs.dirs" pid=11050 comm="head" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Jun 14 13:17:05 thinkpad kernel: [81490.043267] audit: type=1400 audit(1623665825.291:116): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/home/user/Documents/" pid=11052 comm="head" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
Jun 14 13:17:05 thinkpad kernel: [81490.075063] audit: type=1400 audit(1623665825.323:117): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/usr/share/icons/" pid=10998 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:17:05 thinkpad kernel: [81490.075086] audit: type=1400 audit(1623665825.323:118): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/var/lib/snapd/desktop/icons/" pid=10998 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:17:05 thinkpad kernel: [81490.090622] audit: type=1400 audit(1623665825.339:119): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/usr/share/glib-2.0/schemas/" pid=11105 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:17:05 thinkpad kernel: [81490.092306] audit: type=1400 audit(1623665825.343:120): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/usr/share/glib-2.0/schemas/" pid=11107 comm="desktop-launch" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:17:06 thinkpad kernel: [81490.815755] audit: type=1400 audit(1623665826.063:121): apparmor="DENIED" operation="connect" profile="snap.vlc.vlc" pid=11118 comm="glxinfo" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@/tmp/.X11-unix/X0" peer="unconfined"
Jun 14 13:17:06 thinkpad dbus-daemon[1202]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/DBus" interface="org.freedesktop.DBus" member="RequestName" mask="send" name="org.freedesktop.DBus" pid=10998 label="snap.vlc.vlc" peer_label="unconfined"
Jun 14 13:17:06 thinkpad dbus-daemon[1202]: apparmor="DENIED" operation="dbus_method_call"  bus="session" path="/org/freedesktop/DBus" interface="org.freedesktop.DBus" member="RequestName" mask="send" name="org.freedesktop.DBus" pid=10998 label="snap.vlc.vlc" peer_label="unconfined"
Jun 14 13:17:06 thinkpad kernel: [81490.848604] audit: type=1400 audit(1623665826.099:122): apparmor="DENIED" operation="open" profile="snap.vlc.vlc" name="/etc/pulse/client.conf" pid=10998 comm="vlc" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Jun 14 13:17:06 thinkpad kernel: [81490.848612] audit: type=1400 audit(1623665826.099:123): apparmor="DENIED" operation="connect" profile="snap.vlc.vlc" pid=10998 comm="vlc" family="unix" sock_type="stream" protocol=0 requested_mask="send receive connect" denied_mask="send connect" addr=none peer_addr="@/tmp/.X11-unix/X0" peer="unconfined"

```

---

### Post by shizow on 2021-06-19
bump

---

### Post by TheFu on 2021-06-19
> **shizow said:**
> bump

You've been provided alternatives and a possible solution.  Did you try those? How well did they work or not work?  We can't read your mind.
Saying or implying "it doesn't work" is lacking in 
* what you did
* what the result was

Need some details, please.

I don't use telegram. Are there any related bugs open with that program or their snap package?

---

