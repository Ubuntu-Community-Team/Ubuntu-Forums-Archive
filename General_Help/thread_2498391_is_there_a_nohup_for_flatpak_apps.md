---
title: "is there a nohup for flatpak apps"
date: 2024-06-11
forum: General Help
---

### Post by buill on 2024-06-11
hi i control a ubuntu laptop running kodi and open it via a ssh command from my phone this all worked fine until i just upgraded to latest version which is now flatpak not apt but when i leave the app it closes kodi not very familiar with flatpak was wondering if anyone knew how to keep it running when oged in terminal closes

old ccode which worked --
[COLOR=#080808][COLOR=#8c8c8c][I]("export DISPLAY=:0\n"+"nohup "+"kodi"+"\n");

new code with the flatpak which opens it but closes once i leave the app
[/I][/COLOR][COLOR=#080808]([COLOR=#067d17]"export DISPLAY=:0[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"[/COLOR]+[COLOR=#067d17]"nohup "[/COLOR]+[COLOR=#067d17]"flatpak run tv.kodi.Kodi"[/COLOR]+[COLOR=#067d17]"[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"[/COLOR]);

i have tried
[/COLOR][/COLOR][COLOR=#080808][COLOR=#080808]([COLOR=#067d17]"export DISPLAY=:0[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"[/COLOR]+[COLOR=#067d17]"nohup "[/COLOR]+[COLOR=#067d17]"flatpak run tv.kodi.Kodi"[/COLOR]+[COLOR=#067d17]" nohup[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"[/COLOR]);
still did not work[/COLOR][/COLOR]
[COLOR=#080808][COLOR=#080808] 


[/COLOR]
[/COLOR]

---

### Post by #&amp;thj^% on 2024-06-11
I'm guessing, but have you tried the working code with a trailing "&"
ie:
```
("export DISPLAY=:0\n"+"nohup "+"flatpak run tv.kodi.Kodi"+"\n") &
```

---

### Post by buill on 2024-06-11
thanks for reply im using java you cant end a statement with and like sudo apt update & sudo apt upgrade will make system try both at once sudo apt update && sudo apt upgrade will update then upgrade once finished you cant say & without giving an anoher command or condition i have been reading about disown cmd maybe that could be the solution

---

### Post by #&amp;thj^% on 2024-06-11
I know just enough java to get me and you in trouble, so I'm stepping to the sideline.

Good Luck though

---

### Post by Holger_Gehrke on 2024-06-11
Neither kodi nor 1fallen's use of '&' have anything to do with Java. A '&' at the end of a shell command makes the process run in the background. That's what happens in the example you give, apt update is run in the background and the shell proceeds to execute the next command, 'apt upgrade' which of course tries to use the same resources as the update command and therefore fails.
'disown' might actually be an idea, especially with the option '-h' which basically does the same thing as nohup: it stops the shell from passing on the 'hangup' signal to this child process. So what I'd try:
```

DISPLAY=:0.0 flatpak run tv.kodi.Kodi &

```
This should print two numbers, the first one in brackets is the job number the second is the process id. Now you can use
```

disown -h jobnumber

```
(replace the obvious ...)

Holger

---

### Post by currentshaft on 2024-06-12
Use tmux, a program which lets you leave running terminal sessions open which you can connect and disconnect to.

---

### Post by buill on 2024-06-14
thanks for replys

i tryed 
[COLOR=#080808][COLOR=#067d17]"export DISPLAY=:0[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"[/COLOR]+[COLOR=#067d17]"nohup "[/COLOR]+[COLOR=#067d17]"flatpak run tv.kodi.Kodi"[/COLOR]+[COLOR=#067d17]" disown -a [/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17] nohup[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"
but it still closes when the session neds

it print 

[/COLOR] export DISPLAY=:0
19:56:19.643  I  nohup flatpak run tv.kodi.Kodi disown -a 
19:56:19.643  I   nohup
19:56:19.643  I  med1a@med1a-Lat:~$ export DISPLAY=:0
19:56:19.643  I  med1a@med1a-Lat:~$ nohup flatpak run tv.kodi.Kodi disown -a 
19:56:19.643  I  nohup: ignoring input and appending output to 'nohup.out'

but then kodi closes aaargh i like flatpak but would in this case would pref if i coucld just get a deb
[/COLOR]

---

### Post by buill on 2024-06-14
A HA
[COLOR=#067d17]"export DISPLAY=:0[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"[/COLOR]+[COLOR=#067d17]"nohup "[/COLOR]+[COLOR=#067d17]"flatpak run tv.kodi.Kodi"[/COLOR]+[COLOR=#067d17]"& disown -a [/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17] nohup[/COLOR][COLOR=#0037a6]\n[/COLOR][COLOR=#067d17]"

i left out the & oops now she is working thanks so much for help and replys[/COLOR]

---

