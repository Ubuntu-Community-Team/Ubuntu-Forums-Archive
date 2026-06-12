---
title: "need help to create install/remove script in deb"
date: 2008-06-10
forum: General Help
---

### Post by chunchengch on 2008-06-10
I am trying to create a deb to install new battery icons to replace the old ones, I plan to rename these old icons, so they can be retrieved when I remove the new icons.

I create preinst and postrm scripts as follows and make them executable, but the installation is aborted because of permission problem and causes a package index error, I am still new to create install/remove scripts, and hope someone can help me to solve it, thanks a lot!


_preinst script_

[COLOR="SeaGreen"]#!/bin/bash
sudo mv /usr/share/gnome-power-manager/icons/hicolor/16x16/status/gpm-primary-000.png /usr/share/gnome-power-manager/icons/hicolor/16x16/status/gpm-primary-000-old.png
...
[/COLOR]

_postrm script_

[COLOR="SeaGreen"]#!/bin/bash
sudo mv /usr/share/gnome-power-manager/icons/hicolor/16x16/status/gpm-primary-000-old.png /usr/share/gnome-power-manager/icons/hicolor/16x16/status/gpm-primary-000.png
...[/COLOR]

---

### Post by hal10000 on 2008-06-10
I guess you should remove the two [COLOR="Red"]sudo[/COLOR] entries in your scritpts and instead run the scripts with [COLOR="Red"]sudo preinst[/COLOR] and [COLOR="Red"]sudo postinst[/COLOR].

The preinst and postinst scripts (and usually all files inside a .deb package ) should be owned by root and installe with sudo.

---

### Post by chunchengch on 2008-06-10
> **hal10000 said:**
> I guess you should remove the two [COLOR="Red"]sudo[/COLOR] entries in your scritpts and instead run the scripts with [COLOR="Red"]sudo preinst[/COLOR] and [COLOR="Red"]sudo postinst[/COLOR].

The preinst and postinst scripts (and usually all files inside a .deb package ) should be owned by root and installe with sudo.


Thanks for reply!

1. I don't understand, How can you run [COLOR="Red"]sudo preinst[/COLOR] and [COLOR="Red"]sudo postinst[/COLOR] inside a deb package?

2. I believe all the deb packages, or the most of, are all executed with the root privilege. you said The preinst and postinst scripts should be owned by root, but I inspect inside other deb packages, such as brasero, I do not find this limitation, why?

---

### Post by hal10000 on 2008-06-10
> How can you run sudo preinst and sudo postinst inside a deb package?


Of course you are right, you usually don't run it with sudo **inside** the deb-package, but you usually install a deb package with sudo and thus your preinst/postinst script is run with sudo (in a way). ANd after you installed a deb package, the corresponding preinst/postinst scripts go to /var/lib/dpkg/info/ and these scripts can be run manually (with sudo).
When i look into the /var/lib/dpkg/info/ directory i can not find a script which is not owned by root (at least on my machine)

WHat i don't understand is why are you using sudo inside your script, i believe it's not necessary because if you install a deb package you usually do this with sudo (or as root).

I think if you have a preinst/posinst script with a sudo command inside then maybe these scripts ask for your password, but the installation process (of the debian package) is going on and so you don't have the chance to type your password and maybe this is the reason why your installation is aborted.

---

### Post by chunchengch on 2008-06-11
Thanks!

I remove [COLOR="Red"]sudo[/COLOR] from the scripts, and they do work, but there is one thing weird, the deb executes postrm first instead of preinst.

I try to rename the postrm to prerm and preinst to postrm, then rebuild the deb, now the deb do execute the rename procedure in postrm, but it does not install the icons because the icons of same filename are also in the target folder, but the reality is all the files are already renamed, do I miss something?

[ATTACH]73641[/ATTACH]


PS: I search on the web and still can not find detailed instructions of these install/remove scripts, any information will be appreciated.

---

### Post by hal10000 on 2008-06-11
I have no experience in writing debian packaging-scripts, but i found something in the [COLOR="Red"]Debian Policy Manual[/COLOR] which might be helpful for you:
[http://debid.vlsm.org/share/Debian-Doc/debian-policy/ch-maintainerscripts.html]("http://debid.vlsm.org/share/Debian-Doc/debian-policy/ch-maintainerscripts.html"). I guess especially chapter 6.5 tells something about your problem.

---

