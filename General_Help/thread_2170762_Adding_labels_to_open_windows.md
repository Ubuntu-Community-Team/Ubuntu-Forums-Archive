---
title: "Adding labels to open windows"
date: 2013-08-27
forum: General Help
---

### Post by ZaHACKieL on 2013-08-27
Do you guys know if there is an app to add labels to open windows? I usually have a lot of terminals opened, some logged in my pc, some logged in other pcs and I sometimes lose track of which is which because not all are in the command line, some are opened in mysql or other applications that do not actively show the user/host.

It's not just the user/host problem but also the task running there. So I thought it would be cool to have an app to add a label to the titlebar so you can quickly identify/group your windows. I know you can change the title if you use tabs in a terminal but I don't like using a lot of tabs.

I use Ubuntu 12.04LTS with classic gnome (never got used to Unity)

Any thoughts?

Thanx!

---

### Post by rai_shu2 on 2013-08-27
I use different terminal programs for different types of jobs. For some jobs, I use Xfce terminal, and then use xterm for others. That makes it pretty obvious which is which, and there are lots of terminal applications out there.

---

### Post by ZaHACKieL on 2013-08-27
It's true that there are a lot of terminal applications but what about if I want to use just the xterm? Also, my idea about labeling windows can be expanded to other programs.

---

### Post by stinkeye on 2013-08-27
wmctrl can do this.
```
sudo apt-get install wmctrl
```


eg
list widows...
```
wmctrl -l
```

Change title...
```
wmctrl -r [COLOR="#808080"]title[/COLOR] -N [COLOR="#808080"]newtitle[/COLOR]
```
where title is the current title of the window.

Can also change title of the currently focused window.
eg
```
wmctrl -r :ACTIVE: -N [COLOR="#808080"]newtitle[/COLOR]
```


Add a sleep command for time to select window...
```
sleep 3 && wmctrl -r :ACTIVE: -N [COLOR="#808080"]newtitle[/COLOR]
```


Raise a window with title "MyTitle"  and give it focus....if a "MyTitle" window doesn't exist
launch gnome-terminal and rename to "MyTitle"
```
wmctrl -a MyTitle || gnome-terminal && sleep 1 && wmctrl -r :ACTIVE: -N MyTitle
```

See...
```
man wmctrl
```

---

