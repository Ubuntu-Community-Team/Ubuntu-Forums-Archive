---
title: "Ubuntu Menu Bar Option for LibreOffice"
date: 2013-06-03
forum: General Help
---

### Post by foberle on 2013-06-03
Hi: 

I'm using LibreOffice 4.0.3.3 rather than the version included  with Ubuntu 12.04LTS for various reasons, but one thing I would like to  know is whether or not there is an add-on (pretty sure there used to be one for LibreOffice 3.5) that  will let LibreOffice use the Ubuntu menu systems and the Heads Up Display (which  is helpful for the commands I don't often use). 

Does anyone know if this exists and, if so, where I can download it? 

Thanks.

---

### Post by gifford on 2013-06-03
I'm also using 4.0.3.3 in Ubuntu 12.04.2 and have the global menu. It came with 4.0.3.3.
How did you install Libreoffice 4.0.3.3? As for the older add-on, it was lo menu.
If I were you, I would do a reinstall of libreoffice but first purge you existing configuration.
[COLOR=#000000]sudo apt-get purge libreoffice*
[/COLOR]then add the following ppa.
[COLOR=#000000]sudo add- apt-repository ppa: libreoffice/ppa[/COLOR]
[COLOR=#000000]sudo apt-get update
[/COLOR][COLOR=#000000]sudo apt-get install libreoffice[/COLOR]
[COLOR=#000000]This ppa will give you libreoffice 4.0X and give you the updates as well.[/COLOR]

---

