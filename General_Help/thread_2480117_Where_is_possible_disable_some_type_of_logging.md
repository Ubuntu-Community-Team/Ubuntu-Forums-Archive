---
title: "Where is possible disable some type of logging ?"
date: 2022-10-19
forum: General Help
---

### Post by aug7744 on 2022-10-19
Hello.
I have installed Gnome Control Center and have options about :

- Connectivity Checking ( connection issues keep online ) .
- Location services .
- File history .

How disable the features above using command line or editing configuration files ?

Thanks for reading.
I wish an nice day for you.

---

### Post by &amp;KyT$0P# on 2022-10-19
Those are stored in the dconf database.  To change them by command line, you first need to install [FONT=Courier New]dconf-cli[/FONT] if you don't already have it -
```
sudo apt-get install dconf-cli
```
then you should be able to set them with a [FONT=Courier New]dconf[/FONT] command (refer to [FONT=Courier New]man dconf[/FONT] for details).

You might also be able to change them with a [FONT=Courier New]gsettings set ...[/FONT] command (refer to [FONT=Courier New]man gsettings[/FONT] for details on that).

I don't recall what are the exact settings for those, but you should be able to find out using [FONT=Courier New]dconf-editor[/FONT]

* I couldn't find the setting for connectivity check in a quick look, but
 - Location services is [FONT=Courier New]org.gnome.system.location.enabled[/FONT]
 - File history is [FONT=Courier New]org.gnome.desktop.privacy.remember-recent-files[/FONT]

** I remembered wrong about connectivity checking.  To disable that one, add the following lines to [FONT=Courier New]/etc/NetworkManager/NetworkManager.conf[/FONT] -
```
[connectivity]
enabled=false
interval=0
```

Then run [FONT=Courier New]sudo systemctl restart NetworkManager[/FONT] to apply the change.

Note that this may make the state of the GNOME Control Center switch inconsistent with the actual state of the setting: this will override the way the switch would make that setting.

---

### Post by grahammechanical on 2022-10-19
Users of Ubuntu 20.04 can do this through System Settings>Privacy. I think that you are using Lubuntu and I have been trying to find a way of changing privacy options in the Lubuntu Manuel. And I have failed.

[https://manual.lubuntu.me/stable/](https://manual.lubuntu.me/stable/)

Regards

---

