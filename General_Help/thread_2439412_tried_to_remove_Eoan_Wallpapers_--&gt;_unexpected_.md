---
title: "tried to remove Eoan Wallpapers --&gt; unexpected result"
date: 2020-03-27
forum: General Help
---

### Post by amano on 2020-03-27
```
amano@amano-desktop:~$ **sudo apt purge ubuntu-wallpapers-eoan**
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  fonts-cantarell fprintd gir1.2-graphene-1.0 gir1.2-mutter-6 gir1.2-nma-1.0
  libfprint-2-2 libfprint-2-tod1 libpam-fprintd ubuntu-wallpapers-cosmic
  ubuntu-wallpapers-disco
Verwenden Sie »sudo apt autoremove«, um sie zu entfernen.
Die folgenden zusätzlichen Pakete werden installiert:
  policykit-1-gnome
Die folgenden Pakete werden ENTFERNT:
  chrome-gnome-shell* gdm3* gnome-session* gnome-shell*
  gnome-shell-extension-appindicator* gnome-shell-extension-desktop-icons*
  gnome-shell-extension-ubuntu-dock* ubuntu-desktop* ubuntu-desktop-minimal*
  ubuntu-session* ubuntu-wallpapers* ubuntu-wallpapers-eoan*
Die folgenden NEUEN Pakete werden installiert:
  policykit-1-gnome
0 aktualisiert, 1 neu installiert, 12 zu entfernen und 0 nicht aktualisiert.
Es müssen 25,0 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 18,4 MB Plattenplatz freigegeben.
Möchten Sie fortfahren? [J/n] **n**
Abbruch.
```

Why do the old wallpapers have so many dependencies? Is that a bug?

---

### Post by slickymaster on 2020-03-27
*Thread moved to **General Help**.*

---

### Post by deadflowr on 2020-03-27
You're thinking in the opposite direction.
ubuntu-wallpapers-eoan is a dependency of ubuntu-wallpapers which is a dependency of gnome-shell.
And without gnome-shell all those are packages go out the window too.

I don't think this is a bug, [s]just a matter of the wallpapers for focal aren't there yet.
When they are, they should be switching the dependency version to that. One would assume.[/s]

Edit: Somehow I assumed this was focal related.
But there's no clear evidence posted to suggest that.

---

