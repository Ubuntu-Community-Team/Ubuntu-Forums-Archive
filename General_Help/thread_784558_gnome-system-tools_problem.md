---
title: "gnome-system-tools problem"
date: 2008-05-06
forum: General Help
---

### Post by tosoth on 2008-05-06
Hi, I'm using ubuntu 8.04. I have strange problem with **gnome-system-tools** that started yesterday. I installed VirtualBox and tried to add my user to "vboxusers" group, using users-admin tool. So i run it and unlocked it, but there wasn't any group on the list. So I run **polkit-gnome-authorization** and gave myself rights to change user configuration "org.freedesktop.systemtoolsbackends.self.set". If I recall corectly, after that, I couldn't run **users-admin** tool at all, so i Revoked this rights and than I realized I can't run any tool from **gnome-system-tools**. I couldn't mount any removable drives also although it was working earlier and i didn't change anything with this. Eventually I solved problem with mounting somehow, but I still can't run gnome-system-tools although I have authorizations in policykit for my user for "org.freedesktop.systemtoolsbackends.self.set" and "org.freedesktop.systemtoolsbackends.set"

Errors:
users-admin
```
tommy@tommy-ubu:~$ users-admin 

** (users-admin:22598): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
```

shares-admin
```
tommy@tommy-ubu:~$ shares-admin 

(shares-admin:23462): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (shares-admin:23462): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
```

network-admin
```
tommy@tommy-ubu:~$ network-admin 

(network-admin:23835): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (network-admin:23835): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
```

services-admin
```
tommy@tommy-ubu:~$ services-admin 

** (services-admin:24207): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
```

time-admin
```
tommy@tommy-ubu:~$ time-admin 

(time-admin:24562): Gtk-WARNING **: Unsupported tag for GtkWidget: atkproperty


(time-admin:24562): Gtk-WARNING **: Unsupported tag for GtkWidget: atkproperty


(time-admin:24562): Gtk-WARNING **: Unknown property: GtkCalendar.display-options


** (time-admin:24562): CRITICAL **: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
```

And all of the above give me error window that I attached.

Of course I can do all the things these tools should do, ie. from terminal.

```
Package: gnome-system-tools
Architecture: i386
Version: 2.22.0-0ubuntu9

Package: system-tools-backends
Architecture: i386
Version: 2.6.0-0ubuntu7

Package: policykit
Architecture: i386
Version: 0.7-2ubuntu7

Package: policykit-gnome
Architecture: i386
Version: 0.7-2ubuntu1
```

Anyone have the same problem? Someone knows how to solve it?

---

### Post by tosoth on 2008-05-07
Bump! Bump! Anybody Home?!

---

