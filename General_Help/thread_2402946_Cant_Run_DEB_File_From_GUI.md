---
title: "Cant Run DEB File From GUI"
date: 2018-10-05
forum: General Help
---

### Post by JengaBlocks on 2018-10-05
Go to File Manager
Double click on .DEB file
Window comes up with name of package
Click Install button

Nothing happens.

Installed GDebi:
sudo apt install gdebi
Went to File Manager
Right clicked on .deb
Open With GDebi Package Installer

Didn't work.


BTW, I'm using XFCE4.

---

### Post by oldos2er on 2018-10-05
Which version of Ubuntu (or other flavor)?

---

### Post by JengaBlocks on 2018-10-05
Ubuntu Desktop 18.04 Bionic Beaver

---

### Post by JengaBlocks on 2018-10-05
Ok, so I got this to work with:

sudo dkpg -i (name of deb)

This also worked:

sudo gdebi (name of deb)


Still doesn't make sense why this is not running from GUI. I'm running XFCE4.

---

### Post by again? on 2018-10-06
Clicking a deb here in Xubuntu 18.04 brings up gnome-software to install the deb.
gdebi isn't installed.
[ATTACH=CONFIG]281262[/ATTACH]

If you've just installed xfce in Ubuntu you may need to tweak or install something or
perhaps install the complete Xubuntu package ...**xubuntu-desktop** 
*/usr/share/applications/mimeinfo.cache* shows...
```
application/x-deb=engrampa.desktop;**gnome-software-local-file.desktop**;org.gnome.FileRoller.desktop;
```
_/usr/share/applications/gnome-software-local-file.desktop_
```
[Desktop Entry]
Name=Software Install
Comment=Install selected software on the system
Categories=System;
Exec=**gnome-software --local-filename=%f**
Terminal=false
Type=Application
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon[af]=system-software-install
Icon[bg]=system-software-install
Icon[ca]=system-software-install
Icon[ca@valencia]=system-software-install
Icon[cs]=system-software-install
Icon[da]=system-software-install
Icon[de]=system-software-install
Icon[el]=system-software-install
Icon[en_GB]=system-software-install
Icon[es]=system-software-install
Icon[eu]=system-software-install
Icon[fa]=system-software-install
Icon[fi]=system-software-install
Icon[fr]=system-software-install
Icon[fur]=system-software-install
Icon[gd]=system-software-install
Icon[gl]=system-software-install
Icon[hr]=system-software-install
Icon[hu]=system-software-install
Icon[id]=system-software-install
Icon[it]=system-software-install
Icon[ja]=system-software-install
Icon[kk]=system-software-install
Icon[ko]=system-software-install
Icon[lv]=system-software-install
Icon[lt]=system-software-install
Icon[nb]=system-software-install
Icon[ne]=system-software-install
Icon[nl]=system-software-install
Icon[oc]=system-software-install
Icon[pa]=system-software-install
Icon[pl]=system-software-install
Icon[pt_BR]=system-software-install
Icon[ro]=system-software-install
Icon[ru]=system-software-install
Icon[sk]=system-software-install
Icon[sl]=system-software-install
Icon[sr]=system-software-install
Icon[sr@latin]=system-software-install
Icon[sv]=system-software-install
Icon[tr]=system-software-install
Icon[zh_CN]=system-software-install
Icon[zh_TW]=system-software-install
Icon=system-software-install
StartupNotify=true
NoDisplay=true
MimeType=application/x-rpm;application/x-redhat-package-manager;application/x-deb;application/x-app-package;application/vnd.ms-cab-compressed;application/vnd.flatpak;application/vnd.flatpak.repo;application/vnd.flatpak.ref;application/vnd.snap;
X-Ubuntu-Gettext-Domain=gnome-software
```


I always use apt in any case as it resolves dependencies. (dpkg -i Does not resolve dependencies)
To install a deb using apt...
```
sudo apt install [COLOR="#696969"]/full/path/to/deb[/COLOR]
```

****Note**: even if you open a terminal in the directory where the deb is you still need to use the full path to the deb.

---

### Post by ajgreeny on 2018-10-06
I have also occasionally found that gdebi does not start when double clicking on a package.deb file in my file manager; I'm also using Xubuntu 18.04.

It is an annoyance but I just run ```
sudo apt install /full/path/to/file.deb
``` as mentioned by guber2, so I have not reported this as a bug, which perhaps I should do, but it does make gdebi rather superfluous, hence my lack of action.

Other times gdebi works with no problem, so I wonder if it is something to do with permissions of the .deb files, something I must look into a bit deeper, though I have nothing to install at present.

---

### Post by dragonfly41 on 2018-10-06
When using GDebi I tend to launch GDebi first, then apply File > Open,
select the deb package, then hit Install.  
Usually the package to be installed is found in ~/Downloads

---

