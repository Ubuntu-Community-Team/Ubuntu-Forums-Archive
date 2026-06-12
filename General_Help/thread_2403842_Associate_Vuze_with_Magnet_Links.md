---
title: "Associate Vuze with Magnet Links"
date: 2018-10-17
forum: General Help
---

### Post by wsmith1018 on 2018-10-17
Hello,

I am trying to associate Vuze with magnet links, and using the directions [here]("https://wiki.vuze.com/w/Magnet#Ubuntu.2FKubuntu"), but it doesn't seem to work.

System Details:
[LIST]
[*]Ubuntu 18.04.1
[*]Vuze 5.7.6.0
[*]Firefox 62.0.3
[/LIST]

I created the file: /usr/share/applications/vuze.desktop

Contents:
```
[Desktop Entry]Categories=Java;Network;FileTransfer;P2P
Commenten_US=Multimedia Bittorrent Client
Comment=Multimedia Bittorrent Client
Encoding=UTF-8
Exec=vuze "%U"
GenericNameen_US=Multimedia Bittorrent Client
GenericName=Multimedia Bittorrent Client
Icon=vuze.png
MimeType=x-scheme-handler/magnet;application/x-bittorrent;
Nameen_US=Vuze
Name=Vuze
Path=/snap/vuze-vs/3/opt/vuze/
StartupNotify=true
StartupWMClass=Vuze
Terminal=false
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=
X-KDE-SubstituteUID=false
X-KDE-Username=
```


I created  this file: /usr/bin/vuze

With Contents of:
```
#!/bin/bash

cd /snap/vuze-vs/3/opt/vuze/


./vuze "$@"
```

I ran: chmod +x /usr/bin/vuze

Then I ran the following commands:
gconftool-2 -t string -s /desktop/gnome/url-handlers/magnet/command "/snap/vuze-vs/3/opt/vuze/vuze %U"
gconftool-2 -s /desktop/gnome/url-handlers/magnet/needs_terminal false -t bool
gconftool-2 -t bool -s /desktop/gnome/url-handlers/magnet/enabled true

When I click on a magnet link, Firefox opens a dialog asking me to choose a file to open a link. I've tried the options listed in the prompt, but neither work.

Can anyone explain what I'm doing wrong or missing? Thanks!

---

### Post by wsmith1018 on 2018-10-19
Friendly bump...

---

### Post by wsmith1018 on 2018-10-24
Does anyone have any suggestions? I've tried many solutions found Googling the issue, but they haven't worked. Thanks!

---

### Post by wsmith1018 on 2018-10-28
Another friendly bump...

---

### Post by nlee2 on 2018-10-29
Try to run the commands in your /usr/bin/vuze script in a terminal and see if there are any messages that might help.

I did this and discovered that java was not installed. After installing java, I encounter the following 

```
You seem to have set an invalid PROGRAM_DIR, unable to continue!
```

The snap folder is read only so I applied my fix to a copy

```
cp /snap/vuze-vs/3/opt/vuze/vuze /usr/local/bin/myvuze

change line #6 from
PROGRAM_DIR="$SNAP/opt/vuze/"    # use full path to Azureus bin dir
to
PROGRAM_DIR="/snap/vuze-vs/3/opt/vuze/" # use full path to Azureus bin dir
```

Finally change your /usr/bin/vuze script to run myvuze as root.

---

