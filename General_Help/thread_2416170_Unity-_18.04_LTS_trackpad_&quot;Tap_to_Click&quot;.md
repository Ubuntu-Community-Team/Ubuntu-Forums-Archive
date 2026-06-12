---
title: "Unity- 18.04 LTS trackpad &quot;Tap to Click&quot; problems"
date: 2019-04-06
forum: General Help
---

### Post by jhusch on 2019-04-06
Hello,

thanks for opening this thread - even if it says [SOLVED] I have some problems:
Ubuntu 18.04.2, just changed to Unity, Tap Click is not working.
Tried above procedure, but gut the following message for 

```
sudo apt install xserver-xorg-input-synaptics
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder, wenn Sie die
Unstable-Distribution verwenden, dass einige erforderliche Pakete noch
nicht erstellt wurden oder Incoming noch nicht verlassen haben.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben unerfüllte Abhängigkeiten: (unmet dependencies):
 xserver-xorg-input-synaptics : Hängt ab von: xserver-xorg-core (>= 2:1.18.99.901)
E: Probleme können nicht korrigiert werden, Sie haben zurückgehaltene defekte Pakete.

```

Trying to install xserver-xorg-core:

```
sudo apt install xserver-xorg-core
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
Vorgeschlagene Pakete:
  xfonts-100dpi | xfonts-75dpi
Die folgenden Pakete werden ENTFERNT: (following packeges are going to be REMOVED):
  ubuntu-desktop ubuntu-unity-desktop xorg xserver-xorg-core-hwe-18.04
  xserver-xorg-hwe-18.04 xserver-xorg-input-all-hwe-18.04
  xserver-xorg-input-libinput-hwe-18.04 xserver-xorg-input-wacom-hwe-18.04
  xserver-xorg-video-all-hwe-18.04 xserver-xorg-video-amdgpu-hwe-18.04
  xserver-xorg-video-ati-hwe-18.04 xserver-xorg-video-fbdev-hwe-18.04
  xserver-xorg-video-intel-hwe-18.04 xserver-xorg-video-nouveau-hwe-18.04
  xserver-xorg-video-qxl-hwe-18.04 xserver-xorg-video-radeon-hwe-18.04
  xserver-xorg-video-vesa-hwe-18.04 xserver-xorg-video-vmware-hwe-18.04
Die folgenden NEUEN Pakete werden installiert: (the following NEW packages are going to be installed):
  xserver-xorg-core
0 aktualisiert, 1 neu installiert, 18 zu entfernen und 41 nicht aktualisiert.
Es müssen 1.351 kB an Archiven heruntergeladen werden.
Nach dieser Operation werden 5.570 kB Plattenplatz freigegeben.
Möchten Sie fortfahren? [J/n]

```
I said no, I don't trust..... seems like this wants to uninstall all video support.

Any ideas how I can proceed?
Thanks a lot!!

HW: Dell XPS 13 9343 QHD Touch, i7, 8GB RAM, Intel Graphics

---

### Post by ajgreeny on 2019-04-06
Post moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2396860](https://ubuntuforums.org/showthread.php?t=2396860)

Translation of original for those like me with no German.

> Hello,

thanks for opening this thread - even if it says [SOLVED] I have some problems:
Ubuntu 18.04.2, just changed to Unity, Tap Click is not working.
Tried above procedure, but good the following message for

```
sudo apt install xserver-xorg-input-synaptics
Package lists are read ... Done
Dependency tree is set up.
Status information is read .... Done
Some packages could not be installed. That may mean that
You have requested an impossible situation or if you have the
Unstable distribution still use some required packages
have not been created or have not yet left Incoming.
The following information may help you to resolve the situation:

The following packages have unmet dependencies: (unmet dependencies):
xserver-xorg-input-synaptics: Depends on: xserver-xorg-core (> = 2: 1.18.99.901)
E: Problems can not be corrected, you have retained defective packages.
```


Trying to install xserver-xorg-core:

```
sudo apt install xserver-xorg-core
Package lists are read ... Done
Dependency tree is set up.
Status information is read .... Done
Suggested packages:
xfonts-100dpi | xfonts-75dpi
The following packages are being REMOVED: (following items are going to be REMOVED):
ubuntu-desktop ubuntu-unity-desktop xorg xserver-xorg-core-hwe-18.04
xserver-xorg-hwe-18.04 xserver-xorg-input-all-hwe-18.04
xserver-xorg-input-libinput-hwe-18.04 xserver-xorg-input-wacom-hwe-18.04
xserver-xorg-video-all-hwe-18.04 xserver-xorg-video-amdgpu-hwe-18.04
xserver-xorg-video-ati-hwe-18.04 xserver-xorg-video-fbdev-hwe-18.04
xserver-xorg-video-intel-hwe-18.04 xserver-xorg-video-nouveau-hwe-18.04
xserver-xorg-video-qxl-hwe-18.04 xserver-xorg-video-radeon-hwe-18.04
xserver-xorg-video-vesa-hwe-18.04 xserver-xorg-video-vmware-hwe-18.04
The following NEW packages will be installed: (the following NEW packages are going to be installed):
xserver-xorg-core
0 updated, 1 reinstalled, 18 removed and 41 not updated.
There are 1,351 kB of archives to download.
After this operation, 5,570 KB of disk space will be released.
Do you want to continue? [Y / n]
```

I said no, I do not trust ..... seems to like this to uninstall all video support.

Any ideas how can I proceed?
Thanks a lot!!

HW: Dell XPS 13 9343 QHD Touch, i7, 8GB RAM, Intel Graphics

---

