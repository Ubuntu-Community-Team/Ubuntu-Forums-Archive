---
title: "Does conky v1.10 work with lua scripts?"
date: 2016-04-22
forum: General Help
---

### Post by scooter3 on 2016-04-22
Much searching I've not found a single example of conky 1.10.x (the version in the repos) which works with a lua script in Ubuntu.  Does any one know of any examples?  Or do we need to downgrade to v1.9 to do this?

Any help would be very much appreciated, thanks.

---

### Post by vasa1 on 2016-04-22
> **scooter3 said:**
> Much searching I've not found a single example of conky 1.10.x (the version in the repos) which works with a lua script in Ubuntu.  Does any one know of any examples?  Or do we need to downgrade to v1.9 to do this?

Any help would be very much appreciated, thanks.
I don't know anything about lua scripting but there's no reason for conky 1.10 to not work with lua scripts. The syntax may have changed a bit ...

*man conky* has this:```
       lua_load
              Loads the Lua scripts separated by spaces.

```Edit: outdated links removed.

---

### Post by Habitual on 2016-04-22
conky-all package I believe does LUA.

---

### Post by scooter3 on 2016-04-22
Thanks for the reply.  The documentation in that README.md is all for the old version (1.9) of conky.  

Installing conky-all does indeed install a version that says it works with lua:
   Lua bindings:  * Cairo
  * Imlib2
  * RSVG
and lua_load loads the lua scripts, which I can verify do run but nothing from lua is drawn on the screen.  In trying to debug I searched for any example of conky 1.10 + lua script in ubuntu, but couldn't find a single one.  Made me wonder if anyone has this working in ubuntu?

---

### Post by ajgreeny on 2016-04-22
Are you using the same .conkyrc configuration file as you have in the past?

I've been using conky for several years with the largely same .conkyrc file but in 16.04 I can not get any conky display at all so I'm assuming there has been a change in the required syntax of the configuration file with this new version.

I have not had time to search out any answers to this so far, but will report back if I find anything that may help you.

---

### Post by scooter3 on 2016-04-22
I found an example file for a different linux which had an old version, and a new one which had been converted to conky v1.10 format.  This was very useful and I was able to get my conky + lua running.  The conky syntax has changed a lot, and you can find some documentation if you look around but most of it is still for the older versions.  Look for lines like: "conky_function = true,"  instead of "conky_function yes".  New format uses "=".  

If you search for "ConkyBar" on the web, version 3.1 and 3.2 are converted to conky 1.10, though there are probably simpler examples around.  

Seems a huge change to conky happened last summer with, um, very mild warning. :)

---

### Post by ajgreeny on 2016-04-22
Yes, I found the need for the = sign but there are still some errors that I see when starting it in terminal looking for clues.
I think.you need two ## at the start of comment lines instead of the previous single # but that is yet to be confirmed.

I'll keep looking.

---

