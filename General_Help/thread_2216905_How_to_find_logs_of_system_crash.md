---
title: "How to find logs of system crash"
date: 2014-04-14
forum: General Help
---

### Post by silver nekode on 2014-04-14
So I have a new computer that I installed Kubuntu 13.10 on, and I seemed to have everything running well. I got into a game of minecraft and was playing for several hours, when the system randomly shut down. I saw the Kubuntu shut down splash screen before it did so it didn't lose power, it just shut down. On reboot I checked the bios and system temps all looked normal. I got back into minecraft and after just a few minutes, the system crashed to a blank black screen with a blinking cursor. I tried a quick search to see which logs to check, and the few parts I can understand don't seem to show any problem. Can someone please help me figure out which log to check to try and find what is causing the crash? Thanks in advance.

[COLOR=#000000]Specs:[/COLOR]
[COLOR=#000000]MSI H87-G43 Mobo[/COLOR]
[COLOR=#000000]Intel Core I5[/COLOR]
[COLOR=#000000]EVGA 750 ti superclocked[/COLOR]

---

### Post by baphomet2 on 2014-04-14
Did you look in /var/crash?  That should contain memory dumps taken at the moment of crash with the application name of what crashed.  Some other logs that could contain the information would be /var/log/messages, /var/log/syslog, or /var/log/rsyslog.

---

