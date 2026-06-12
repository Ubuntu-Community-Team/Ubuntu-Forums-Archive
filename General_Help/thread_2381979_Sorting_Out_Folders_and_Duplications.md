---
title: "Sorting Out Folders and Duplications"
date: 2018-01-07
forum: General Help
---

### Post by brakecane on 2018-01-07
[COLOR=#000000]Browsing around on this laptop I see I have[/COLOR]
[COLOR=#000000]/tom[/COLOR]
[COLOR=#000000]and I have [/COLOR]
[COLOR=#000000]/home/tom (the older folder?)[/COLOR]

[COLOR=#000000]I am now booted into the older install, Debian GNU/Linux 7, and I see that "Places / Home" brings me to "/home/tom". So I guess that is the older of the two.[/COLOR]

[COLOR=#000000]I've been through a few installs on this laptop. I'm currently in the process of repairing the Grub. That means I'm currently booted into the old install, in here I see there is a difference between the files in [/COLOR]
[COLOR=#000000]/tom/Documents/Artisans.Asylum[/COLOR]
[COLOR=#000000]as opposed to [/COLOR]
[COLOR=#000000]/home/tom/Documents/Artisans.Asylum (apparently, the older version)[/COLOR]

[COLOR=#000000]I once had only one partition (maybe two?)[/COLOR]
[COLOR=#000000]Later I correctly partitioned the HD with Root, Home, and Swap[/COLOR]

[COLOR=#000000]This seems to be the older folder because it has less in it[/COLOR]
[COLOR=#000000]/home/tom/Documents/Artisans.Asylum[/COLOR]

[COLOR=#000000]With this being the newer[/COLOR]
[COLOR=#000000]/tom/Documents/Artisans.Asylum[/COLOR]
[COLOR=#000000]The "modified" dates tell me that is correct.[/COLOR]

[COLOR=#000000]How can I safely combine[/COLOR]
[COLOR=#000000]/tom/Documents/[/COLOR]
[COLOR=#000000]and[/COLOR]
[COLOR=#000000]/home/tom/Documents/[/COLOR]
[COLOR=#000000]without overwriting newer files[/COLOR]

---

### Post by TheFu on 2018-01-07
rsync.

---

