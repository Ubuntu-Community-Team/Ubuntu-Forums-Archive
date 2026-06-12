---
title: "two network icons, how do I fix?"
date: 2019-06-13
forum: General Help
---

### Post by ardouronerous on 2019-06-13
I'm running Lubuntu 18.04.
[ATTACH=CONFIG]283426[/ATTACH]
I have two network icons appearing, how do I fix this?

Thanks.

---

### Post by Xian on 2019-06-13
A couple of ideas :

1. If you have ~/.config/lxpanel/Lubuntu/panels/panel
set network=1

2. In the settings panel remove the Status Notifier Plugin
See then if only 1 icon remais

---

### Post by ardouronerous on 2019-06-13
```
# lxpanel <profile> config file. Manually editing is not recommended.
# Use preference dialog in lxpanel to adjust config when you can.

Global {
  edge=bottom
  allign=left
  margin=0
  widthtype=percent
  width=100
  height=24
  transparent=0
  tintcolor=#000000
  alpha=0
  setdocktype=1
  setpartialstrut=1
  usefontcolor=0
  fontcolor=#000000
  background=0
  backgroundfile=/usr/share/lxpanel/images/lubuntu-background.png
  iconsize=24
}
Plugin {
  type=menu
  Config {
    image=/usr/share/lubuntu/images/lubuntu-logo.png
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
  type=launchtaskbar
  Config {
    Button {
      id=menu://applications/Accessories/pcmanfm.desktop
    }
    Button {
      id=lxde-x-www-browser.desktop
    }
    FlatButton=0
    GroupedTasks=0
    UseSmallerIcons=-1
    ShowAllDesks=0
  }
}
Plugin {
  type=space
  Config {
    Size=4
  }
}
Plugin {
  type=wincmd
  Config {
    Button1=iconify
    Button2=shade
  }
}
Plugin {
  type=space
  Config {
    Size=4
  }
}
Plugin {
  type=pager
  Config {
  }
}
Plugin {
  type=space
  Config {
    Size=4
  }
}
Plugin {
  type=bluetooth
  Config {
  }
}
Plugin {
  type=tray
  Config {
  }
}
Plugin {
  type=indicator
  Config {
    applications=1
    datetime=0
    messages=0
    network=0
    session=0
    sound=1
  }
}
Plugin {
  type=dclock
  Config {
    ClockFmt=%l:%M %p
    TooltipFmt=%A, %d %b %Y
    BoldFont=1
    IconOnly=0
    CenterText=0
  }
}
Plugin {
  type=launchbar
  Config {
    Button {
      id=/usr/share/applications/lubuntu-logout.desktop
    }
  }
}

```

Not sure where to put [FONT=system]set network=1[/FONT]though.

Where is the settings panel?

---

### Post by Xian on 2019-06-13
Admittedly that was a bit of a stretch .... 

Follow the instructions listed in this post and report back:

[https://ubuntuforums.org/showthread.php?t=2403372&p=13808039#post13808039](https://ubuntuforums.org/showthread.php?t=2403372&p=13808039#post13808039)

---

### Post by Xian on 2019-06-13
> **ardouronerous said:**
> 
Not sure where to put [FONT=system]set network=1[/FONT]though.

> [COLOR=#000000]Plugin {[/COLOR] type=indicator
Config {
applications=1
datetime=0
messages=0
network=0
session=0
sound=1



You would change network=0 to network=1

---

### Post by ardouronerous on 2019-06-14
It fixed the problem, after restarting, there's only one network app.
But it created another problem, my battery applet vanished though.

---

### Post by ardouronerous on 2019-06-14
I had to restore [FONT=system]/.config/lxpanel/Lubuntu/panels/panel[/FONT] back to it's default settings because my battery applet vanished.

I've discovered a solution, but it's a messy solution though: [https://ubuntuforums.org/showthread.php?t=2387434&p=13750208#post13750208](https://ubuntuforums.org/showthread.php?t=2387434&p=13750208#post13750208)

```
[Desktop Entry]
Version=1.1
Type=Application
Name=pkill nm-applet && nm-applet &
Exec=sh -c "sleep 10 && pkill nm-applet && nm-applet &"

```

I created this launcher and placed it in [FONT=system]/.config/autostart/[/FONT]. I gave it a 10 second delay because when I tried it without the delay, it didn't work.

---

