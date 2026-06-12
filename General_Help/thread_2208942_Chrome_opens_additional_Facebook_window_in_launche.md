---
title: "Chrome opens additional Facebook window in launcher"
date: 2014-03-03
forum: General Help
---

### Post by chaushev on 2014-03-03
Using Ubuntu 13.10 x64 unity. I started my laptop today and here is what I noticed. Any idea how to get rid of that darn facebook. I dont want to use any wep apps, integrated facebooks, yahoos or whatever.
[ATTACH=CONFIG]250831[/ATTACH]

---

### Post by chaushev on 2014-03-04
Solved it. I ran this in terminal. Logged out and back in - all done!
```
[FONT=Ubuntu Mono]rm $HOME/.local/share/applications/google-chrome-*.desktop[/FONT][COLOR=#333333][FONT=UbuntuRegular]
```
From then on, Unity launcher won't create a second icon when you open Chrome.[/FONT][/COLOR]

---

