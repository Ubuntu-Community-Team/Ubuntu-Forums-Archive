---
title: "How to complete commands during booting"
date: 2005-04-16
forum: General Help
---

### Post by DezaTur on 2005-04-16
I need to bring up interface of one LAN card during boot time. When i try to do this by using  gnome-nettool, i get error (interface eth0 doesen't exist, but it worsk fine with command "ifconfig eth0 up"). After that i need to start Firestarter, if I add Firestarter to Startup Programms I need to fill root passw, how to avoid this?

---

### Post by Slade Winstone on 2005-04-26
A quick search shows:

HOWTO: Load Firestarter (Firewall) when session starts.
[http://ubuntuforums.org/showthread.php?t=26483](http://ubuntuforums.org/showthread.php?t=26483) 

Slade.

---

### Post by Xerampelinae on 2005-04-26
[QUOTE=Slade Winstone]A quick search shows:

HOWTO: Load Firestarter (Firewall) when session starts.
[http://ubuntuforums.org/showthread.php?t=26483](http://ubuntuforums.org/showthread.php?t=26483) 

Slade.[/QUOTE]

This link describes how to run commands when you first log in to gnome.  It is good, but perhaps not what was desired in this case.

If, instead, you want to load commands when the machine boots (regardless of whether someone logs in or not), I place commands at the end of the file /etc/init.d/bootmisc.sh

I suppose this is potentially dangerous, since during an upgrade that file could change, and you'd lose your commands.  In that case one might have to worry about creating their own init script in  /etc/init.d and adding it to the appropriate run levels.  It shouldn't be hard, but I haven't tried it so I won't comment on it.

---

