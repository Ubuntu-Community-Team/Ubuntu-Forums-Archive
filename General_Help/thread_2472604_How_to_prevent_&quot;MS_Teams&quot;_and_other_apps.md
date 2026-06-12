---
title: "How to prevent &quot;MS Teams&quot; and other apps from modifying &quot;Startup Applications&quot;"
date: 2022-03-05
forum: General Help
---

### Post by cigtoxdoc on 2022-03-05
"Ms Teams" is a fact-of-life for those of us who participate in on-line conferences.  The Linux version of MS Teams under Ubuntu 21.10 often works better than the Win 10 version running under Windowa.  Only drawback is MS Teams modifies that it modifies the file (or files ?) that control the program "Startup Applications".  How do I write-protect those files so that MS Teams cannot insert itself in the list of startup applications?

Thank you,

John

---

### Post by dragonfly41 on 2022-03-05
There is a Ubuntu app .. Startup Applications Preferences .. and you can disable/remove apps from the list.
I would hope that this would apply for your MS Teams app but it might be smart enough to restore in the list.
Another management tool is Stacer.

---

### Post by GhX6GZMB on 2022-03-05
No external program should be able to modify your system.
How are you logged in? Main user or normal user?

The problem might be the "normal user" permissions, where the configuration files are stored in $HOME. This includes the application menu.
I recommend excluding "other" from your $HOME directory by executing the following commands from the terminal:
```
cd
sudo chmod o-rwx -R ./* ./.[!.]*
```
This will remove all rights from "other" users in your home- and subdirectories. From now on, only you and "group" (depending on permissions) can change something. It's not detrimental, and default after 20.10, I believe.

Cheers.

---

### Post by vanadium on 2022-03-06
There is a setting in the app to disable autostart.

---

### Post by cigtoxdoc on 2022-03-10
Thank you, John

---

