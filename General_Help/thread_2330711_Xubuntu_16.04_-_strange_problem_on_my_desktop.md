---
title: "Xubuntu 16.04 - strange problem on my desktop"
date: 2016-07-14
forum: General Help
---

### Post by ardouronerous on 2016-07-14
[ATTACH=CONFIG]270095[/ATTACH]

As you can see on the screenshot, the icon labels are misaligned. This behavior only happens on the desktop, but not on any other application.

---

### Post by Bucky Ball on 2016-07-14
Well, 'File System' looks fine, 'Home' looks fine, but Trash and the Anti-virus ones don't. Were those desktop launchers created by the apps when they were installed or did you create them manually?

If the latter, you may have left a bunch of spaces or perhaps even hit tab at the end of the launcher name when naming the launcher.

---

### Post by ardouronerous on 2016-07-14
[ATTACH=CONFIG]270097[/ATTACH]
There all misaligned.
Never created these, Home, Trash and File System are the defaults, well, expect for Comodo Antivirus of course.

---

### Post by ardouronerous on 2016-07-14
[ATTACH=CONFIG]270098[/ATTACH]
Here's another problem I found, when I move the icons, it leaves a trace of the icon labels.

---

### Post by Bucky Ball on 2016-07-14
That's better. Much easier to see the problem, which appears to be that the icons names are aligned, but in black, and this version is displacing the white names. Hmm. 

If you right click the desktop> Desktop Settings> Icon Type> is that set to 'File/launcher'?

Also, check Applications> Settings> Appearance> Fonts. How are the settings there? Do you have anti-aliasing on? If so, under 'Rendering', set 'Hinting' to 'None'. Any different? Not sure if you need to logout and in to see the changes or restart.  

Try tweaking and experimenting and see if it changes anything. 

With any luck someone will arrive who knows a simple fix for this, but in the meantime, have you found anyone else on the big, wide net that has had this issue or something similar?

---

### Post by ardouronerous on 2016-07-14
Yeah, I've tried icon type to none and back to File/Launcher icons, I've tried unchecking the default icons as well.
I've noticed that when I change icon types to none, the icons vanish as well as the labels, but when I uncheck default icons, the white labels are left behind, as you can see on the third screenshot.

Changing Hinting to None doesn't fix it either.

It wasn't like this yesterday, it only started when I received updates, here's the update log;
> 
Start-Date: 2016-07-13  11:44:06
Commandline: /usr/bin/unattended-upgrade
Upgrade: libnss3-nssdb:i386 (2:3.21-1ubuntu4, 2:3.23-0ubuntu0.16.04.1), libgd3:i386 (2.1.1-4ubuntu0.16.04.1, 2.1.1-4ubuntu0.16.04.2), pidgin:i386 (1:2.10.12-0ubuntu5, 1:2.10.12-0ubuntu5.1), libpurple-bin:i386 (1:2.10.12-0ubuntu5, 1:2.10.12-0ubuntu5.1), libpurple0:i386 (1:2.10.12-0ubuntu5, 1:2.10.12-0ubuntu5.1), pidgin-data:i386 (1:2.10.12-0ubuntu5, 1:2.10.12-0ubuntu5.1), libnss3:i386 (2:3.21-1ubuntu4, 2:3.23-0ubuntu0.16.04.1), libnspr4:i386 (2:4.11-1ubuntu1, 2:4.12-0ubuntu0.16.04.1)
End-Date: 2016-07-13  11:44:37

Start-Date: 2016-07-13  14:57:03
Commandline: /usr/sbin/synaptic
Upgrade: gir1.2-gtk-3.0:i386 (3.18.9-1ubuntu3, 3.18.9-1ubuntu3.1), gir1.2-gmenu-3.0:i386 (3.13.3-6ubuntu3, 3.13.3-6ubuntu3.1), libgtk-3-common:i386 (3.18.9-1ubuntu3, 3.18.9-1ubuntu3.1), libgtk-3-0:i386 (3.18.9-1ubuntu3, 3.18.9-1ubuntu3.1), libunity-protocol-private0:i386 (7.1.4+15.10.20151002-0ubuntu2, 7.1.4+16.04.20160701-0ubuntu1), gtk2-engines-murrine:i386 (0.98.2-0ubuntu2, 0.98.2-0ubuntu2.1), libgtk-3-bin:i386 (3.18.9-1ubuntu3, 3.18.9-1ubuntu3.1), libwnck-common:i386 (1:2.30.7-5ubuntu1, 1:2.30.7-5ubuntu1.1), libunity9:i386 (7.1.4+15.10.20151002-0ubuntu2, 7.1.4+16.04.20160701-0ubuntu1), libgnome-menu-3-0:i386 (3.13.3-6ubuntu3, 3.13.3-6ubuntu3.1), libunity-scopes-json-def-desktop:i386 (7.1.4+15.10.20151002-0ubuntu2, 7.1.4+16.04.20160701-0ubuntu1), libwnck22:i386 (1:2.30.7-5ubuntu1, 1:2.30.7-5ubuntu1.1), gnome-menus:i386 (3.13.3-6ubuntu3, 3.13.3-6ubuntu3.1)
End-Date: 2016-07-13  14:57:19

---

### Post by Toz on 2016-07-14
Its a bug in the [gtk2-engine-murrine](https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/1598316) package. Downgrading the package will temporarily resolve the issue until the bug is fixed.

To downgrade, look to see if you have the file gtk2-engines-murrine_0.98.2-0ubuntu2.*.deb (replace the * with your architecture like amd64 or i386) in /var/cache/apt/archives or get the file from [https://launchpad.net/ubuntu/+source/gtk2-engines-murrine](https://launchpad.net/ubuntu/+source/gtk2-engines-murrine). Simply install the file via:
```
sudo dpkg -i .....
```
...and log out and back in again.

EDIT: Some more info....
[Here](https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/1294699) is the patch that was applied to gtk2-engines-murrine to fix another problem, but has resulted in this side effect. It also only appears to affect some themes like Numix (Greybird) is not affected. If you switch between themes you need to also refresh xfdesktop to see if the new theme is affected:
```
xfdesktop -R
```

So it looks like the bug might be in either gtk2-engines-murrine or in the Numix theme.

---

### Post by linkinpunk on 2016-08-04
the same problem after the upgrade from 14.06 to 16.06
[ATTACH=CONFIG]270570[/ATTACH]

---

