---
title: "gnome-system-monitor and snap"
date: 2018-09-21
forum: General Help
---

### Post by ChrisOfBristol on 2018-09-21
gnome-system-monitor won't run, from a terminal I get this message about snap - the suggested commands don't work.

chris@dxp051:~$ gnome-system-monitor
You need to connect this snap to the gnome platform snap.

You can do this with those commands:
snap install gnome-3-26-1604
snap connect gnome-system-monitor:gnome-3-26-1604 gnome-3-26-1604

(the '3-26-1604' number defines the platform version and might change)

---

### Post by Claus7 on 2018-09-21
Hello,

I do not know why you are getting this message, yet, have you checked if you have installed gnome-system-monitor from synaptic package manager? If you have updated recently, some packages in your system are snap ones. Since you face such an issue I would advice you to remove the snap package in question and install the regular one.

Regards!

---

### Post by mc4man on 2018-09-21
> **ChrisOfBristol said:**
> gnome-system-monitor won't run, from a terminal I get this message about snap - the suggested commands don't work.

chris@dxp051:~$ gnome-system-monitor
You need to connect this snap to the gnome platform snap.

You can do this with those commands:
snap install gnome-3-26-1604
snap connect gnome-system-monitor:gnome-3-26-1604 gnome-3-26-1604

(the '3-26-1604' number defines the platform version and might change)
What happened when you ran those 2 commands? (likely needing sudo..

---

### Post by monkeybrain20122 on 2018-09-21
In 18.04 gnome-system monitor in the default install in  a snap package (the other is gnome-calculator, there is one more snap but I can't remember which ) you can remove it and install the deb in the normal repository, problem solved.
```

sudo snap remove gnome-system-monitor
sudo apt install gnome-system-monitor


```

P.S if you install software from the software centre/software store you may get a snap package and some of them only work partially because of sandboxing and what not and at least in my experience they slow down boot time. Since I don't use the software store I don't know if it indicates whether package are snap or not. If you install from the synaptic package manager then you get only .debs (not snap) and in any case the listing in synaptic is much more complete than the software store (except for snaps and proprietary/paid apps)

```
sudo apt install synaptic
```

---

### Post by ChrisOfBristol on 2018-09-22
[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("https://ubuntuforums.org/member.php?u=1843403") removing the snap and installing the deb looks like the simplest plan, and it works.

---

