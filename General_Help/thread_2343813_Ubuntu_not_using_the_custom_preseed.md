---
title: "Ubuntu not using the custom preseed"
date: 2016-11-19
forum: General Help
---

### Post by reddybuss on 2016-11-19
[COLOR=#000000]I am trying to load a preseed file as a kernel argument. I forget where I saw this used as an example, but my pxelinux.cfg entry looks like this:[/COLOR]

[COLOR=#000000]Code:
       kernel /images/ubuntu-14.04.2-server-x86_64/linux
        ipappend 2
        append initrd=/images/ubuntu-14.04.2-server-x86_64/initrd.gz preseed/url=ftp://ipaddress/preseed.cfg [/COLOR]
[COLOR=#000000]
The parameter seems to be ignored, when it boots I see "successfully loaded preseed file from file:///preseed.cfg".[/COLOR]

[COLOR=#000000]Could someone help me?[/COLOR]

---

### Post by cariboo on 2016-11-19
Moved to General Help

---

