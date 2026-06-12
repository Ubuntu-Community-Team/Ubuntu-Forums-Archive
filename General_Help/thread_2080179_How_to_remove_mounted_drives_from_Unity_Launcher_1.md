---
title: "How to remove mounted drives from Unity Launcher 12.10"
date: 2012-11-03
forum: General Help
---

### Post by apollothethird on 2012-11-03
Can someone tell me how to remove the mounted drives from the Unity Launcher.  The clutter is distracting.  It's not necessary since the drives already are accessible via Nautilus.

I've already performed extensive searches that doesn't appear to work with Ubuntu 12.10.

I tried 
```

gconftool --set /apps/compiz-1/plugins/unityshell/screen0/options/devices_option  --type=int 0

```

It doesn't give an error message.  However, the drives stay on the Unity launcher.

I also went to the myunity home page ([https://apps.ubuntu.com/cat/applications/precise/myunity/](https://apps.ubuntu.com/cat/applications/precise/myunity/)).  The application was removed from the repository.

Thanks in advance for any assistance.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by hal8000 on 2012-11-03
Its easier than you think.
Right click on each drive icon on the unity launcher and click unlock from launcher.

---

### Post by apollothethird on 2012-11-03
> **hal8000 said:**
> Its easier than you think.
Right click on each drive icon on the unity launcher and click unlock from launcher.

Great!

Thanks!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by #1udancqSHv% on 2013-01-03
Hi all, apologies to apollothethird and mods for thread-hijacking and resurrecting an oldish thread, but I think this is relevant.

Following hal8000's advice does work, but temporarily - as soon as I run gparted, there they all are again.

I've got a load of test partitions for other distros, and I really don't want to see them all in the launcher.

Any ideas for a more permanent solution?

apollothethird - have you encountered the same issue after running gparted?

Thanks everyone!

---

### Post by scouser73 on 2013-01-03
You'll need to install Gnome Tweak Tool.

[https://apps.ubuntu.com/cat/applications/gnome-tweak-tool/]("https://apps.ubuntu.com/cat/applications/gnome-tweak-tool/")

Once you have installed it, go to the Unity Dash and type **Advanced Settings**

Where it says; **Show Mounted Volumes On The Desktop** make sure it's set to **Off**

---

### Post by mc4man on 2013-01-03
> **jfj33 said:**
> Hi all, apologies to apollothethird and mods for thread-hijacking and resurrecting an oldish thread, but I think this is relevant.

Following hal8000's advice does work, but temporarily - as soon as I run gparted, there they all are again.

I've got a load of test partitions for other distros, and I really don't want to see them all in the launcher.

Any ideas for a more permanent solution?

apollothethird - have you encountered the same issue after running gparted?

Thanks everyone!

current & 'unattended bug'
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1060484](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1060484)

---

### Post by #1udancqSHv% on 2013-01-07
> **scouser73 said:**
> You'll need to install Gnome Tweak Tool.

[https://apps.ubuntu.com/cat/applications/gnome-tweak-tool/](https://apps.ubuntu.com/cat/applications/gnome-tweak-tool/)

Once you have installed it, go to the Unity Dash and type **Advanced Settings**

Where it says; **Show Mounted Volumes On The Desktop** make sure it's set to **Off**
Thanks for helping out a woolyback, Scouser73, but the gnome-tweak-tool doesn't stop the mounted drives reappearing after running gparted. It's very useful though, cheers for the tip! ;)

> **mc4man said:**
> current & 'unattended bug'
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1060484](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1060484)
Aha! That's the one. Have added my report. Thanks mc4man

---

