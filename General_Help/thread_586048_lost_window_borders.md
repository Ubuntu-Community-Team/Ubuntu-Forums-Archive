---
title: "lost window borders"
date: 2007-10-21
forum: General Help
---

### Post by nickoli on 2007-10-21
My computer gave me this error message.
Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory.Killing bonobo-activation-server and restarting Nautilus may help fix the problem.
I lost my window borders. The only way I can get any window borders is to run beryl. I don't like to run beryl all the time. I noticed that when I log into different user accounts I still have my borders and I don't get any error messages. Any help in this matter will be appreciated. I'd hate to do a complete reinstall if I don't have to. Thanks.:confused:

---

### Post by DagMan on 2007-10-21
try opening a terminal and typing 
metacity --replace & disown
and if you aren't able to get a terminal working properly then hit ctrl-alt-f1 then log in and type
DISPLAY=:0 metacity --replace &
then hit ctrl-alt-f7

If it persists beyond a reboot then adding to the startup via system->preferances->sessions
metacity --replace
will do it on every boot, but you need to remember it's there in case it later messes with beryl loading at startup should you choose to use it later.

---

### Post by Beggar on 2007-10-21
Haha, I doubt this is the answer, but whats the system time, I seem to remember the reason I got this error was my system time got all confused.

---

### Post by Mateo on 2007-11-24
Same problem here.  However, when I restart the computer it is gone again.  I don't want to have to type that command every time.  how do I make it the way it used to be?

---

