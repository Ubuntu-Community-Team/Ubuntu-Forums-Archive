---
title: "Help: Opening Settings logs user out of session"
date: 2018-07-18
forum: General Help
---

### Post by seannieuwoudt on 2018-07-18
Fresh install of Ubuntu. 

When I open the default settings GUI, I get black screened and logged out of the current user session. Takes me back to log in screen. 

Here are the logs:

```

09:41:08 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
09:41:08 pulseaudio: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
09:41:05 kernel: nouveau 0000:09:00.0: gr: init failed, -16
09:41:05 kernel: nouveau 0000:09:00.0: gr: init failed, -16
09:41:05 kernel: nouveau 0000:09:00.0: gr: FECS falcon already acquired by gr!
09:40:59 pulseaudio: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 2 matched rules; type="method_call", sender=":1.110" (uid=1000 pid=2492 comm="/usr/bin/pulseaudio --start --log-target=syslog " label="unconfined") interface="org.freedesktop.DBus.ObjectManager" member="GetManagedObjects" error name="(unset)" requested_reply="0" destination="org.bluez" (uid=0 pid=1192 comm="/usr/lib/bluetooth/bluetoothd " label="unconfined")
09:40:59 gnome-session-b: CRITICAL: We failed, but the fail whale is dead. Sorry....
09:40:59 kernel: nouveau 0000:09:00.0: gr: init failed, -16
09:40:59 pulseaudio: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
09:40:59 kernel: nouveau 0000:09:00.0: gr: init failed, -16
09:40:50 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
09:40:49 pulseaudio: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
09:40:44 kernel: nouveau 0000:09:00.0: gr: init failed, -16
09:40:31 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
09:40:30 kernel: nouveau 0000:09:00.0: gr: init failed, -16
09:40:28 kernel: tpm_crb MSFT0101:00: can't request region for resource [mem 0xdc40c000-0xdc40cfff]
09:40:28 kernel: nouveau 0000:09:00.0: gr: init failed, -110

```

---

### Post by Frogs Hair on 2018-07-18
Hello and Welcome

Do you know why there is a reference to redhat spice on Ubuntu? 

```
[COLOR=#000000]*spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0*[/COLOR]
```


[https://bugzilla.redhat.com/show_bug.cgi?id=1497637](https://bugzilla.redhat.com/show_bug.cgi?id=1497637)

---

### Post by seannieuwoudt on 2018-07-19
I don't know why, but here's everything that was installed: 


[LIST]
[*]NVIDIA drivers (GP104 390.48-0ubuntu3)
[*]Chrome
[*]VirtualBox
[*]Vagrant
[*]Intellij
[*]Docker
[*]Dropbox
[*]Spotify
[*]Git
[/LIST]
 
Nothing else from my side. 

I suspected that it might have something to do with the NVIDIA drivers and removed those, but the issue persists. Everything else works 100%, just can't open the settings dialog.

---

### Post by Frogs Hair on 2018-07-19
Is this a virtual or hard-drive installation ?

---

### Post by kazakore on 2018-07-20
> **Frogs Hair said:**
> Hello and Welcome

Do you know why there is a reference to redhat spice on Ubuntu? 

```
[COLOR=#000000]*spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0*[/COLOR]
```


[https://bugzilla.redhat.com/show_bug.cgi?id=1497637](https://bugzilla.redhat.com/show_bug.cgi?id=1497637)


I just noticed I also have spice-vdagent on my machine when checking services so did a rdepend and that makes me wonder how anybody would not have it with a default install!!

```
~$ apt-cache rdepends spice-vdagent 
spice-vdagent
Reverse Depends:
  ubuntu-desktop
  xubuntu-desktop
  xubuntu-core
  vanilla-gnome-desktop
  ubuntustudio-desktop-core
  ubuntustudio-desktop
  ubuntukylin-desktop
  ubuntu-mate-desktop
  ubuntu-mate-core
  ubuntu-budgie-desktop
  kubuntu-desktop


```

---

### Post by Frogs Hair on 2018-07-20
Appears to be for a virtual machine client. I was surprised to read red hat in the error.  


[https://www.spice-space.org/download.html](https://www.spice-space.org/download.html)

---

### Post by dino99 on 2018-09-29
Workaround, till getting a fix:

 > sudo gedit /usr/lib/tmpfiles.d/spice-vdagentd.conf 

and modify the path from /var/run/....  to /run/....
then save  and exit. That will stop the log spam.

---

