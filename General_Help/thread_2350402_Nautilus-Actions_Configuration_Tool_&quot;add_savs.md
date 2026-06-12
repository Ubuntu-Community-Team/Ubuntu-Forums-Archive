---
title: "Nautilus-Actions Configuration Tool &quot;add savscan to"
date: 2017-01-24
forum: General Help
---

### Post by liam.gutierrez on 2017-01-24
Hi,

I've installed Sophos Antivirus in my Ubuntu system and want to run the command "savscan" from the nautilus context menu. I use the tool Nautilus Actions. I managed to add the command in the context menu but nothing works once I select a file and try to run it from the context menu.

I exported my action into desktop file, maybe you see what I did wrong:


```
[Desktop Entry]Type=Action
Name[en_US]=Scan with SOPHOS
Name[en]=Scan with SOPHOS
Name[C]=Scan with SOPHOS
Tooltip[en_US]=Scan for Viruses, Malware and other "Harmware"
Tooltip[en]=Scan for Viruses, Malware and other "Harmware"
Tooltip[C]=Scan for Viruses, Malware and other "Harmware"
Icon[en_US]=/home/liam/Pictures/System Pictures/Sophos-Linux-Penguin.png
Icon[en]=/home/liam/Pictures/System Pictures/Sophos-Linux-Penguin.png
Icon[C]=/home/liam/Pictures/System Pictures/Sophos-Linux-Penguin.png
TargetToolbar=true
ToolbarLabel[en_US]=Scan with SOPHOS
ToolbarLabel[en]=Scan with SOPHOS
ToolbarLabel[C]=Scan with SOPHOS
Profiles=profile-zero;


[X-Action-Profile profile-zero]
Name[en_US]=Default profile
Name[en]=Default profile
Name[C]=Default profile
Exec=/usr/bin/savscan %B
Path=%d%f
ExecutionMode=DisplayOutput
```

---

