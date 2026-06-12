---
title: "get error saying command not found when i try to run gparted"
date: 2012-12-29
forum: General Help
---

### Post by howhy on 2012-12-29
get error saying command not found when i try to run gparted ? I also checked in the software center and it says remove which means its already installed ...but don't know why i get this message ...?

---

### Post by ajgreeny on 2012-12-29
You can not run gparted as a normal user, so I expect you got the error ```
Inhibit all polling failed: Only uid 0 is authorized to inhibit the daemon
```; you need root permissions to run gparted.

The command you need is ```
gksudo gparted
```

---

### Post by dcstar on 2012-12-29
> **ajgreeny said:**
> 
The command you need is ```
gksudo gparted
```

No, you do not "run" graphical commands from the command line - that is what GUI Menu items specifically set up for the program are for.

Telling people to use the command line when they shouldn't results in these issues.

---

### Post by haqking on 2012-12-29
> **dcstar said:**
> No, you do not "run" graphical commands from the command line - that is what GUI Menu items specifically set up for the program are for.

Telling people to use the command line when they shouldn't results in these issues.

[s]I wonder why gksudo exists[/s]

Edit: though i was being sarcastic i just re-read your post and think you meant it differently to how i read it ;-)

---

### Post by howhy on 2012-12-29
either way executing gksudo gparted shows nothing , their si sjust a pause for some seconds and then thats it....

i didn't even go tthe error saying "Inhibit all polling failed: Only uid 0 is authorized to inhibit the daemon"

---

### Post by elliotn on 2012-12-30
Why not try removing Gparted and reinstall it

---

### Post by Mark Phelps on 2012-12-30
Actually, if the OP is trying to launch Gparted from the Dash -- and seeing nothing as a result, running it from inside a terminal is an excellent way to see if any error messages are produced when the app is launched.

So, for diagnostic purposes, running GUIs from the command line can be a useful approach.

---

### Post by rnerwein on 2012-12-30
> **Mark Phelps said:**
> Actually, if the OP is trying to launch Gparted from the Dash -- and seeing nothing as a result, running it from inside a terminal is an excellent way to see if any error messages are produced when the app is launched.

So, for diagnostic purposes, running GUIs from the command line can be a useful approach.
hi
that's it. i always running gparted from a shell (mostely working in a shell).
but don't forget you have to run it from a root-shell
cheers

---

### Post by ajgreeny on 2012-12-30
> **Mark Phelps said:**
> Actually, if the OP is trying to launch Gparted from the Dash -- and seeing nothing as a result, running it from inside a terminal is an excellent way to see if any error messages are produced when the app is launched.

So, for diagnostic purposes, running GUIs from the command line can be a useful approach.
Thanks for the confirmation Mark; I was beginning to doubt myself for suggesting "gksudo gparted".

@ dcstar.
> No, you do not "run" graphical commands from the command line - that is  what GUI Menu items specifically set up for the program are for.

Telling people to use the command line when they shouldn't results in these issues.     
Why do you suggest that you should not run a GUI application from terminal or a command in Alt+F2 or from dash and that it will cause such issues to occur?  As long as you use **gksudo <command>** rather than **sudo <command>** for GUI apps there is absolutely no problem at all.

---

### Post by howhy on 2012-12-31
> **elliotn said:**
> Why not try removing Gparted and reinstall it

i uninstalled and installed it again, now I am getting a different error saying "/usr/sbin/gpartedbin: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
"

I run using *sudo gparted*

i looked for libgtkmm in usr/lib folder and its their in but of version higher i.e. libgtkmm-3.0.so.1 .. so Do i need to get a lower version exact if so how can i get libgtkmm-2.4.so.1 and should i place it in the gparted directory or apt-get will manage it itself?

---

### Post by stinkeye on 2012-12-31
gparted works fine here and synaptic shows the libgtkmm installed packages
as in pic.

---

### Post by ajgreeny on 2012-12-31
> **howhy said:**
> i uninstalled and installed it again, now I am getting a different error saying "/usr/sbin/gpartedbin: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
"

[COLOR=Red]I run using ***sudo gparted***[/COLOR]

i looked for libgtkmm in usr/lib folder and its their in but of version higher i.e. libgtkmm-3.0.so.1 .. so Do i need to get a lower version exact if so how can i get libgtkmm-2.4.so.1 and should i place it in the gparted directory or apt-get will manage it itself?
As I said in my last post, you should always use **"gksudo <command>"** not** "sudo <command>"** for a GUI application; sudo is just for command line utilities, not GUI, and if you insist in using sudo for that purpose it is possible to lock yourself out of admin for the machine.

See RootSudo in my signature for more info and details.

---

### Post by ivotkl on 2012-12-31
> **Mark Phelps said:**
> Actually, if the OP is trying to launch Gparted from the Dash -- and seeing nothing as a result, running it from inside a terminal is an excellent way to see if any error messages are produced when the app is launched.

So, for diagnostic purposes, running GUIs from the command line can be a useful approach.

Totally agree. I also run it always from terminal and with root privileges. I am thinking that uid0 may be related to permissions. I think that error means your user is not authorised to run the program.

By the way, gksudo does not exist on my system. I always used sudo and never had a problem. Have you tried running update and dist-upgrade afterwards? What happens if you mark it for complete removal or see the dependencies? Does any other program need that higher version of libraries installed? Which OS and version are you running? gparted works fine on my Ubuntu 12.04 and asks me for root pwd if I run it using Alt+F2.

---

### Post by oldos2er on 2012-12-31
> **howhy said:**
> get error saying command not found when i try to run gparted ? I also checked in the software center and it says remove which means its already installed ...but don't know why i get this message ...?

We seem to be missing some basic information. Can you tell us which version of Ubuntu you're running, and is it Ubuntu, or Lubuntu, Xubuntu, or ?

Also if you could run the following command in a terminal and copy/paste the output here, it might help. ```
sudo apt-get update && sudo apt-get install gparted
```

---

