---
title: "Windows access error on ubuntu samba share"
date: 2016-11-11
forum: General Help
---

### Post by uncommonw on 2016-11-11
[COLOR=#555555][FONT=sans-serif]Recently I upgraded my Ubuntu server to 16 and installed Veracrypt and samba to share the mounted drive with my windows computers. I can access the unmounted Veracrpt files fine but there seems to be a problem when I mount a drive on my Ubuntu box then try and share that folder. I was on Ubuntu 12 before all this. Example below...
[/FONT][/COLOR][IMG]https://dl.dropboxusercontent.com/u/5795375/2016-11-10_0022.png[/IMG]

[IMG]https://dl.dropboxusercontent.com/u/5795375/2016-11-10_0026.png[/IMG]

You can see here for some reason my share is working but the folder is not accessible.
[IMG]https://dl.dropboxusercontent.com/u/5795375/2016-11-10_0029.png[/IMG]

[COLOR=#555555][FONT=sans-serif]After playing around a bit more I found out it was not necessarily this folder. Any file or folder that was created by Veracrypt seems to have strange access not belonging to any group. Apparently this can't be changed. Even running nautilus as root will not allow me to switch he access to something else. It keeps switching back to None. I thought about using chmod 777 but that does not sound right to me, it's over kill. What am I doing wrong?

[/FONT][/COLOR][IMG]https://dl.dropboxusercontent.com/u/5795375/2016-11-10_0030.png[/IMG]

FYI: I did make a post about this in the Veracrypt forums buts it been over 24 with no reply so I decided to try here.
Update from veracrypt forum:I was told post my question on a Linux forum as opposed to a Veracrypt forum because, "[COLOR=#555555][FONT=sans-serif]this is a question which experienced Linux users could answer"[/FONT][/COLOR]

---

### Post by uncommonw on 2016-11-11
Managed to mount the drive on a folder with normal access to users and groups. But still having trouble accessing from windows. Still get the same window error above. So maybe its not a permission issue?

---

