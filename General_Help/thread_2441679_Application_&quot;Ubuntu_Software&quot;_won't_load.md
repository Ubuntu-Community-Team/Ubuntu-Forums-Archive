---
title: "Application &quot;Ubuntu Software&quot; won't load properly anymore"
date: 2020-04-25
forum: General Help
---

### Post by nor-wanderer on 2020-04-25
I have a clean installation of Ubuntu 20.04, and Ubuntu Software worked fine.

I've now changed some confirmation, and installed various applications through the terminal. Just happend to realized the Ubuntu Software icon looked weird, and upon trying the open the app, only parts of the app will display, with a transparent backgroun.

Not sure what caused it, or what I can do to try to fix it? Any advise?

Icon:
[ATTACH=CONFIG]285616[/ATTACH]

Screenshots after clicking to open "Ubuntu Software":
[ATTACH=CONFIG]285614[/ATTACH]
[ATTACH=CONFIG]285615[/ATTACH]

---

### Post by nor-wanderer on 2020-04-25
Here are some brief descriptions of what I have done after the installation:
[LIST=1]
[*]Installed Tweak Tool (gnome-tweak-tool, gnome-shell-extensions, chrome-gnome-shell)
[*]Enabled Extentions and Users themes to install the Ultimate Maia theme and icons
[*]Changed login screen background using these instructions: [https://github.com/PRATAP-KUMAR/focal_gdm3_complete_hack](https://github.com/PRATAP-KUMAR/focal_gdm3_complete_hack)
[/LIST]

---

### Post by Dennis N on 2020-04-25
> upon trying the open the app, only parts of the app will display, with a transparent background. Not sure what caused it, or what I can do to try to fix it? Any advise?

It's happened to others. See this thread for a solution:
[Ubuntu Software Application]("https://ubuntuforums.org/showthread.php?t=2440700")

---

### Post by nor-wanderer on 2020-04-25
Thanks. These two commands in the terminal solved it for me too (although it doesn't look quite like it used to...)
```
snap remove snap-store
sudo apt install ubuntu-software

```

---

### Post by CelticWarrior on 2020-04-25
> **nor-wanderer said:**
> Thanks. These two commands in the terminal solved it for me too (although it doesn't look quite like it used to...)
```
snap remove snap-store
sudo apt install ubuntu-software

```

Not really a solution. It removed the default store and installed the older one.
The problem is the theme you applied, that's all.

---

### Post by nor-wanderer on 2020-04-28
> **CelticWarrior said:**
> Not really a solution. It removed the default store and installed the older one.
The problem is the theme you applied, that's all.

I have the same Theme installed on an older laptop with Ubuntu 18.04 and don't experience that issue there.

Is there any changes I can make to the theme instead. If so what should I look for in what file?
In addition, is there any way to get the old store back, because the new one looks quite different...

---

### Post by CelticWarrior on 2020-04-28
> **nor-wanderer said:**
> I have the same Theme installed on an older laptop with Ubuntu 18.04 and don't experience that issue there.

The theme hasn't been optimized to the new release. It's not the only one that worked until now but has issues with 20.04.

---

### Post by nor-wanderer on 2020-04-29
> **CelticWarrior said:**
> The theme hasn't been optimized to the new release. It's not the only one that worked until now but has issues with 20.04.

Thanks. That makes sense. Any idea how I can get my old store back then?

---

