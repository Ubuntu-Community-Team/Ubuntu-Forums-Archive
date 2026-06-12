---
title: "Disable all USB automounting"
date: 2015-06-26
forum: General Help
---

### Post by DigiAngel on 2015-06-26
Topic says it...I've tried going to the system prefs and the dconf-editor method, but as soon as I turn on this external drive bay Ubuntu 14.04 automounts the dives to /media/usb0 and /media/usb1.  Is there a way to stop this?  Thank you.

---

### Post by deadflowr on 2015-06-27
I found that usb drives tend to get mounted by the system before my personal dconf media-handling settings even come up.
So to avoid that I created an override schema.
To do so I opened gedit
Then adding the following lines
```
[org.gnome.desktop.media-handling]
automount=false
automount-open=false
```
then saved it as 10_media-handling.gschema.override.
(I saved originally in my personally Documents folder, but you can save it anywhere)
Then copy it into the folder /usr/share/glib-2.0/schemas/
Then run the re-compile command
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```
It is possible some other override setting or schema is off-kilter so pay attetion to any errors.
It any errors are shown, but have nothing to do with your overrride (I got one for eog) you can ignore it, and life should go on.

Hope this helps.

---

### Post by DigiAngel on 2015-08-06
Iam giving this a shot not...thank you.

---

### Post by DigiAngel on 2015-08-06
Thank you....gave that a shot, but no go...I plugged in a USB stick and:

```
/dev/sdb1 on /media/usb0 type fuseblk (rw,noexec,nosuid,nodev,sync,noatime,allow_other,blksize=4096)
```

---

### Post by deadflowr on 2015-08-07
My method above would require a logout/login.
I don't think the change affects an existing session.

---

### Post by Bucky Ball on 2015-08-07
*Thread moved to **General Help**.*

Not related to ***Desktop Environments*** ...

---

