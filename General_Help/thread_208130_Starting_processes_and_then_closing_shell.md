---
title: "Starting processes and then closing shell"
date: 2006-07-03
forum: General Help
---

### Post by Mau on 2006-07-03
I recently got a new, old machine that I want to use as some sort of limited server.  It has no monitor connected to it.

When I connect via SSH, I want to be able to start a process, but then disconnect from SSH and close the shell with the process still running.  Is this possible to do?  I am executing a PHP script that logs IRC channels, so I can change the script.

---

### Post by scxtt on 2006-07-03
tack an **&** on to the end of the command ... preceeding it by **nohup** may work as well ...

---

### Post by Ramses de Norre on 2006-07-03
Just putting an & after the command wont do the job, the process will still be killed when closing the terminal, what you need to use is nohup:
```
nohup command
```
The nohup command is designed for exactely this purpose. When you put an & after the command you wont see any output and you can use the same terminal for other commands. All output of processes executed with nohup is in   ~/nohup.out.

---

### Post by thasheep on 2006-07-03
I'm not so sure the process is stopped with & once the terminal is closed. I just did
```
 mplayer /home/music/Ibrahim\ Ferrer/Buena\ Vista\ Social\ Club\ Presents\ Ibrahim\ Ferrer/03\ -\ Marieta.mp3 & exit
``` in gnome-terminal and as I expected, the terminal closed and I can here some nice Cuban music :)

---

### Post by FLeiXiuS on 2006-07-03
This may be a bit old school but how about 'screen'.  I loved resumable screen sessions!

---

### Post by Ramses de Norre on 2006-07-03
[QUOTE=thasheep]I'm not so sure the process is stopped with & once the terminal is closed. I just did
```
 mplayer /home/music/Ibrahim\ Ferrer/Buena\ Vista\ Social\ Club\ Presents\ Ibrahim\ Ferrer/03\ -\ Marieta.mp3 & exit
``` in gnome-terminal and as I expected, the terminal closed and I can here some nice Cuban music :)[/QUOTE]
This is strange, I hadn't noticed it yet but it seems that closing the terminal with exit doesn't kill processes executed with &, but closing a terminal like gnome-terminal with the close button does.. I don't know why.. (anyone?)

---

### Post by mlind on 2006-07-03
[QUOTE=FLeiXiuS]This may be a bit old school but how about 'screen'.  I loved resumable screen sessions![/QUOTE]

Ditto. Screen is one of the best "hidden gems" that average linux user should add
to their bag of tools. I reckon someone should write good screen wiki howto with
some nice examples, if there already isnt' one.

For starters, check out simple but good guige this [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)

---

### Post by mlind on 2006-07-03
[QUOTE=Ramses de Norre]This is strange, I hadn't noticed it yet but it seems that closing the terminal with exit doesn't kill processes executed with &, but closing a terminal like gnome-terminal with the close button does.. I don't know why.. (anyone?)[/QUOTE]

I don't know, but close button probably sends a different signal to all running
processes on that terminal session? 

I have this strange behaviour with Azureus (java process). If I fork the process on
background and exit the terminal,  sometimes the process dies, sometimes it
doesn't..

---

### Post by FLeiXiuS on 2006-07-03
[QUOTE=mlind]Ditto. Screen is one of the best "hidden gems" that average linux user should add
to their bag of tools. I reckon someone should write good screen wiki howto with
some nice examples, if there already isnt' one.

For starters, check out simple but good guige this [http://jmcpherson.org/screen.html](http://jmcpherson.org/screen.html)[/QUOTE]

Myfavorite parameters we're always:

$ screen -A -m -d -S 

Easy to remember,AMDS.

---

