---
title: "Dependency/dpkg error prevents me from installing or doing anything"
date: 2019-08-05
forum: General Help
---

### Post by griffinb on 2019-08-05
Hey, 

I tried to install and get gnome working, and now whenever I try to install anything I get this issue:

[FONT=courier new]Setting up gedit-plugin-terminal (3.28.1-1) ...
/var/lib/dpkg/info/gedit-plugin-terminal.postinst: 6: /var/lib/dpkg/info/gedit-plugin-terminal.postinst: py3compile: not found
dpkg: error processing package gedit-plugin-terminal (--configure):
 installed gedit-plugin-terminal package post-installation script subprocess returned error exit status 127[/FONT]

and I get it for every single one of the programs below:

Errors were [FONT=courier new]encountered while processing:
 gedit-plugin-terminal
 caribou
 gedit-plugin-join-lines
 gedit-plugin-smart-spaces
 gedit-plugin-commander
 gedit-plugin-git
 gedit-plugin-multi-edit
 language-selector-common
 gedit-plugin-dashboard
 gedit-plugin-translate
 gedit-plugin-character-map
 gedit-plugin-code-comment
 python3-scour
 scour
 gdebi-core
 python3-wheel
 gedit-plugin-synctex
 gnome-music
 gnome-tweaks
 gedit-plugin-color-picker
 ubuntu-system-service
 python-scour
 gedit-plugin-bracket-completion
 python3-pip
 gedit-plugin-color-schemer
 update-manager
 python3-setuptools
 language-selector-gnome
 dh-python
 gdebi
 python3-dev
 gnome-control-center

[/FONT]Any help on this would be greatly appreciated!

---

