---
title: "Exporting installed package as .deb file?"
date: 2017-01-21
forum: General Help
---

### Post by peter1897 on 2017-01-21
I installed **dpkg-repack** but when i try to export installed package as .deb file and then try to install this .deb package on another machine i get missing dependencies error. How to export all dependencies along with the package i want to export? How to find which dependencies the package i want to export is using?

---

### Post by cogier2 on 2017-01-21
Open Terminal and navigate to the folder where the .deb file is. Type **dpkg -I *.deb | grep Depends:** (Replace the * with the name of your .deb file). This will give you a list of the dependencies required.

---

### Post by peter1897 on 2017-01-21
The command doesn't work. It say 'no found package' and i entered the name of the package correctly.

---

### Post by dragonfly41 on 2017-01-21
Try this command ...

apt-cache depends <name_of_package>

e.g. apt-cache depends abiword

---

### Post by peter1897 on 2017-01-21
I am trying to export Dockbarx package and if i run 'apt-cache depends dockbarx' i get this:
```
osboxes@osboxes:~$ apt-cache depends dockbarx
dockbarx
  Depends: dockbarx-dockx
  Recommends: gnomepanel-applet-dockbarx
```

But there are also other packages that are related to Dockbarx:
```
osboxes@osboxes:~$ dpkg -l | grep dockbarx
ii  awn-applet-dockbarx                       0.92-1~webupd8~trusty4                      all          Avant Window Navigator DockBarX applet
ii  dockbarx                                  0.92-1~webupd8~trusty4                      all          DockBarX, an icon-based taskbar
ii  dockbarx-applet-appindicator              0.92-1~webupd8~trusty4                      all          DockBarX DockX AppIndicator applet
ii  dockbarx-applet-battery-status            0.92-1~webupd8~trusty4                      all          DockBarX DockX Battery Status applet
ii  dockbarx-applet-cardapio                  0.92-1~webupd8~trusty4                      all          DockBarX DockX Cardapio applet
ii  dockbarx-applet-clock                     0.92-1~webupd8~trusty4                      all          DockBarX DockX Clock applet
ii  dockbarx-applet-hello-world               0.92-1~webupd8~trusty4                      all          DockBarX DockX Hello World applet
ii  dockbarx-applet-namebar                   0.92-1~webupd8~trusty4                      all          DockBarX DockX Namebar applet
ii  dockbarx-applet-volume-control            0.92-1~webupd8~trusty4                      all          DockBarX DockX Volume Control applet
ii  dockbarx-common                           0.92-1~webupd8~trusty4                      all          DockBarX common files
ii  dockbarx-dockx                            0.92-1~webupd8~trusty4                      all          The stand-alone DockBarX dock called DockX
ii  dockbarx-themes-extra                     2.1-1~2                                     all          DockBarX themes
ii  xfce4-dockbarx-plugin                     0.4.1-1~webupd8~trusty2                     i386         DockBarX plugin for Xfce
```

---

### Post by dragonfly41 on 2017-01-21
I'm only surmising from my own reading,  since I don't use dpkg-repack but

(a) the package appears to have been installed as PPA ([COLOR=#000000][FONT=Ubuntu Mono]webupd8~trusty40) and I don't know if PPA dependencies are listed by "depends"[/FONT][/COLOR]

(b) I don't see fakeroot used in your dpkg-repack command string

(c) Here are some _very old_ notes found in quick search ("dpkg-repack NEAR PPA")

[https://www.reddit.com/r/Ubuntu/comments/n8z50/how_the_heck_do_i_backup_only_my_applications/](https://www.reddit.com/r/Ubuntu/comments/n8z50/how_the_heck_do_i_backup_only_my_applications/)

See the last notes referring to PPA.

---

