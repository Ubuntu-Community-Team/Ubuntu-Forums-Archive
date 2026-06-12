---
title: "RDesktop 1.4 (RDP5 support)"
date: 2005-04-19
forum: General Help
---

### Post by hndrcks on 2005-04-19
I am interested in getting printer redirection and cut-and-paste functionality working in the RDP / Terminal Services client; it looks like I will need to upgrade the rdesktop from 1.3.1 - 1.40 to support RDP5. Anyone done this? Are there any 'gotchas' I should look out for?

---

### Post by speedman on 2005-04-19
rdesktop 1.3.1 already supports RDP version 5 with the -5 flag.  Copy and paste works fine between Windows Terminal sessions and Gnome.  I haven't tried the printer redirection however.

From man rdesktop with the default package installed by Hoary:

OPTIONS
-5     Use RDP version 5 (default).


Regards,

SM

---

### Post by hndrcks on 2005-04-19
Thanks sir. It does support v5 and audio redir but not 5.1 or 5.2, where the printer and local drive redirection sit. Looks like 1.40 has preliminary support for printer redirection; I will attempt to install and keep everyone apprised (if you even care!)

---

### Post by hndrcks on 2005-04-19
Update: grabbed the .deb from Debian Unstable [http://packages.debian.org/unstable/x11/rdesktop](http://packages.debian.org/unstable/x11/rdesktop)
Installed without complaint. Successfully redirected a local floppy drive. w00t! The printer redirected too, but my windows test page was gobbledygook - will work on that later.

---

### Post by speedman on 2005-04-19
[QUOTE=hndrcks]I will attempt to install and keep everyone apprised (if you even care!)[/QUOTE]

Absolutely.  :) 

Glad to see you made some progress.


Regards,

SM

---

