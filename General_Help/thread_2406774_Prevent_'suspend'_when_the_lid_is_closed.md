---
title: "Prevent 'suspend' when the lid is closed"
date: 2018-11-25
forum: General Help
---

### Post by susja on 2018-11-25
Hello,
I have an issue with 18.04 when close the lid of my laptop.
I did not have it with 16.04.
[COLOR=#000000][FONT=Verdana]*I've changed file /etc/systemd/logind.conf and uncomment the line*[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]*HandleLidSwitch=ignore*[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][I]But still ... when the lid is open I have no problem to connect and with closed lid I failed.
Then I did this in a file[/I][/FONT][/COLOR]/etc/UPower/UPower.conf
IgnoreLid=true
Last step I did was this:
[FONT=&quot]gsettings set org.gnome.settings-daemon.plugins.power lid-close-ac-action 'nothing'[/FONT]
But I still have the issue i.e. loosing Wi-Fi connection to this laptop when the lid is closed.
Note: as soon as I open the lid ... connection get restored .
Any other suggestion?

Thanks

---

### Post by susja on 2018-11-27
Bump

---

### Post by susja on 2018-11-28
Hey Folks,
Any suggestions?

Thanks

---

