---
title: "problems opening a script in a terminal at startup"
date: 2007-02-20
forum: General Help
---

### Post by oracle5 on 2007-02-20
I wrote a script that I need to open up in a terminal window at the startup of a session. I put sh location_of_script in with System>Prefs>session but it never opens up the terminal window. The script requires user input so I know its not completing.

Thanks,
oracle5

---

### Post by RedSquirrel on 2007-02-20
Maybe you have to specify the terminal command to make it open a terminal, for example:

gnome-terminal -x location_of_script

Have a look at the man page of whatever terminal you're using.

```
 man gnome-terminal

```

---

### Post by kerry_s on 2007-02-20
what command are you using to open the terminal?
i use> xterm -T "name" -e command/path to script 
for instance for prozilla(not startup item)->
xterm -T "Prozilla" -e dproz

man xterm <for options.

So from what you describe->
xterm -T "Script" -e /path/to/script  <startup session entry
 
or you could just put the script in /usr/bin
xterm -T "Script" -e script   <startup session entry

---

