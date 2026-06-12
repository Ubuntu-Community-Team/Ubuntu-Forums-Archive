---
title: "Libreoffice Kickoff"
date: 2024-07-16
forum: General Help
---

### Post by mikegreen8 on 2024-07-16
Ubuntu 22.04 

Hi.

I've just updated libreoffice 7.6 ---> 24.2

Now I have to change all my libreoffice menu items
from 'libreoffice7.6 --writer'  TO  'libreoffice24.2 --writer'

Is there a central way to do this such that when I update to a newer version of libreoffice, I don't have to change a dozen or so menu items?

Thanks,
M...

---

### Post by him610 on 2024-07-16
FWIW, I normally use the LibreOffice version that comes with LTS 22.04.? or 24.04.?. 
Never thought about downloading and installing a just released version from the libreoffice.org; I think it is begging for issues.

Have you tried [https://ask.libreoffice.org/]("https://ask.libreoffice.org/")

---

### Post by mikegreen8 on 2024-07-17
I like to keep up to date.

Is there some way to have a sort of association link - i.e. when i enter 'libreoffice', 'libreofficex.y' is invoked? That way it would only be changed in one place. 

 I will try the link.

Thanks for you help,
M...

---

### Post by Holger_Gehrke on 2024-07-17
Are you talking about the items in whatever graphical starter your DE uses ? Those are generated from text files with the extension '.desktop' in several well-known directories (most prominently '/usr/share/applications' (system-wide, programs installed through traditional  package management), '/usr/local/share/applications/' (system-wide, programs installed from source or developed locally, '/var/lib/snapd/desktop/applications/' (system-wide, installed as snap-packages), and '~/.local/share/applications/' (user-specific)). The 'Name'-line in the '.desktop files is used as a key and files with the same key override each other in the order in which the files are read. The user-specific files are read last, so what's in them overrides system-wide settings. So you could copy the system-wide starters to your user directory and change them to run whatever program with whatever options you want or need.

Alternatively: '/usr/bin/libreoffice' as installed by the package from the repositories is already a symbolic link pointing at '/usr/lib/libreoffice/program/soffice'. Erasing that link and making a new one ('sudo ln -s /path/and/filename/of/NewLibreOffice /usr/bin/libreoffice', replace the obvious placeholder) pointing to the new program should work; be aware though that this change is probably going to be overwritten by any update to the installed older libreoffice.

Holger

---

### Post by mikegreen8 on 2024-07-17
Good info.

Thanks.

---

