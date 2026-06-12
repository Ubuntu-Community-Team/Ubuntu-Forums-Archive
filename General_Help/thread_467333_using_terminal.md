---
title: "using terminal"
date: 2007-06-07
forum: General Help
---

### Post by Irti on 2007-06-07
hey...is there any way i can close a program using the terminal

---

### Post by Sockerdrickan on 2007-06-07
kill -9 PROCESS-ID

---

### Post by jfinkels on 2007-06-07
> **Irti said:**
> hey...is there any way i can close a program using the terminal

yes, you can do this:
```
killall *nameofprocess*
```
or this:
```
pidof *nameofprocess* | xargs kill
```
or this:
```
xkill
```
or, if you started it in the terminal and it is living in the terminal, press Ctrl+C to send the interrupt signal, or Ctrl+D to send the terminate signal.

---

### Post by Irti on 2007-06-07
coooooollllll...thanx a lot......ok could you also please tell me how do i check on which processes are running (alternative to cntrl+alt+del  in xp)...

---

### Post by drs305 on 2007-06-07
Minimum typing (not neceesarily fastest if you are quick with the keyboard and the program name is short) is with jfinkels suggestion:
```
xkill
```

It will create a skull and crossbones out of the mouse cursor. The first window you click on immediately closes. Of course, if you use the mouse you can also just click on the X ...

---

### Post by borahshadow on 2007-06-07
try
> top

---

### Post by eggdeng on 2007-06-07
There's a processes tab in the System Monitor applet (Add to Panel -> System and Hardware). ```
ps -A
``` will get you this info from the terminal.

---

### Post by Irti on 2007-06-07
niceeeeeeeeeeeee........really nice......ok how do i uninstall a program using the terminal........

---

### Post by jfinkels on 2007-06-07
> **eggdeng said:**
> There's a processes tab in the System Monitor applet (Add to Panel -> System and Hardware). ```
ps -A
``` will get you this info from the terminal.

I prefere ```
ps ax
```It shows all processes, including those not necessarily associated with a tty (a terminal). Read more by typing ```
man ps
```

> **Irti said:**
> niceeeeeeeeeeeee........really nice......ok how do i uninstall a program using the terminal........

Depends how you installed it. If you installed it using Synaptic or apt-get (or aptitude), type the following:
```
sudo aptitude remove *packagename*
```
or you might try this if you installed from a .deb file and aptitude doesn't uninstall it (although I think aptitude takes care of all installed .debs anyway):```
sudo dpkg -r *packagename*
```

Read more about installing software here: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Crafty Kisses on 2007-06-07
> **jfinkels said:**
> yes, you can do this:
```
killall *nameofprocess*
```
or this:
```
pidof *nameofprocess* | xargs kill
```
or this:
```
xkill
```
or, if you started it in the terminal and it is living in the terminal, press Ctrl+C to send the interrupt signal, or Ctrl+D to send the terminate signal.

They're many ways. :D

---

### Post by AoisDeCogadh on 2007-06-13
Is there a way to have a program close after a certain amount of time (basically a sleep timer for one program, instead of something like GShutDown to turn the whole computer off)?

---

### Post by Sockerdrickan on 2007-06-13
ps -e | grep thenameoftheprogram and you get processid

kill -9 id

---

### Post by jfinkels on 2007-06-13
> **AoisDeCogadh said:**
> Is there a way to have a program close after a certain amount of time (basically a sleep timer for one program, instead of something like GShutDown to turn the whole computer off)?

I'm not on a Linux computer right now but you might look into doing something like this:

Start the program (for example, firefox):```
firefox
```

Then do this (the number after sleep is the number of seconds to sleep): ```
sleep 60 && killall firefox
```

---

### Post by eggdeng on 2007-06-13
```
sleep 60 && killall
```
OK! Neat trick.

---