### Post by vasa1 on 2016-04-22
Just some notes I put together when I moved to conky 1.10:
conky 1.10 syntax
[LIST]
[*]wrap your config section in **conky.config = { ... }**
[*]wrap your TEXT section in **conky.text = [[ ... ]]**
[*]the config options are lookup values and you need to assign values (i.e. use "=")
[*]each line in the config section ends with ","
[*]replace instances of "yes" and "no" with "true" and "false", respectively (without quotes)
[*]all values except numbers, "true" and "false" need quotes
[*]comments on single lines start with **--** instead of **#**
[*]multi-line comments start with **--[[** and end with **--]]** each in its own line. See [http://stackoverflow.com/a/22722493](http://stackoverflow.com/a/22722493) for comments with internal **[** or **]**
[*]a default conky.conf is here: /usr/share/doc/conky-std/conky.conf or here: /etc/conky/conky.conf 
[/LIST]

---

### Post by vasa1 on 2016-04-22
> **scooter3 said:**
> Thanks for the reply.  The documentation in that README.md is all for the old version (1.9) of conky.  
...
Thanks for pointing that out. I'll edit my post to remove those links. Meanwhile, check out
[Conky v1.10 Thread]("http://crunchbang.org/forums/viewtopic.php?id=39997") (note that many of the developers and posters there moved over to the community continuation at [BunsenLabs]("https://forums.bunsenlabs.org"))
and the [Arch Wiki]("https://wiki.archlinux.org/index.php/conky") because those people get new and shiny programs all the time (rolling release effect).

---

### Post by Frogs Hair on 2016-04-22
To correct my own conky I downloaded a configuration known to work with v1.10 and made changes  line by line.

---

### Post by ajgreeny on 2016-04-23
> **vasa1 said:**
> Just some notes I put together when I moved to conky 1.10:
conky 1.10 syntax
[LIST]
[*]wrap your config section in **conky.config = { ... }**
[*]wrap your TEXT section in **conky.text = [[ ... ]]**
[*]the config options are lookup values and you need to assign values (i.e. use "=")
[*]each line in the config section ends with ","
[*]replace instances of "yes" and "no" with "true" and "false", respectively (without quotes)
[*]all values except numbers, "true" and "false" need quotes
[*]comments on single lines start with **--** instead of **#**
[*]multi-line comments start with **--[[** and end with **--]]** each in its own line. See [http://stackoverflow.com/a/22722493](http://stackoverflow.com/a/22722493) for comments with internal **[** or **]**
[*]a default conky.conf is here: /usr/share/doc/conky-std/conky.conf or here: /etc/conky/conky.conf 
[/LIST]
Thank you vasa1 for that quick "man conky", which is what your notes almost amount to.

It is going to be incredibly useful to me and I think many others who suddenly find that their old .conkyrc file is no use at all as it stands.

---

### Post by vasa1 on 2016-04-23
> **ajgreeny said:**
> Thank you vasa1 for that quick "man conky", which is what your notes almost amount to.

It is going to be incredibly useful to me and I think many others who suddenly find that their old .conkyrc file is no use at all as it stands.
@ajgreeny, from what I understand, conky 1.10 will make an attempt to parse .conkyrc. Whether it does so successfully, is another matter ;)

---

### Post by mcduck on 2016-04-23
So it looks like the config file is now following Lua syntax as well? Nice, I wonder if you can actually just add Lua functions directly in the file then...

---

### Post by vasa1 on 2016-04-23
[new Conky syntax beginning from version 1.10]("https://forum.manjaro.org/index.php?topic=24054.0") 
and
[Conky 1.10 -- Lua conversion]("http://forum.siduction.org/index.php?topic=5709.0")
may be of interest.

---

### Post by ajgreeny on 2016-04-23
> **vasa1 said:**
> @ajgreeny, from what I understand, conky 1.10 will make an attempt to parse .conkyrc. Whether it does so successfully, is another matter ;)
Not successful in my case, I'm afraid, though the error in terminal when I start it that way says it's trying to do so.

I do not use any lua scripts in my configuration, so that is nothing to do with it.

---

### Post by CantankRus on 2016-04-26
The conky-all package includes a **/usr/share/doc/conky-all/convert.lua** script which I 
believe converts your old configs to lua on the fly when you run conky.
It doesn't make any permanent changes to your configs.

You can copy the** convert.lua** script to your home folder, make it executable and use it to permanently convert your configs.
```
cp /usr/share/doc/conky-all/convert.lua ~/ && chmod +x ~/convert.lua
```

Then convert a config using ...
```
/path/to/convert.lua /path/to/old/config /path/to/save/new/lua/config

```
eg...
```
~/convert.lua /home/glen/conky/configs/conkyrc /home/glen/luaconkyrc
```
Still had to make a couple of changes as the lua config didn't recognize **max_specials** or **$pre_exec** and 
**own_window_argb_visual** doesn't appear to work.

---

