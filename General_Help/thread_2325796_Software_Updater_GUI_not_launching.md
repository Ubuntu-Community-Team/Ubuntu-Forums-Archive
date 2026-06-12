---
title: "Software Updater GUI not launching"
date: 2016-05-25
forum: General Help
---

### Post by Bucky Ball on 2016-05-25
Hi all,

Xubuntu 14.04 on Toshiba Tecra R950.

About a year and a half ago I set a friend up with a new computer for uni and installed Xubuntu 14.04 LTS on it for them. 'Just works' and has been doing so for that whole time, until now.

The Software Updater GUI will no longer launch and it no longer notifies of updates (from what my friend is saying). It launches fine from a terminal with:

```
gksudo update-manager
```

... but attempting to launch Software Updater from the entry under 'Application>Settings', nothing happens. No GUI appears.

Note well: simply telling the user to update via a terminal is _not_ an option. User just wants to switch on and click buttons and the machine just works. They are not tech savvy at all (they refuse to even come on here for a clue). 

Naturally I've searched for answers but found little and nothing that worked. I have removed/purged and reinstalled update-manager to no avail. I currently have the machine to fix and can try suggestions and give any further info. Just ask. 

Any clues or ideas greatly appreciated and TNX in advance.

---

### Post by howefield on 2016-05-25
Does the .desktop file look ok ?

```
[Desktop Entry]
Name=Software Updater
GenericName=Software Updates
Comment=Show and install available updates
Exec=/usr/bin/update-manager
Icon=system-software-update
Terminal=false
Type=Application
Categories=System;Settings;
X-Ubuntu-Gettext-Domain=update-manager
X-Unity-IconBackgroundColor=#4c9e39
```

---

### Post by Bucky Ball on 2016-05-26
Bingo. I found the .desktop file here.

```
 ~/.local/share/applications/
```

I had this:

```
[Desktop Entry]
Name=Software Updater
GenericName=Software Updates
Comment=Show and install available updates
Exec=/usr/bin/update-manager
Icon=system-software-update
Terminal=true
Type=Application
Categories=System;Settings;
X-Ubuntu-Gettext-Domain=update-manager
X-Unity-IconBackgroundColor=#4c9e39
Path=
StartupNotify=true
```

Changed it to this:
```

[Desktop Entry]
Name=Software Updater
GenericName=Software Updates
Comment=Show and install available updates
Exec=/usr/bin/update-manager
Icon=system-software-update
Terminal=**false**
Type=Application
Categories=System;Settings;
X-Ubuntu-Gettext-Domain=update-manager
X-Unity-IconBackgroundColor=#4c9e39
**#** Path=
**#** StartupNotify=true
```

Not sure if hashing out the last two lines was necessary. They made no difference alone but changed 'Terminal=' from true to false in combo and that did the trick. Clicked 'Software Updater' in the Apps menu and up it popped. :)

Thanks howefield. Was digging around for a couple of hours with this yesterday/last night. Solved.

---

### Post by howefield on 2016-05-26
Cool, glad you got it.

I'd have expected you to get the .desktop file in 

```
/usr/share/applications/
```

but as long as you got there, it doesn't matter.

The "*StartupNotify=true*" shouldn't make any difference to whether or not the application starts or not, but may give the user visual clues that is loading, as I understand it. Not critical but can be useful.

[https://developer.gnome.org/integration-guide/stable/startup-notification.html.en](https://developer.gnome.org/integration-guide/stable/startup-notification.html.en)

The path field without a path being set probably makes no difference :)

---

