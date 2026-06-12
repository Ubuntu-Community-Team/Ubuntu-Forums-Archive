---
title: "Script to turn off beryl when launching World of Warcraft"
date: 2006-12-16
forum: General Help
---

### Post by glave on 2006-12-16
I'm trying to get a script going that will toggle beryl back to kde, then launch WoW, and on exit of WoW, retoggle beryl to take back over.

The problem is, sometimes it seems the first toggle does not take effect, then WoW launches. After it exits, the second toggle DOES work, and then I'm in the wrong mode. This seems to be intermittent though, as sometimes the first toggle works.

```
!/bin/sh
/usr/bin/killall -USR2 beryl-manager
sleep 3
/usr/X11R6/bin/wine "/media/storage/Games/World of Warcraft/WoW.exe" -opengl
sleep 3
/usr/bin/killall -USR2 beryl-manager

```

Am I missing something?

---

### Post by koenn on 2006-12-16
you could try to at least have the WoW statement only execute if the previous statements (kill Beryl ; sleep ) are executed with succes (and if they fail, WoW won't run, you just try again)

```

#!/bin/sh
/usr/bin/killall -USR2 beryl-manager  && sleep 3 && \
/usr/X11R6/bin/wine "/media/storage/Games/World of Warcraft/WoW.exe" -opengl  ;
sleep 3
/usr/bin/killall -USR2 beryl-manager

```

' && ' means 'AND', for an AND statement to be true, both parts need to be true.  the result is that the statements after an && only gets executed if the previous part is 'true' (i.e. returns '0' for success), because if it doesn't, there's no point in running the second statement. 

the \ is to 'escape' the end-of-line, i.e. make the statement continue on the next line

try and see if it works

you can also grab the return code of "./usr/bin/killall -USR2 beryl-manager " and only run the rest of your script if it was successfull
something like
```

/usr/bin/killall -USR2 beryl-manager
if [ "_$?" = "_0"  ] ; then
       # do other stuff
fi

```

---

### Post by koenn on 2006-12-16
also note you have a # missing at the first line. 
should be #!/bin/sh
don't know how important that is though

---

### Post by robgill on 2006-12-16
> **glave said:**
> I'm trying to get a script going that will toggle beryl back to kde, then launch WoW, and on exit of WoW, retoggle beryl to take back over.

The problem is, sometimes it seems the first toggle does not take effect, then WoW launches. After it exits, the second toggle DOES work, and then I'm in the wrong mode. This seems to be intermittent though, as sometimes the first toggle works.

```
!/bin/sh
/usr/bin/killall -USR2 beryl-manager
sleep 3
/usr/X11R6/bin/wine "/media/storage/Games/World of Warcraft/WoW.exe" -opengl
sleep 3
/usr/bin/killall -USR2 beryl-manager

```

Am I missing something?

You might have to kill beryl not beryl-manager because beryl still runs if beryl-manager is killed if I remember correctly.  B-M starts beryl when it is called, but I belive beryl can run alone.  I don't know anything about scripts though, but if nothing else works try killing beryl-manager AND beryl and just restarting beryl-manager after your game.

---

### Post by aidanr on 2006-12-16
> **robgill said:**
> You might have to kill beryl not beryl-manager because beryl still runs if beryl-manager is killed if I remember correctly.  B-M starts beryl when it is called, but I belive beryl can run alone.  I don't know anything about scripts though, but if nothing else works try killing beryl-manager AND beryl and just restarting beryl-manager after your game.

bingo

this is they way i'd do it

#!/bin/bash
killall beryl &&
wine "/media/storage/Games/World of Warcraft/WoW.exe" -opengl &&
beryl &

---

### Post by glave on 2006-12-16
I actually played with both scripts for a bit, but found a big problem I had. Both worked great, but then I discovered that once in WoW, Tabbing over to use firefox was near impossible, actually tabbing over to do anything didn't work so well since there was no wm running. Here is the comprise that is working great so far:

```

#!/bin/bash
killall beryl &&
kwin &
wine "/media/storage/Games/World of Warcraft/WoW.exe" -opengl &&
beryl &

```

---

### Post by adrift on 2006-12-23
I'd like to run something like this but in Ubuntu. I think all i'd have to change would be the location of the WOW file and Metacity instead of Kwin, is that correct? Also what should i name the script?

---

### Post by Ecthelion on 2007-01-15
I recently also started to make such a script.
Maybe you can help to finish it... There's only one little problem left.

[http://ubuntuforums.org/showthread.php?p=2015148](http://ubuntuforums.org/showthread.php?p=2015148)

You can use that script also for WoW.
You only have to replace "tremulous" by the command to run WoW.
For the moment the script isn't finished yet. ( problem to executed the whole script)

Please go have a look.
Maybe you see what I don't

---

### Post by Ecthelion on 2007-01-15
> For the moment the script isn't finished yet. ( problem to executed the whole script)

The problem is solved.
If you still need this kind of script, you will find it in the second post of this link:
[http://ubuntuforums.org/showthread.php?p=2015505](http://ubuntuforums.org/showthread.php?p=2015505)

The script was written for Tremulous but there's written how to use it for WoW
(I've based it on the command in the first post of this thread:
/usr/X11R6/bin/wine "/media/storage/Games/World of Warcraft/WoW.exe" -opengl
I hope it is correct :)  )

The script is for gnome btw

---

