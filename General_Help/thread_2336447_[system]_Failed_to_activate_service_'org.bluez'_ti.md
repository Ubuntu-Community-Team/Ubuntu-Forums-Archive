---
title: "[system] Failed to activate service 'org.bluez': timed out"
date: 2016-09-08
forum: General Help
---

### Post by alain.roger on 2016-09-08
Hi,

i have the following error in auth.log:

```
[system] Failed to activate service 'org.bluez': timed out
```

After doing some research on internet i discovered that it is link to bluetooth of my laptop. I want to remove the error message so i disabled bluetooth:

```
[FONT=monospace][COLOR=#000000]&#9679; bluetooth.service - Bluetooth service[/COLOR]
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset:  
   Active: inactive (dead)
     Docs: man:bluetoothd(8)
[/FONT]
```

i even did the following changes in '[COLOR=#000000]/usr/share/dbus-1/services/org.bluez.obex.service' as following:
```
[/COLOR][COLOR=#000000]SystemdService=obex.service[/COLOR][COLOR=#000000]
```

[/COLOR]however nothing changed... i always have the same error message.

What did i do wrong ?

thx
[COLOR=#000000]
[/COLOR]

---

### Post by #&amp;thj^% on 2016-09-08
I'm not sure you did anything wrong...and welcome to "systemd" bug report: [https://bugs.launchpad.net/ubuntu/+source/blueman/+bug/1533206](https://bugs.launchpad.net/ubuntu/+source/blueman/+bug/1533206)
> If I remember correctly it's related to systemd which removes the service configuration for org.bluez if one disables bluetooth.service. _**blueman needs to be prepared for that situation**_.
Source: [https://github.com/blueman-project/blueman/issues/488](https://github.com/blueman-project/blueman/issues/488)

---

### Post by alain.roger on 2016-09-10
if i type:
[COLOR=#000000]```
sudo systemctl stop bluetooth.service
```[/COLOR]
i stopped the service bluetooth

and i disable it with:
```
[COLOR=#000000]sudo systemctl disable bluetooth.service[/COLOR]
```

however, after a restart of laptop, the bluetooth service is restarted :(


[IMG]http://i68.tinypic.com/296kxo4.png[/IMG]

---

### Post by #&amp;thj^% on 2016-09-10
Try this...and after reboot.
```
sudo "echo 'manual' > /etc/init/bluetooth.override"
```
This should disable Bluetooth.

---

