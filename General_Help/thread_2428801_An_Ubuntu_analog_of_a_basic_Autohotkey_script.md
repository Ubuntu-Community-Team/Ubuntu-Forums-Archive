---
title: "An Ubuntu analog of a basic Autohotkey script"
date: 2019-10-09
forum: General Help
---

### Post by zorath2 on 2019-10-09
I spent a week worth of free time researching this simplest of questions, tried several approaches, asked Stack Exchange - all to no avail. The script is supposed to disable my broken mouse wheel and let me use the numpad for mouse scrolling:

```
WheelUp::return
WheelDown::return
$NumpadSub::Send {WheelUp}
$NumpadAdd::Send {WheelDown}

```
What I tried already:


[LIST=1]
[*]xbindkeys + xdotool. Mouse wheel blocking works but mouse wheel emulation does not: 'clicks' emulated by xdotool get blocked by xbindkeys too. 
[*]xmodmap. All kinds of weird side effects. People say it is deprecated and should not be used. 
[*]xinput. Does not work at all, supposedly because of a conflict with libevent. Removing the latter disabled my keyboard and mouse completely. 
[*]Took a look at xkb but could not find any actionable documentation. 
[/LIST]

Ubuntu 18.04.3. Any suggestions?

---

### Post by Holger_Gehrke on 2019-10-09
Finding the name for the mouse with xinput
```
xinput -list
```
Killing the scrollwheel-function using the name found in the previous step (could use the numerical id, but that's subject to change on boot so it's not so good for use in scripts;obviously the name will be different on your machine)
```
xinput --set-button-map "Logitech USB-PS/2 Optical Mouse" 1 2 3 0 0
```
Using xdotool to scroll up and down
```
xdotool click 4; xdotool click 5
```
Works fine as far as that. Now just assign those two commands to the keys in your "~/.xbindkeysrc"
```

...
"xdotool click 4"
  KP_Subtract

"xdotool click 5"
  KP_Add
...

```

Seems to work for me on XUbuntu 18.4.3 ...

Holger

---

### Post by zorath2 on 2019-10-09
Sadly, the xinput part does not work for me. The sequence below blocks mouse wheel in Firefox and Double Commander but not in Chromium or Gnome terminal.

```
$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; VirtualBox mouse integration                id=9    [slave  pointer  (2)]
&#9116;   &#8627; ImExPS/2 Generic Explorer Mouse             id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
$ xinput --set-button-map "ImExPS/2 Generic Explorer Mouse" 1 2 3 0 0 6 7 8
```

---

### Post by dragonfly41 on 2019-10-09
I use Actiona quite often for emulation and automation of workflows.

I have not tried the wheel action in the library of objects but it is [described here]("https://wiki.actiona.tools/doku.php?id=en:actions:actionwheel").

Actiona is an alternative to autohotkey.

P.S. the script can be run without GUI by command

**actexec myscript.ascr**

---

### Post by zorath2 on 2019-10-09
**dragonfly41**, could you please provide something like a complete script with a trigger? Because I tried all these tools in every combination imaginable and they always do one of the two things:


[LIST=1]
[*]Refuse to block the physical mouse wheel outright. 
[*]Block the synthesized mouse wheel events along with the physical ones. 
[/LIST]
 
There is no middle ground like Autohotkey has.

---

### Post by dragonfly41 on 2019-10-09
Actiona *emulates* actions and does not *react* to external events. For that you need to look at devilspie2 or Autokey
which can use defined rules to trigger scripts such as Actiona or xdotool or bash.

---

### Post by zorath2 on 2019-10-09
Unfortunately, devilspie2 does not seem to be relevant either.

---

### Post by dragonfly41 on 2019-10-09
Found this ..

[https://askubuntu.com/questions/874287/how-to-run-custom-command-by-pressing-a-key](https://askubuntu.com/questions/874287/how-to-run-custom-command-by-pressing-a-key)

This needs to be run in two steps

Detect hot keys to launch a script

System Settings > Keyboard > Shortcuts > Custom shortcuts
Create a new shortcut for mousewheel up
Create a new shortcut for mousewheel down

Now create a script for each action.

I have tried 
Super+Up -> mouse wheel up
and 
Super+Down -> mouse wheel down
 
Note: your screen might freeze while setting accelerator keys for each new shortcut. This happened to me.
Just hit backspace to clear freeze.

---

### Post by zorath2 on 2019-10-09
Emulating the mouse wheel is not a problem. The difficulty lies in  blocking the physical mouse wheel at the same time.

---

### Post by dragonfly41 on 2019-10-10
[disable mouse up and down]("https://askubuntu.com/questions/59128/how-to-disable-mouse-wheel-scroll-in-ubuntu-11-04-or-10-10")

I would try that.

---

### Post by zorath2 on 2019-10-10
**dragonfly41**, please see post #3.

Okay, I'll be checking on this thread once in a while. If anyone knows a solution, please kindly share.

---

