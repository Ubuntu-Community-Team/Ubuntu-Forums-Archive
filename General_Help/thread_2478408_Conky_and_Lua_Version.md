---
title: "Conky and Lua Version"
date: 2022-08-25
forum: General Help
---

### Post by keithc2 on 2022-08-25
I have a conky config file which is using lua. It is a simple conky that displays the current weather.

 If I issue the command: ```
conky -c <path to my conky config file>
```, I get the following errors:
```
conky: llua_do_call: function conky_weather_desc execution failed: <path to my conky config file>:55: module 'lunajson' not found:
    no field package.preload['lunajson']
    no file '/usr/local/share/lua/5.3/lunajson.lua'
    no file '/usr/local/share/lua/5.3/lunajson/init.lua'
    no file '/usr/local/lib/lua/5.3/lunajson.lua'
    no file '/usr/local/lib/lua/5.3/lunajson/init.lua'
    no file '/usr/share/lua/5.3/lunajson.lua'
    no file '/usr/share/lua/5.3/lunajson/init.lua'
    no file './lunajson.lua'
    no file './lunajson/init.lua'
    no file '/usr/lib/conky/liblunajson.so'
    no file '/usr/local/lib/lua/5.3/lunajson.so'
    no file '/usr/lib/x86_64-linux-gnu/lua/5.3/lunajson.so'
    no file '/usr/lib/lua/5.3/lunajson.so'
    no file '/usr/local/lib/lua/5.3/loadall.so'
    no file './lunajson.so'

```
I have identified the problem. Conky is looking for the lunajson module in the wrong place. Seems that conky is configured to work with lua version 5.3. However, I am running lua version 5.4
To expound on the problem: conky wants to look for the 'lunajson' module in '/usr/local/share/lua/5.3/lunajson.lua' when the actual path is /usr/local/share/lua/5.4/lunajson.lua. 
If I issue the following commands:
```
~$ cd /usr/local/share/lua/5.4/
:/usr/local/share/lua/5.4$ conky -c <path to my conky config file>

```
I get no errors because it is able to find the lunajson files, but I have to make sure to run conky from /usr/local/share/lua/5.4/

How can I make conky look for the /usr/local/share/lua/5.4 folder instead of /usr/local/share/lua/5.3?

---

### Post by Irihapeti on 2022-08-25
*Thread moved to **General Help**, as it's a request for support.*

(FTR, Forum Feedback and Help is for issues with the working of the forum itself.)

---

### Post by norobro on 2022-08-25
Try using update-alternatives to change the lua version:```
$ lua -v
Lua 5.1.5  Copyright (C) 1994-2012 Lua.org, PUC-Rio

$ sudo update-alternatives --config lua-interpreter
There are 2 choices for the alternative lua-interpreter (providing /usr/bin/lua).

  Selection    Path             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/lua5.1   110       auto mode
  1            /usr/bin/lua5.1   110       manual mode
  2            /usr/bin/lua5.4   20        manual mode

Press <enter> to keep the current choice
[*], or type selection number: 2
update-alternatives: using /usr/bin/lua5.4 to provide /usr/bin/lua (lua-interpreter) in manual mode

$ lua -v
Lua 5.4.4  Copyright (C) 1994-2022 Lua.org, PUC-Rio
```

---

### Post by keithc2 on 2022-08-26
Interesting:
```
$ lua -v
Lua 5.4.3  Copyright (C) 1994-2021 Lua.org, PUC-Rio
$ sudo update-alternatives --config lua-interpreter
There is only one alternative in link group lua-interpreter (providing /usr/bin/lua): /usr/bin/lua5.3
Nothing to configure.
```
Have no idea how this happened.

Anyway updated all the packages for lua 5.4 and ran the following commands (chose the 5.4 option):
```
$ sudo update-alternatives --config lua-compiler
There are 2 choices for the alternative lua-compiler (providing /usr/bin/luac).

  Selection    Path              Priority   Status
------------------------------------------------------------
  0            /usr/bin/luac5.3   120       auto mode
  1            /usr/bin/luac5.3   120       manual mode
* 2            /usr/bin/luac5.4   20        manual mode

Press <enter> to keep the current choice
[*], or type selection number: ^C
$ sudo update-alternatives --config lua-interpreter 
There are 2 choices for the alternative lua-interpreter (providing /usr/bin/lua).

  Selection    Path             Priority   Status
------------------------------------------------------------
  0            /usr/bin/lua5.3   120       auto mode
  1            /usr/bin/lua5.3   120       manual mode
* 2            /usr/bin/lua5.4   20        manual mode

Press <enter> to keep the current choice
[*], or type selection number: 

```

However, conky is still looking for lunajson in /usr/local/share/lua/5.3/
```

conky: llua_do_call: function conky_weather_desc execution failed: <path to my conky config file>:55: module 'lunajson' not found:
    no field package.preload['lunajson']
    no file '/usr/local/share/lua/5.3/lunajson.lua'
    no file '/usr/local/share/lua/5.3/lunajson/init.lua'
    no file '/usr/local/lib/lua/5.3/lunajson.lua'
    no file '/usr/local/lib/lua/5.3/lunajson/init.lua'
    no file '/usr/share/lua/5.3/lunajson.lua'
    no file '/usr/share/lua/5.3/lunajson/init.lua'
    no file './lunajson.lua'
    no file './lunajson/init.lua'
    no file '/usr/lib/conky/liblunajson.so'
    no file '/usr/local/lib/lua/5.3/lunajson.so'
    no file '/usr/lib/x86_64-linux-gnu/lua/5.3/lunajson.so'
    no file '/usr/lib/lua/5.3/lunajson.so'
    no file '/usr/local/lib/lua/5.3/loadall.so'
    no file './lunajson.so'

```

---

### Post by keithc2 on 2022-08-26
I have also tried uninstalling and re-installing conky.

---

### Post by norobro on 2022-08-26
> **keithc2 said:**
> However, conky is still looking for lunajson in /usr/local/share/lua/5.3/
That's puzzling . . .

Try installing lunajson for version 5.3 to see if that works:```
$ sudo luarocks --lua-version 5.3 install lunajson
```

---

### Post by Cavsfan on 2022-08-28
I could not use the conky-all version that is default for 22.04 and it uses lua extensively. I test for Param, a friend who maintains the conky with added weather from [[COLOR=blue]HOWTO: VinDSL Conky Script[/COLOR]]("https://ubuntuforums.org/showthread.php?t=1771033").

He codes in Perl, Lua and some others bigly.

Jammy comes with conky version 1.12.2-1 and my conkys didn't work as they should. I had to install an older version because that version is not ready IMO.

I installed [[COLOR=blue]conky-all_1.11.6-2_amd64.deb[/COLOR]]("https://pkgs.org/download/conky-all") from that page. The actual deb file download seems difficult to find; at least for me.

That version worked better.

[[img]http://i.imgur.com/lLyoiSfl.png[/img]](https://imgur.com/lLyoiSf)

---

