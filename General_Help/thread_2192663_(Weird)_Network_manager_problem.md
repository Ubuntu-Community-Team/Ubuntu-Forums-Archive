---
title: "(Weird) Network manager problem"
date: 2013-12-09
forum: General Help
---

### Post by nobody92 on 2013-12-09
Hello,
 I am posting this, hoping that someone can figure out what problem my laptop has. I've posted this question before on AskUbuntu, however several days have passed and nobody has answered, so I hope I can get some help here.

[COLOR=#333333][FONT=UbuntuRegular]I've just installed Ubuntu 13.10 Mini with MATE Desktop, and I've also installed network-manager and network-manager-gnome. The problem is that the nm-applet is missing from the tray.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Even though this may look like a trivial question, I've tried most of the solutions I've found but to no avail. The interesting things I've found out are:[/FONT][/COLOR]

[LIST]
[*]Even though network-manager and network-manager-gnome are installed, there is no such service known as NetworkManager or network-manager. However, after I login and go to a terminal and type **sudo NetworkManager**, the response I get is: **NetworkManager is already running (pid 2447)** (even though it is not registered as a service / daemon, at starts automatically.
[*]Even though nm-applet is set to start automatically(I have it registered in Startup Applications), it doesn't appear in the notification area, and this indicates that it cannot connect to the network manager service. However, when I start it manually via the terminal, it appears and works flawlessly(and it shows that the networks are managed by network-manager, not by another service). And it gives me the following output:
[/LIST]


```

** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon
** Message: applet now embedded in the notification area


(nm-applet:2589): libnotify-WARNING **: Failed to connect to proxy


** (nm-applet:2589): WARNING **: Failed to show notification: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Notifications was not provided by any .service files


** (nm-applet:2589): WARNING **: Failed to show notification: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Notifications was not provided by any .service files

```

Below are some information relevant to my problem: The contents of /etc/network/interfaces:

```
[INDENT]# This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
[/INDENT]

```
[COLOR=#333333][FONT=UbuntuRegular]
The contents of /etc/NetworkManager/NetworkManager.conf:
[/FONT][/COLOR]```
[INDENT][main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=true
[/INDENT]

```
[COLOR=#333333][FONT=UbuntuRegular]
The contents of /var/lib/NetworkManager/NetworkManager.state
[/FONT][/COLOR]```
[INDENT][main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
[/INDENT]

```
[COLOR=#333333][FONT=UbuntuRegular]
Is there any way I could solve this problem? Thanks in advance.

**EDIT:** Sorry, I forgot to mark it as solved.[/FONT][/COLOR]

---

### Post by nobody92 on 2013-12-09
Nevermind, I've managed to solve this problem with the help of [this thread]("http://ubuntuforums.org/showthread.php?t=2186487"). 

[COLOR=#333333][FONT=UbuntuRegular]The autostart file located here: **/etx/xdg/autostart/nm-applet.desktop**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]contained this certain line:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]**AutostartCondition=GNOME3 unless-session gnome**[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I removed it, and now nm-applet shows correctly.[/FONT][/COLOR]

---

### Post by Bucky Ball on 2013-12-09
Good news. Please mark thread as solved to help others. ;)

---

### Post by nobody92 on 2013-12-09
Done! Sorry, I had forgotten to do that.

---

