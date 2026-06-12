---
title: "gnome-terminal -t &quot;name&quot; not working with 3.16.2"
date: 2016-05-04
forum: General Help
---

### Post by AllenE on 2016-05-04
So I found a few forum posts with people complaining that they lost the ability to name/title a terminal tab following an upgrade to 3.16.2. What really stinks is that the -t is still listed in the man page. Anyways, does anyone know if this was added back or corrected with a newer release of gnome-terminal? If so, I tried upgrading and received the following message....

ecka00@p17835:~$ gnome-terminal --version
GNOME Terminal 3.16.2
ecka00@p17835:~$ man gnome-terminal
ecka00@p17835:~$ sudo apt-get install --only-upgrade gnome-terminal
[sudo] password for ecka00: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-terminal is already the newest version.

---

### Post by sudodus on 2016-05-04
Welcome to the Ubuntu Forums :-)

There are other terminal window programs, for example xterm, sakura, tilda, terminator. Try them and keep the one you like the best. If you want to use command line options, the grand old xterm is a good choice:

Examples:

```

xterm -fa default -fs 32 -fg yellow -bg blue -geometry 32x3 -title '24-h clock' -e bash -c 'echo " ";echo " ";while true; do echo -en "\0033[A ";date;sleep 1;done'

xterm -fa default -fs 10 -geometry 32x1 -fg black -bg '#ebeceb' -e bash -c 'echo -en "  24-h clock;quit with ctrl c";while true; do winttl=$(date "+%H:%M:%S");sleep 1;echo -en "\0033]0;$winttl\0007";done'

```

---

