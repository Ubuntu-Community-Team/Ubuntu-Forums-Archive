---
title: "Help with loop script and autostart."
date: 2016-10-29
forum: General Help
---

### Post by CantankRus on 2016-10-29
I use nemo as my file browser in 16.04.
If you show hidden files, this setting is retained when you close and open nemo again.
I wanted nemo to always open not showing hidden so I wrote this loop script and
added it to startup applications.

**show_hidden_false-loop.sh**
```
#!/bin/bash

while true; do
	if pidof nemo
		then
			echo "nemo is running"
		else
			echo "nemo is not running... show hidden set to false"
			dconf write /org/nemo/preferences/show-hidden-files false
	fi
 sleep 5
done
exit 0
```
Problem is, when I logout and back in it continues to run and another instance is spawned.
I thought this would automatically be killed when I logged out.
[ATTACH=CONFIG]271861[/ATTACH]

Is there something I'm missing or do I need to check for a running instance in the script?

---

### Post by CantankRus on 2016-10-30
Found the solution.
Seems to be a setting of systemd logind.conf.
```
sudoedit /etc/systemd/logind.conf
```

Change
```
#KillUserProcesses=no
```

to
```
KillUserProcesses=yes
```
Reboot.

Credit to: [https://bbs.archlinux.org/viewtopic.php?pid=1520751#p1520751](https://bbs.archlinux.org/viewtopic.php?pid=1520751#p1520751)

---

