---
title: "keyboard does'nt answer anymmore....."
date: 2018-05-01
forum: General Help
---

### Post by discou on 2018-05-01
[FONT=Liberation Serif][SIZE=3]Hi everyone,[/SIZE][/FONT]

  [FONT=Liberation Serif][SIZE=3]I don't know what happened but I don't have any more mouse and keyboard with ubuntu 17…. the session start normally without any problem but those don’t answer at all ….[/SIZE][/FONT]
  [FONT=Liberation Serif][SIZE=3]
I tried to start the computer in advance mode with different hearts… but I've the same result…[/SIZE][/FONT]
[FONT=Liberation Serif][SIZE=3]
when I want to re install with this line : [/SIZE][/FONT]```
[FONT=Liberation Serif][SIZE=3]sudo apt-get install --reinstall xserver-xorg[/SIZE][/FONT]

  [FONT=Liberation Serif][/FONT]
```[FONT=Liberation Serif][SIZE=3]
I've this error : 

[B][I]Building dependency tree
Reading state information...Done
Reinstallation of xserver-org is not possible, it cannot be downloaded.[/I][/B][/SIZE][/FONT]****
  
  [FONT=Liberation Serif][SIZE=3]I even connected my computer in Ethernet to be sure it has Internet.[/SIZE][/FONT]

 [FONT=Liberation Serif][SIZE=3]I did a boot-info if it can help anyone to understand what’s happening : [http://paste.ubuntu.com/p/NWC6Xk9dgn/](http://paste.ubuntu.com/p/NWC6Xk9dgn/)[/SIZE][/FONT]

  
 
 [FONT=Liberation Serif][SIZE=3]I would like to precise I don’t have this file **/etc/X11/xorg.config** ?? instead i’ve [/SIZE][/FONT]**[FONT=Liberation Serif][SIZE=3]/etc/X11/xorg.config.failsafe[/SIZE][/FONT]**[FONT=Liberation Serif][SIZE=3] ?? is it normal ? I tried to rename this file without[/SIZE][/FONT]**[FONT=Liberation Serif][SIZE=3] .failsafe[/SIZE][/FONT]**[FONT=Liberation Serif][SIZE=3] but it changes nothing ….

this is the file :[/SIZE][/FONT][B][FONT=Liberation Serif][SIZE=3]
[/SIZE][/FONT][/B]```

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```[B][FONT=Liberation Serif][SIZE=3]
[/SIZE][/FONT][/B]
 [FONT=Liberation Serif][SIZE=3]Do you have any idea ?? Do I have to reinstall everything ???[/SIZE][/FONT]

 [FONT=Liberation Serif][SIZE=3]Thank for your answers[/SIZE][/FONT]

---

