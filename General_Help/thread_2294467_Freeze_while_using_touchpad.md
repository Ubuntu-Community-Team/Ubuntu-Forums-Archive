---
title: "Freeze while using touchpad"
date: 2015-09-11
forum: General Help
---

### Post by kechuck on 2015-09-11
[COLOR=#111111][FONT=Ubuntu]There is a small [/FONT][/COLOR][bug]("https://bugs.launchpad.net/xorg-server/+bug/1220426/")[COLOR=#111111][FONT=Ubuntu] that affects me. It already solved and fix released, but updated package accessible only for [/FONT][/COLOR]*vivid*[COLOR=#111111][FONT=Ubuntu] and higher.

[/FONT][/COLOR]
[LIST=1]
[*]I do not know what I must to do to apply this to *trusty*?
[*]Must I do it before or after *nvidia-355* and *nvidia-prime* installation?
[/LIST]
[COLOR=#111111][FONT=Ubuntu]
Currently I have no drivers installed.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]By default, to do this I use following commands:

[/FONT][/COLOR]
[LIST=1]
[*]Add repository: ```
[COLOR=#111111][FONT=Ubuntu]sudo add-apt-repository ppa:x[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]org-edgers/ppa[/FONT][/COLOR]
```
[*]Update package DB: ```
[COLOR=#111111][FONT=Ubuntu]sudo apt-get update[/FONT][/COLOR]
```
[*]Install nvidia-prime and nvidia drivers: ```
[COLOR=#111111][FONT=Ubuntu]sudo apt-get install nvidia-355 nvidia-prime[/FONT][/COLOR]
```
[/LIST]

[COLOR=#111111][FONT=Ubuntu]P.S.: I'm using Ubuntu Trusty x86-64 with kernel 3.13.0-63-generic.[/FONT][/COLOR]

---

