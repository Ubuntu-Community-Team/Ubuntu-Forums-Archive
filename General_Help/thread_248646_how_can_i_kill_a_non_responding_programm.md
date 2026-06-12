---
title: "how can i kill a non responding programm?"
date: 2006-09-01
forum: General Help
---

### Post by eighthate on 2006-09-01
thanks

---

### Post by Anonii on 2006-09-01
The best way if its a GUI application is to:

"ALT + F2" and  call the program "xkill" then click on the bad program.

---

### Post by professor_chaos on 2006-09-01
other ways for both gui and non-gui apps, is to kill the process by the name of the process, by using "killall" followed by the process name.

ex 
```
killall gnome-panel
```

if you know the process id, or pid. For example, in the terminal you can type ps -aef. And you will get a list of processes running.  You can then use the command kill to kill the process.

ex for a pid of 2893
```
kill -9 2893
```

---

### Post by Anonii on 2006-09-01
> **professor_chaos said:**
> other ways for both gui and non-gui apps, is to kill the process by the name of the process, by using "killall" followed by the process name.

ex 
```
killall gnome-panel
```

if you know the process id, or pid. For example, in the terminal you can type ps -aef. And you will get a list of processes running.  You can then use the command kill to kill the process.

ex for a pid of 2893
```
kill -9 2893
```
You can find the process id with the top command:
_top_
and check the PID section.

And then, as professor_chaos said, you can kill it with 
*kill -9 <PID>*

Also, check "man top" for more info, if you like to learn more.

---

### Post by morrin on 2006-09-01
ps x will get you a list of processes and ids. If you type in top, as mentioned above, you can simply type k and then you will see "PID to kill:" at the top. You can just give it the PID there or a -9 PID if it's not dying

---

### Post by john_markh on 2006-09-01
1. First of all you will need to figure out the PID (process id) of none responding program 
```
ps -a
```
2. Find your application in the list and kill it
```
kill 6922
```where 6922 is your process id

---

### Post by ayoli on 2006-09-01
another nice way to use kill without run ps or top before:

```
kill -9 `pidof application_name`
```
replace application_name with the name of app you want to kill.
btw there is also an gnome applet named force quit which can be use to kill graphica apps by cliking on them.
regards.

---

### Post by jotagab on 2006-09-01
If you want to avoid the command-line add the "Force Quit" to your panel:
-Mouse right-click
-Add to Panel...
-[Desktop & Windows] Force Quit

Then click on it, and then on the non-responding application (but beware, I think you can also kill the panel itself, or even Gnome).

---

### Post by jis on 2006-09-07
Is there a "Force Quit" equivalent for Xfce?

---

### Post by slimdog360 on 2006-09-07
my favourite way is pressing  ctrl+alt+esc    you get a cool skull and crossbones

---

### Post by ayoli on 2006-09-07
> **slimdog360 said:**
> my favourite way is pressing  ctrl+alt+esc    you get a cool skull and crossbones

seems that it doesnt work here.

---

### Post by jis on 2006-09-07
ctrl+alt+esc works in Xubuntu, too. Thanks for the hint. 

I used Settings -> Menu Editor to add the "Kill Program" (xkill) below "Run Program" in the Applications menu. I wish I could use the cool skull and crossbones as an icon for that item. (Checking "Use startup notification" seems to have no effect.)

---

