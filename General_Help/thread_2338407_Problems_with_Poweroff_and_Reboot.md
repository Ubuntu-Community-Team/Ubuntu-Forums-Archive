---
title: "Problems with Poweroff and Reboot"
date: 2016-09-28
forum: General Help
---

### Post by lolipop-uncaramelito on 2016-09-28
[SIZE=2][FONT=arial]Hellow, sorry for my english. 


[/FONT][/SIZE][COLOR=#212121][FONT=arial][FONT=arial]When joining the terminal poweroff or reboot get the following message:

[/FONT][/FONT][/COLOR][HTML]User root is logged in on ???.[/CODE][CODE]
Please retry operation after closing inhibitors and logging out other users.
Alternatively, ignore inhibitors and users with 'systemctl poweroff -i'.[/HTML]

[HTML]lolito@loli-pc:~$ who
lolito   tty7         2016-09-27 21:07 (:0)[/HTML]

[HTML]lolito@loli-pc:~$ systemd-inhibit --list     
Who: lolito (UID 1001/lolito, PID 1471/unity-settings-) 
What: sleep     Why: GNOME needs to lock the screen    
Why: GNOME needs to lock the screen
Mode: delay 

Who: lolito (UID 1001/lolito, PID 1471/unity-settings-)
What: handle-power-key:handle-suspend-key:handle-hibernate-key
Why: GNOME handling keypresses
Mode: block

Who: NetworkManager (UID 0/root, PID 1017/NetworkManager)
What: sleep
Why: NetworkManager necesita apagar redes
Mode: delay[/HTML]

The version is Ubuntu 16.04 LTS x64

Thanks you for reading.

---

