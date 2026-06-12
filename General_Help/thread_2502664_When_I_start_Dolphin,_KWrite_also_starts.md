---
title: "When I start Dolphin, KWrite also starts"
date: 2024-11-23
forum: General Help
---

### Post by massimiliano-polito on 2024-11-23
Whenever Dolphin is started (because I launch it from the application menu or by clicking on the Trash widget or even from the command line) at the same time also KWrite opens. It's really annoying. It started today but I'm not aware of any configuration change that could cause such a behaviour.

I made some internet searches and all what I found was a couple of configuration issues that could cause the system to open .desktop files but I don't have that configuration.

1) Dolphin configuration doesn't say that Dolphin should execute an executable file but just asking what to do (see attached picture);

2) the kiorc file doesn't have any parameters set to automatically start applications:
```

max@ASUS-V221IC:~/.config$ cat kiorc 
[Confirmations] 
ConfirmDelete=true 
ConfirmEmptyTrash=true 
ConfirmTrash=false 

max@ASUS-V221IC:~/.config$ 

```

When I run Dolphin from the command line this is what I read:

```
max@ASUS-V221IC:~/.config$ dolphin  
kf.coreaddons: KDirWatch: "/boot/grub/themes/ubuntustudio/theme.txt" is a file. Use addFile! 
kf.kio.core: "/boot/grub/themes/ubuntustudio/theme.txt is a file, but a folder was expected." 
kf.kio.core: "The file or folder /home/max/Desktop/pippo.sh does not exist." 
Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes. 
kf.sonnet.clients.hspell: HSpellDict::HSpellDict: Init failed 
max@ASUS-V221IC:~/.config$ 

```

(/boot/grub/themes/ubuntustudio/theme.txt is the last file I opened with KWrite)

Any idea about how to address the problem?

Ciao,
Max

---

### Post by massimiliano-polito on 2024-11-24
I've found the problem.

In the "Startup" tab of Dolphin configuration, parameter "Show on startup" had been configured to "Folders, tabs, and window state from last time". To solve the problem I just checked the following checkbox, the one when a directory is specified, and it stopped starting KWrite.

Funny enough... in my searching for a solution I uninstalled KWrite and Dolphin started opening Kate. I uninstalled Kate and it started opening LibreOffice. I uninstalled LibreOffice and it started opening Okular. I uninstalled Okular and then finally there was no SW left to open text files. At that point Dolphin asked me how to open "theme.txt" and I had the suspect it was just executing some startup command...

Ciao,
Max

---

