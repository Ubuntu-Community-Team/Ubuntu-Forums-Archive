---
title: "No motd displaying when logging into SSH"
date: 2014-01-10
forum: General Help
---

### Post by smith7 on 2014-01-10
[SIZE=2][FONT=times new roman][COLOR=#333333]I recently upgraded my box from 13.04 to 13.10. After the upgrade, I ran into some issues with motd displaying twice (specifically, */etc/motd* was being displayed after the contents of* /var/run/motd.dynamic*).
[/COLOR]
[COLOR=#333333]I found a few workarounds and tried them out, but ended up in a situation where no motd is displaying. I reverted any changes (I believe) that I made while tinkering to try and get the duplicate motd to be fixed.
[/COLOR]
[COLOR=#333333]Stuff I checked:[/COLOR]
[COLOR=#333333]/etc/pam.d/sshd has the following:[/COLOR]
```
session    optional     pam_motd.so  motd=/run/motd.dynamic noupdate
session    optional     pam_motd.so # [1]
```
[COLOR=#333333]/etc/pam.d/login has the following:[/COLOR]
```
session    optional   pam_motd.so  motd=/run/motd.dynamic noupdate
session    optional   pam_motd.so
```
[COLOR=#333333]/etc/ssh/sshd_config has these lines:[/COLOR]
```
UsePAM yes
PrintMotd no (switching this to yes has no effect)
```

[COLOR=#333333]Running```
 run-parts /etc/update/motd.d
``` returns what I expect to see.[/COLOR][/FONT][/SIZE]

---

### Post by smith7 on 2014-01-12
I found out I am stupid. I must have made the "~/.hushlogin" when I was trying to fix the double motd issue (which still happens, but such is life).

---

