---
title: "Unable to remove or install applications from the Ubuntu Software App"
date: 2022-05-30
forum: General Help
---

### Post by masteryoyogi on 2022-05-30
Hello all, just got into the world of Ubuntu. I'm only experiencing one issue for now, if I open the Ubuntu Software app and try to remove (or add) an app, I get the following message: 

**"Unable to remove "Name of Application": no packages to remove"**

However, the application is still installed, I'm able to open it and everything. This happens with every application on the installed panel. 

So far I've tried the following:

[LIST]
[*]Ran **"snap changes":** all status is at **Done** except for the following **Errors**:
*3    Error   yesterday at 20:21 EST     yesterday at 20:22 EST  Auto-refresh 4 snaps*
*4    Done    today at 00:46 EST         today at 00:46 EST      Auto-refresh snap "firefox"*
[*][FONT=var(--ff-mono)]Ran killall snap-store[/FONT]
[*][FONT=var(--ff-mono)]Ran [/FONT]sudo snap refresh snap-store
[*]Ran sudo snap remove snap-store && sudo snap install snap-store
[/LIST]

None of the above works. I still get the same error. 

Also, if I try to install an application that's **.snap**, I get the following error in Ubuntu Store: "Failed to install file: not supported".

Thanks!

**Current OS:** Ubuntu 22.04 LTS | GNOME version 42.1 | Windowing System: Wayland.

---

### Post by TheFu on 2022-05-30
Is it all of Linux you are new to or just Ubuntu?
[LIST]
[*]Which release of Ubuntu?   **lsb_release -d** will answer this.
[*]Which DE?   I don't recall off the top of my head how to get this. I don't use any DE. Gnome, KDE, LXQt, Mate are typical answers.
[/LIST]


To see the list of installed snaps, use **snap list**.  Snaps are not the main way that software is installed on any Linux, including Ubuntu.  APT (the package management system) is the way.

BTW, I've never used the "Ubuntu Store", so it this issue is about that and you aren't just looking for a solution, but want the Ubuntu Store answer, ignore me.
There are a number of different TUI/GUI interfaces to APT.  Synaptic is the long-time GUI version that deals with normal packages and dependency resolution.

---

### Post by masteryoyogi on 2022-05-30
> **TheFu said:**
> Is it all of Linux you are new to or just Ubuntu?
[LIST]
[*]Which release of Ubuntu?   **lsb_release -d** will answer this.
[*]Which DE?   I don't recall off the top of my head how to get this. I don't use any DE. Gnome, KDE, LXQt, Mate are typical answers.
[/LIST]


To see the list of installed snaps, use **snap list**.  Snaps are not the main way that software is installed on any Linux, including Ubuntu.  APT (the package management system) is the way.

BTW, I've never used the "Ubuntu Store", so it this issue is about that and you aren't just looking for a solution, but want the Ubuntu Store answer, ignore me.
There are a number of different TUI/GUI interfaces to APT.  Synaptic is the long-time GUI version that deals with normal packages and dependency resolution.

Hey there, thanks for the reply!

I'm actually completely new to Ubuntu, so please forgive my ignorance. I'm currently using Ubuntu 22.04 LTS | GNOME version 42.1 | Windowing System: Wayland. Thanks for reminding me, I'll update the post with my version of Ubuntu.

I don't mind using something other than the Ubuntu Store, but can I install .snap applications without it? 

I'm trying to install an application called obsidian ([https://obsidian.md/](https://obsidian.md/)) they offer .snap, .AppImage, and FlatPak. 

I could use an AppImage but it doesn't install in the list of Applications so I can put it my favorites for quick access. Is there a way I can put .AppImage applications in my app list?

Thanks again!

---

### Post by agentl074 on 2022-05-30
What I did to resolve this was to run the following commands:



sudo apt update && sudo apt upgrade -y



It also fixed the category listing problem -- it still take a minute to populate for the first time, but at least it does it :)

So too, if you have a stubborn app that you need to remove, you may use 



sudo apt remove appnamehere

---

### Post by masteryoyogi on 2022-05-30
> **agentl074 said:**
> What I did to resolve this was to run the following commands:



