---
title: "[Question] Help Please. Kubuntu 20.04 NO GUI - Boot stuck at &quot;Finished update UTMP ab"
date: 2020-09-25
forum: General Help
---

### Post by sincegutsy on 2020-09-25
[COLOR=#878A8C][FONT=IBMPlexSans][COLOR=#1A1A1B][FONT=&amp]Hi all, another support request here. This is a fairly new clean install that was working fine for about 10 days. No known changes. I noticed that a few of my panels had disappeared and my desktop images where not updating on 1 of 3 monitors. So I decided to reboot. On reboot (I run without quiet splash) the system sticks at "Finished update UTMP about system runlevel changes ".
No login screen and no GUI. I have searched www and reviewed other similar issues which none appear to be my same problem. No chron jobs running, NVIDIA driver seems to be active and recognized (PNY K1200). I did get a motherboard beep code and noticed my integrated graphics had been reactivated (I set as disabled in BIOS). I reset that and rebooted again - same issue.


I am able to ssh to the box and to get to a text console. I have posted relevant logs at the URL's below. If there is a better place for quick anonymous file share let me know. I could not get attachments to work here. 
[COLOR=#1A1A1B][FONT=&amp][http://www.filedropper.com/syslog](http://www.filedropper.com/syslog)
[/FONT][/COLOR][COLOR=#1A1A1B][FONT=&amp][http://www.filedropper.com/bootlog](http://www.filedropper.com/bootlog)[/FONT][/COLOR][COLOR=#1A1A1B][FONT=&amp][URL="http://www.filedropper.com/xorg0"]
http://www.filedropper.com/xorg0[/URL]
[/FONT][/COLOR]I don't want to do a system recovery on this unless it is absolutely necessary. Anyone with relevant knowledge or has resolved a similar issue would be MUCH appreciated. I had just about gotten this system working and configured exactly the way I wanted.
[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by TheFu on 2020-09-25
Sounds like the GPU is failing or just needs to be reseated or has a bad power connection. A flaky PSU can cause this type of behavior.

---