### Post by happynix on 2008-05-07
Me too!
[http://ubuntuforums.org/showthread.php?t=785860&highlight=network-admin+dbus+hardy]("http://ubuntuforums.org/showthread.php?t=785860&highlight=network-admin+dbus+hardy")

---

### Post by tosoth on 2008-05-08
Maybe this change of title will help :|

---EDIT---
Nope, title didn't change...

---

### Post by happynix on 2008-05-08
I have two systems, a work system and a home system.

Both were upgraded.

No problems with one, and the other I have dbus errors associated with gnome-system-tools.

No messin with polkit rules on either one (well no prior to the problem)

I can't find any differences so far in /etc/dbus-1 between the two systems.
no major differences in group memberships.
Pam seems the same.


On the broken system my .xsession errors is full of 
```
** (nm-applet:6240): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.26" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

** (nm-applet:6240): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.26" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'[\CODE]

I've tried editing the /etc/dbus-1/system.d/NetworkManager.conf
and /etc/dbus-1/system.d/nm-applet.conf and adding the following permission
[CODE]<policy group="netdev">
      <allow own="org.freedesktop.NetworkManagerInfo"/>
      <allow send_destination="org.freedesktop.NetworkManagerInfo"/>
      <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
</policy>

```

I still can't run any of the gnome-system-tools

---

### Post by tosoth on 2008-05-09
I made it yesterday, but a little different.

```
  <policy user="tommy">
		<allow own="org.freedesktop.NetworkManagerInfo"/>
		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
                <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
```

I think it worked only if I comment this section:

```
  <policy context="default">
		<deny own="org.freedesktop.NetworkManagerInfo"/>

		<deny send_destination="org.freedesktop.NetworkManagerInfo"/>
		<deny send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>
```

Looks like this deny policy is more important then allow policy for my user.

Later I tried to make it the same way with **system-tools-backends.conf** but i didn't manage to do it.

Frankly I think that problem is somewhere else and maybe it's really trivial. All the problems started in the same moment and probably were caused by one little thing that changed, but I have no idea where to look.


---EDIT---
Is there any way to revert PolicyKit rules to it's initial state?

I could make a clean install of ubuntu, but if this happened once it'll probably sooner or later happen again. I'm starting to hate this new ubuntu, looks like it's full of strange bugs and imho releasing it in this state was a mistake.

---

### Post by happynix on 2008-05-09
I have another working ubuntu 8.04 system.

I've compaired the files and there was no difference.

---

### Post by tosoth on 2008-05-09
I found out, that all users had **nogroup** as their primary group. Not only normal users, but also root and all system users (ie. haldaemon, polkituser, syslog...). I changed their primary groups accordingly, comparing them with clean Ubuntu installation on VirtualBox. Unfortunately it didn't solve the problem yet, but I wonder what changed all these groups.
To change primary group i used:
```
usermod -g <new primary group name> <user name>
```


---EDIT---
Well it almost works. Changing groups obviously helped. After that I had problem with premissions of "setuid helper" (/usr/lib/dus-1.0/dbus-daemon-launch-helper), because I changed it's permission earlier. Now I can start gnome-system tools, but there's another problem. I can't unlock it, I get this error when I try:
```
** (network-admin:8848): CRITICAL **: Message did not receive a reply (timeout by message bus)
```

---

### Post by tosoth on 2008-05-10
I forgot... this error from earlier post doesn't occur normally. Just nothing happens when I click "Unlock". I got this error yesterday after some wild exercises (trying to run g-s-t with sudo and things like that).

As I see, when I start ie. **users-admin** and try to unlock, **polkit-gnome-manager** starts, but it doesn't start **polkit-grant-helper**.

---

### Post by tosoth on 2008-05-10
**polkit-grant-helper** starts for new user, but not for my. I might've broke something trying to solve this problem. Maybe I should try to make a new account :|

---

### Post by happynix on 2008-05-12
The correct permissions for dbus-daemon-launch-helper from my working system

```
-rwsr-xr-- 1 root messagebus 228628 2008-02-29 04:23 dbus-daemon-launch-helper
```

Maybe we have different problems.  I can't even get the gnome-system-tools utilities to launch.  (I never see unlock buttons)

Do you have dbus and udev launching at seperate times in your startup ?

---

### Post by tosoth on 2008-05-12
I'm afraid I gave up :(. There's no sense comparing our systems because I made a clean install. You can read last post i wrote [here]("https://answers.launchpad.net/ubuntu/+source/gnome-system-tools/+question/32334").

It doesn't mean that everything is ok now... it's not :lolflag:.
In example I can't unlock g-s-t right now, but I will unlock it after system reboot. It happens all the time.

It's very possible that your problem is different then mine was. There were many people with similar symptoms and every time there was different problem ;). In current state Hardy resembles me a trashcan where everything is possible.

(At least I solved problem with flash crashing my firefox3. Funny thing I didn't have such problem before clean install \\:D/ ).


Oh, one more thing. You were writing somewhere that you were changing hal startup priority in /etc/rc2.d from S12 to S13. It should be S24hal. That's how it is in hardy normally.

And another one... have you checked groups in your system? What you get when you enter ```
$groups <your user>
```
?

---