sudo apt update && sudo apt upgrade -y


It also fixed the category listing problem -- it still take a minute to populate for the first time, but at least it does it :)

Thanks for the suggestion Agent! I tried that, but unfortunately no luck yet, still getting the same error. I wonder what's going on :(

---

### Post by TheFu on 2022-05-30
```
sudo snap install obsidian
```

But I don't see that snap package as available.  I guess you can download it ---- say it is named obsidian.snap, then to install it, your terminal would need to be in the same directory and you'd run
```
sudo snap install ./obsidian.snap
```
the last part of that command is the relative or complete path to the snap-package file, so there are many different answers for that which will work.

Are you familiar with Linux or not?

---

### Post by masteryoyogi on 2022-05-30
> **TheFu said:**
> ```
sudo snap install obsidian
```

But I don't see that snap package as available.  I guess you can download it ---- say it is named obsidian.snap, then to install it, your terminal would need to be in the same directory and you'd run
```
sudo snap install ./obsidian.snap
```
the last part of that command is the relative or complete path to the snap-package file, so there are many different answers for that which will work.

Are you familiar with Linux or not?

I'm not familiar with Linux. I know a few terminal commands, but I'm learning. Trying to use it as my main OS. 

Btw, I tried ```
sudo snap install ./[COLOR=#000000][FONT=&quot]obsidian_0.14.6_amd64[/FONT][/COLOR]
``` and got the following error:

```
error: cannot find signatures with metadata for snap       "./obsidian_0.14.6_amd64.snap"
```

---

### Post by TheFu on 2022-05-30
[https://forum.obsidian.md/t/how-to-install-obsidian-snap-on-ubuntu/2515](https://forum.obsidian.md/t/how-to-install-obsidian-snap-on-ubuntu/2515) seems to address this problem. Looks like they have a bad package build.

---

### Post by #&amp;thj^% on 2022-05-30
***Read with caution that error is so unhelpful, I have no idea why they haven't fixed it.
You can get past it though with:
```
sudo snap install --dangerous <snap>
```
use the proper name in place of <snap>
**_But I don't recommend that. Unless for testing only...._**
If you want it's available in flatpak:
```
flatpak search obsidian
Name          Description         Application ID          Version Branch Remotes
Obsidian      Markdown-based kno\u2026 md.obsidian.Obsidian    0.14.6  stable flathub
Obsidian-2 G\u2026 Obsidian-2 theme    \u2026k.Gtk3theme.Obsidian-2 2.20    3.22   flathub
Obsidian-2-T\u2026 Obsidian-2-Teal th\u2026 \u20263theme.Obsidian-2-Teal 2.20    3.22   flathub
Obsidian-2-R\u2026 Obsidian-2-Red the\u2026 \u2026k3theme.Obsidian-2-Red 2.20    3.22   flathub
Obsidian-2-P\u2026 Obsidian-2-Purple \u2026 \u2026heme.Obsidian-2-Purple 2.20    3.22   flathub
Obsidian-2-M\u2026 Obsidian-2-Mint th\u2026 \u20263theme.Obsidian-2-Mint 2.20    3.22   flathub
Obsidian-2-I\u2026 Obsidian-2-Indigo \u2026 \u2026heme.Obsidian-2-Indigo 2.20    3.22   flathub
Obsidian-2-G\u2026 Obsidian-2-Green t\u2026 \u2026theme.Obsidian-2-Green 2.20    3.22   flathub
Obsidian-2-G\u2026 Obsidian-2-Gray th\u2026 \u20263theme.Obsidian-2-Gray 2.20    3.22   flathub
Obsidian-2-A\u2026 Obsidian-2-Aqua th\u2026 \u20263theme.Obsidian-2-Aqua 2.20    3.22   flathub
Obsidian-2-A\u2026 Obsidian-2-Amber t\u2026 \u2026theme.Obsidian-2-Amber 2.20    3.22   flath
```

---

### Post by masteryoyogi on 2022-05-30
Thanks @1fallen and @TheFu. Very helpful! The flatpak solution worked perfectly, got the app running finally! A great day to both!

---

