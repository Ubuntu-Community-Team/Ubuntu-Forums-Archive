---
title: "cannot adjust system"
date: 2017-10-09
forum: General Help
---

### Post by geomcd1949 on 2017-10-09
In addition to being unable to change selections in system settings:

[https://ubuntuforums.org/showthread.php?t=2372896](https://ubuntuforums.org/showthread.php?t=2372896)

am also unable to install or delete programs from the Software Center. When I try to install any program, I get this Authentication Error message:

Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.238'}): org.debian.apt.install-or-remove-packages

Ubuntu 16.04.3 LTS
Intel i-7 3770
Quadro K4200

---

### Post by ajgreeny on 2017-10-09
Check in your autostart programs that the **PolicyKit Authentication Agent** is selected to start at session startup and if not add it or select the tick-box.

This is a known problem in the current 17.10 beta but I have not heard of it in 16.04.

---

### Post by geomcd1949 on 2017-10-09
Thanks ajgreenny. Enabling [COLOR=#000000] [/COLOR]**PolicyKit Authentication Agent  **[B]allowed the changes to be made. Appreciate the help.
~George[/B]

---

