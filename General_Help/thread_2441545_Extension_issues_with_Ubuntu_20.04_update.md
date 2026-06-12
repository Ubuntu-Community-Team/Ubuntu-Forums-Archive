---
title: "Extension issues with Ubuntu 20.04 update"
date: 2020-04-24
forum: General Help
---

### Post by amanagarwal2 on 2020-04-24
[COLOR=#1A1A1B][FONT=&amp][SIZE=3][FONT=arial]The 20.04 stable update rolled out today, and although it feels much more cleaner and snappier, I am facing some major problems after the update.

[/FONT][/SIZE][/FONT][/COLOR]
[SIZE=3][FONT=arial]1) Snap Store says that automatic updates are paused because the computer is connected to a metered network. I made sure that the network was not set to metered, and also tried switching to another network. Still, it doesn't seem to solve the problem.

[/FONT][/SIZE]
[SIZE=3][FONT=arial]2) Problem with many extensions.
[/FONT][/SIZE]
[COLOR=#1A1A1B][FONT=&amp][SIZE=3][FONT=arial]These extensions give error[/FONT][/SIZE][/FONT][/COLOR]

[LIST]
[*][SIZE=3][FONT=arial]GSConnect has stopped working.[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Dynamic panel transparency (To make Title bar transparent) has stopped working[/FONT][/SIZE]
[/LIST]
[COLOR=#1A1A1B][FONT=&amp][SIZE=3][FONT=arial]These extensions dont give an error in tweak tools, still they don't work as intended or don't work at all[/FONT][/SIZE][/FONT][/COLOR]

[LIST]
[*][SIZE=3][FONT=arial]Internet speed meter values are alligned unsymetrically.[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Coverflow Alt+tab has stopped working[/FONT][/SIZE]
[*][SIZE=3][FONT=arial]Cpu power manager (similar to cpufreq) doesnt work.
[/FONT][/SIZE]
[/LIST]
[COLOR=#1A1A1B][FONT=&amp][SIZE=3][FONT=arial]3) Text in right click menu for some apps is overlapping

4) Cpu and Gpu temps running slightly higher compared to 19.10
(This may be due to cpu power manager not working or the update may have made changes to the tlp package)
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp][SIZE=3][FONT=arial]Screenshots:[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp][SIZE=3][FONT=arial][https://imgur.com/RlYjEEO](https://imgur.com/RlYjEEO)
[https://imgur.com/11EoOf5](https://imgur.com/11EoOf5)
[https://imgur.com/CJLvKra](https://imgur.com/CJLvKra)
[/FONT][/SIZE][/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp][SIZE=3][FONT=arial]Is anybody else facing these problems? Any possible solutions?[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by VMC on 2020-04-24
I don't use snapd, but have you tried ```
sudo apt update
```?

Also "[SIZE=3][FONT=arial]Dynamic panel transparency (To make Title bar transparent) has stopped working", stopped working when Gnome was upgraded. 
Not sure if this will work, but work a try:
[https://github.com/rockon999/dynamic-panel-transparency/issues/111](https://github.com/rockon999/dynamic-panel-transparency/issues/111)
edit: the above link, if followed will indeed make top panel transparent again!
[/FONT][/SIZE]

---

### Post by Dennis N on 2020-04-24
Extensions may not have a new version ready for Ubuntu 20.04. You have to wait and hope one appears. For example, "Dynamic Panel Transparency" does not show a version for Gnome Shell 3.36. 

Some Gnome Shell themes have a transparent panel. You could find and use one of those. I use Flat Remix Dark and it has transparency for the panel. An extension is not needed. 

I've tried Internet Speed Meter in the past, and didn't like the display as I recall. I removed it. 

Sometimes, an extension just stops being supported and you need to find a substitute if possible.

Snap Store - I removed Snap Store and installed Gnome Software from the Ubuntu Repository instead. You lose no functionality by doing so. In fact, it has more functionality since it also supports Flatpak, and I wanted that support. You could try this and see if things improve.

---

