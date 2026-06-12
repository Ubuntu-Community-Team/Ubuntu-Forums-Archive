---
title: "WiFi Hotspot doesn't work and Airplane mode always ON after boot"
date: 2018-07-10
forum: General Help
---

### Post by deepamar on 2018-07-10
[COLOR=#000000][FONT=Arial]I have tried all the methods I have found so far.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]I had also followed a procedure given in this link: [https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]My network adaptor is "Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)"[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Problems are:-[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial] - Only WiFi and ethernet are working.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] - I can switch ON the hotspot and Bluetooth but it is not visible on any phone or laptop.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] - Airplane mode is always ON after boot.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] - Airplane mode and Bluetooth keep alternately switching, when I switch one OFF the other one is turned ON automatically.[/FONT][/COLOR]


[COLOR=#000000][FONT=Arial]The commands that I have tried are:-[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial] sudo lspci -nn -d 14e4:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo apt-get purge bcmwl-kernel-source[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo apt update[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo update-pciids[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo apt install bcmwl-kernel-source[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo reboot[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]Then I tried [/FONT][/COLOR]```
[COLOR=#000000][FONT=Arial]sudo rfkill unblock all[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial]I have also tried ( as said in the above link):-[/FONT][/COLOR]
```

[COLOR=#000000][FONT=Arial] sudo apt-get purge bcmwl-kernel-source[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo apt update[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo update-pciids[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo apt install firmware-b43-installer[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo modprobe -r b43[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo modprobe b43[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo rfkill unblock all[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial] sudo reboot
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Please help me, I have installed ubuntu 17.10 and upgraded to 18.04, and both have the same problem.[/FONT][/COLOR]

---

