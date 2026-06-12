---
title: "how to kill an application in ubuntu?"
date: 2007-06-04
forum: General Help
---

### Post by bone2006 on 2007-06-04
With windows clt+alt delete and then I'd kill the application if something went wrong.  I know that if I'm in the command line I can hit clt+c and the process would be killed.  I don't want to completely log out as in clt+alt+backspace.  Is there anything I can do to kill a running application?

I was reading that kde has clt+escape and something comes up that shows you a list, so you can kill any application.  Anything like this for gnome?

---

### Post by bishop9226 on 2007-06-04
yes you can add kill app to the top bar and then click the icon.  or you can make ctrl alt delete open up system monitor/taskbar and kill things that way.  or you can right click the frozen app and you should be able to do exit and then itll bring up a kill menu

if youre using beryl you can bind ctrl alt delete or ctrl alt whatever you want to system monitor, if you arent using beryl you can download ctrl-alt-delete on AUTOMATIX

to add force kill to the top panel - Right click on one of your panels, select add to panel, then drag force quit to the panel

---

### Post by HeavyMetalMessiah on 2007-06-04
The way i do it is to run top to find the PID and then the command kill to stop it.

```
top
kill <PID>
```

---

### Post by FuturePilot on 2007-06-04
Best way to do it.
Alt+F2
```
killall program_name
```

Example: Say you want to kill gnome panel
```
killall gnome-panel
```

---

### Post by bishop9226 on 2007-06-04
i find using the mouse is much easier.  a click here and a click there, everything done with one hand:)

---

### Post by bone2006 on 2007-06-04
what seemed to work the best was I found another post which was none related was pushing alt+f2 and typing in xkill then clicking on what needs killed.

---

### Post by fdrake on 2007-06-04
kill -9 $(ps e |grep name_process)

like if i want to kill firefox or beryl but i don't know the exact id number and name just type:
 kill -9 $(ps e | grep firefox)
 kill -9 $(ps e | grep beryl)

---

### Post by martnemma on 2007-06-06
I have set <Ctrl><ALT>Escape to run xkill and NOT the default cycle panels as ubuntus default settings
Open up a terminal
type gconf-editor

Open Apps
            Metacity
                Keybinding-Commands
select Command_1

Edit command set value to xkill (right click .. Edit Key)

Open Global-Keybindings

CLEAR the value from cycle_panels and cycle_panels_backward

ADD  value to run_command_1

type <Control><Alt>Escape

logout and logback in

you now have <CTRL><ALT>Escape set to xkill and app 

Or you could just add the force quit icon to the "task" bar (right click add to panel and select "force quit"

Much prefer <Ctrl><Alt>Esc though.


-----------------------------

If it dont work its windows

If it does its Linux !!

----------------------------

Martin

---

