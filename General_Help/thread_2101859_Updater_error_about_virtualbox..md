---
title: "Updater error about virtualbox."
date: 2013-01-05
forum: General Help
---

### Post by ubto66 on 2013-01-05
Ubuntu 12.04
gnome environment.

In terminal I downloaded virtualbox key 
sudo apt-key add oracle_vbox.asc
But did not finish the installation of virtualbox.
Virtualbox 4.1.12_ubuntur77245.
was already installed, using software centre.

When running update manager I now get this error message:W:Failed to fetch [http://download.virtualbox.org/virtualbox/](http://download.virtualbox.org/virtualbox/)
debian/dists/precise/InRelease Unable to find expected entry 
'contrib/source/Sources' inRelease file (Wrong sources.list 
entry or malformed file)
,E:some index files failed to download. They have been ignored, 
or old ones used instead.

How can I end the error messages? 

Thank you.

---

### Post by Rebelli0us on 2013-01-05
Uncheck "source code" in Software Sources.

---

### Post by ubto66 on 2013-01-07
Thank you for your answer.

Location: software centre -> edit -> software sources -> other software.
[COLOR=#000000][FONT=Sans Serif]http://download.virtualbox.org/virtualbox/debian precise contrib[/FONT][/COLOR]
[COLOR=#000000][FONT=Sans Serif]http://download.virtualbox.org/virtualbox/debian precise contrib (Source Code)

Are these 2 those who should be unchecked?

[/FONT][/COLOR]

---

### Post by Rebelli0us on 2013-01-07
> **ubto66 said:**
> Thank you for your answer.

Location: software centre -> edit -> software sources -> other software.
[COLOR=#000000][FONT=Sans Serif]http://download.virtualbox.org/virtualbox/debian precise contrib[/FONT][/COLOR]
[COLOR=#000000][FONT=Sans Serif]http://download.virtualbox.org/virtualbox/debian precise contrib (Source Code)

Are these 2 those who should be unchecked?

[/FONT][/COLOR]

No, just uncheck "(Source Code)" as I noted above.

---

### Post by ubto66 on 2013-01-08
Location software centre -> edit -> software sources -> ubuntu software

The source code box was never checked.

But the error messages remains.

Suggestions?
Thanks.

---

