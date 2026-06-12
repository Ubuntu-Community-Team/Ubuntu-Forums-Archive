---
title: "Panel Preferences Icon Size --- goes all the way up to 200"
date: 2014-04-21
forum: General Help
---

### Post by West Swan on 2014-04-21
Hello,

I don't think this has been posted before.

I just installed the new Lubuntu 14.04 on an old Celeron Desktop.

Not sure if it matters but I'm using old ps2 mouse and keyboard.

When I try to increase the icon size in panel preferences by single clicking, the size doesn't go up by one pixel at a time.  

Instead if I click once, it goes up pixel by pixel all the way up to 200.  If I then click the down arrow once, it goes all the way down to 16 pixels.

So I'm either stuck with the 24 it starts out at (I think it was 24 anyhow) or 16 or 200.   My preferred 33 pixels cannot be achieved.

Any ideas?

Regards,

Paul

---

### Post by vasa1 on 2014-04-21
> **West Swan said:**
> ...
Instead if I click once, it goes up pixel by pixel all the way up to 200.  If I then click the down arrow once, it goes all the way down to 16 pixels.

So I'm either stuck with the 24 it starts out at (I think it was 24 anyhow) or 16 or 200.   My preferred 33 pixels cannot be achieved.
...
Until someone has a better fix, you could edit the relevant file rather than use the Panel Settings (Panel Preferences) GUI. The file that is modified by making changes the GUI way is, for me, */home/vasa1/.config/lxpanel/default/panels/panel* and its contents are:

```
[04:31 PM] ~ $ cat /home/vasa1/.config/lxpanel/default/panels/panel
# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

Global {
    edge=top
    allign=left
    margin=0
    widthtype=percent
    width=50
    height=34
    transparent=1
    tintcolor=#000006
    alpha=255
    autohide=0
    heightwhenhidden=2
    setdocktype=1
    setpartialstrut=1
    usefontcolor=1
    fontsize=10
    fontcolor=#cf6c6c
    usefontsize=0
    background=0
    backgroundfile=/usr/share/lxpanel/images/background.png
    **iconsize=33**
    loglevel=2
}

Plugin {
    type = menu
    Config {
        image=/usr/share/lubuntu/images/1404-lubuntu-logo.png
        system {
        }
        separator {
        }
        item {
            command=run
        }
        separator {
        }
        item {
            image=gnome-logout
            command=logout
        }
    }
}

Plugin {
    type = tray
}

Plugin {
    type = taskbar
    expand=1
    Config {
        tooltips=0
        IconsOnly=1
        ShowAllDesks=0
        UseMouseWheel=0
        UseUrgencyHint=1
        FlatButton=1
        MaxTaskWidth=200
        spacing=1
        GroupedTasks=0
    }
}

Plugin {
    type = cpu
}

[04:32 PM] ~ $ 
```
**After making a backup for safety**, modify the **iconsize** value using a plain text editor. Then, from a terminal, run
```
pkill lxpanel
lxpanel & exit
```

---

### Post by West Swan on 2014-04-21
awesome thank you.

---

### Post by bapoumba on 2014-04-21
I cannot reproduce, clicking on the arrow either way increases or decreases the icons by 2 px at a time. The file is /home/bapoumba_lxde/.config/lxpanel/Lubuntu/panels/panel here, and iconsize=24 this should be the default).

What is you panel height ? 24 here.

---

### Post by West Swan on 2014-08-19
Hello, 

Sorry I was away for some time.

I actually fixed the issue by uses my mouse to highlight the value in panel preferences and then typing in the number 33.

It bypassed using the arrows altogether.

Cheers,

Paul

---

