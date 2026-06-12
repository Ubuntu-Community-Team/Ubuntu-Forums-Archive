---
title: "apt unmet dependencies - grub"
date: 2022-09-23
forum: General Help
---

### Post by Andrew_Fischer on 2022-09-23
This came up when doing daily updates on  22.04LTS  server:

[COLOR=#000000][FONT=Menlo]$sudo apt update ....


$ sudo apt upgrade[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Building dependency tree... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Calculating upgrade... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Some packages could not be installed. This may mean that you have[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]requested an impossible situation or if you are using the unstable[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]distribution that some required packages have not yet been created[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]or been moved out of Incoming.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]The following information may help to resolve the situation:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]The following packages have unmet dependencies:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] grub-efi-amd64-signed : Depends: grub-efi-amd64-bin (= 2.06-2ubuntu7) but 2.06-2ubuntu10 is to be installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo][COLOR=#CA3323]**E: **[/COLOR]Broken packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]


[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]$ sudo apt-cache policy grub-efi-amd64[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]grub-efi-amd64:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Installed: 2.06-2ubuntu7[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Candidate: 2.06-2ubuntu10[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  Version table:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]     2.06-2ubuntu10 500 (phased 13%)[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] *** 2.06-2ubuntu7 500[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]        100 /var/lib/dpkg/status[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]


Any suggestions?   I'm hestant to --force anything.

---

### Post by deadflowr on 2022-09-23
Simply wait.
The package is currently in phased-updates.
(your apt policy output shows that: 2.06-2ubuntu10 500 **(phased 13%)**

Basics about phased updates: [https://wiki.ubuntu.com/PhasedUpdates]("https://wiki.ubuntu.com/PhasedUpdates")

Updated information about phased updates: [https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345]("https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345")

---

