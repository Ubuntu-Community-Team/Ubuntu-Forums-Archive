---
title: "Suspend and power off are not reliable - Ubuntu 18.04.01 on Lenovo G70-80"
date: 2019-01-30
forum: General Help
---

### Post by lau-5-jgbrown on 2019-01-30
[COLOR=#000000][FONT=Arial]I am experiencing problems with suspend and power-off after upgrading from Ubuntu 16.04 LTS to Ubuntu 18.04.01 LTS.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have tried multiple fixes, including:[/FONT][/COLOR]


[LIST]
[*][COLOR=#000000][FONT=Arial]Installing **pm-utils**[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Testing several kernels: **4.14.96, 4.17.19, 4.19.18, 4.20.5**[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Adding the parameters **acpi_osi=! "acpi_osi=Windows 2015" ** to the default **linux** command line in **/etc/default/grub**[/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial]In all cases, suspend and power off will work sporadically, but are not reliable.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I am hoping that someone with a Lenovo machine can advise me of a fix that has been reliable.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Details of my configuration are available:[/FONT][/COLOR]


[LIST]
[*][[COLOR=#000000][FONT=Arial]inxi output[/FONT][/COLOR]]("https://pastebin.com/j6BYc9aj")
[*][[COLOR=#000000][FONT=Arial]/boot/grub/grub.cfg[/FONT][/COLOR]]("https://pastebin.com/2Edhxn1t")
[/LIST]


[COLOR=#000000][FONT=Arial]Thanks for your help.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]JGB[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

