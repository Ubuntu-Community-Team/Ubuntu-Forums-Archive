---
title: "wine at startup"
date: 2007-12-13
forum: General Help
---

### Post by gishaust on 2007-12-13
hi everyone

I have a friend that I have talked into using ubuntu on an old laptop. Install was fine and everything is working great. A part of the deal that he has one windows app that he uses all the time and he wants to keep using it. I know that this program works in wine I have seen on another ubuntu machine one time. So I have done a complete install,update  and then apt-get install wine.

What I want to know is I need program to work on the startup program how do I do this. I looked at preferences--> sessions--> startup tap.   What do i do next?

---

### Post by wormser on 2007-12-13
Session is the right place.  What program are you trying to run?  You need to click on Add, Give it a name and the command to run the program.  If this is program to run in Wine the command might be a bit tricker but it should be able to be done.

---

### Post by gishaust on 2007-12-14
what type of command would I have to give

---

### Post by 8daysaweek.co.uk on 2008-04-17
I have the same question, did you solve the issue in the end gishaust?

I have a program that is working well using WINE, but I would like it to start automatically too.  I've added it to **System > Preferences > Sessions > Startup Programs** (as I have with a couple of other Linux programs that start fine) and copied the command from the working app launcher to a new entry in Startup Programs (**env WINEPREFIX="/home/*<username>*/.wine" wine "C:\Program Files\*<path to>*.exe"** ).

However it doesn't work.  Nothing happens, no error or anything.

Is there a way to do this in Startup Programs, or somewhere else I can put the command to get this program to start?

TIA,

---

### Post by danwood76 on 2008-04-17
change the command to just 
```

wine "C:\Program Files\<path to>.exe"

```

and it should work, you can test by running the command in the terminal and if it loads it will laod up in the sessions tab.

the alternative is to do
```

wine /complete/path/to/app.exe

```

the wine complete path is something like:
```

"~/.wine/C_DRIVE/Program Files/app.exe"

```

---

### Post by 8daysaweek.co.uk on 2008-04-17
Thanks danwood76 but it doesn't work I get a whole lot of errors in the terminal window ending in "failed, status c0000135".

However another program works using this method, so I know your instructions are right, perhaps it is something to do with the particular exe.

That's why I was wondering if there's another way of running a WINE program other than putting it in  Startup Programs?

EDIT: I have only tried with the terminal so far, haven't restarted, so I'll report back if there's different behaviour after a restart.

---

### Post by danwood76 on 2008-04-17
I just installed wine to my laptop and got notepad to load on startup by adding this line to my sessions:

```

wine "c:/windows/notepad.exe"

```

what app are you trying to run?

---

### Post by forrestcupp on 2008-04-17
> **danwood76 said:**
> 
the wine complete path is something like:
```

"~/.wine/C_DRIVE/Program Files/app.exe"

```
It's a little bit off.  Also remember that if you're going to use this path without quotes, you need a **\** before the space:
```
~/.wine/drive_c/Program\ Files/app.exe
```

Sometimes Wine needs you to be in the proper directory before the exe will work.  If this is your problem, one way to get it to work is to make a script and put the script in your sessions.  Open up your text editor and make a script like this:
```
#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/*program's_directory*
wine ./*app_name.exe*
```
Substituting the correct folder for your program and the correct file you're trying to run.  Then save that file somewhere in a safe place, open up a terminal and cd to the directory you saved the script to and type:
```
chmod +x ./*script_name*
```to make it executable.  Then you can just point your startup entry in your sessions to that script and it may work.

But if the program doesn't work when you try to run it from the terminal, it's not going to work any way you do it.  But it could have just not been working because you weren't already in the proper directory.

---

### Post by danwood76 on 2008-04-17
> **forrestcupp said:**
> It's a little bit off.  

Yeah sorry was off the top of my head, pretty close though.

---

### Post by 8daysaweek.co.uk on 2008-04-17
> **forrestcupp said:**
> But if the program doesn't work when you try to run it from the terminal, it's not going to work any way you do it.  But it could have just not been working because you weren't already in the proper directory.

Thank you, I think that answers it for the program I was trying to run - I can't open it from the terminal anyway (behaviour as described above even when in the right directory).

*However*, I can't get the method to work for a program which ***does*** start from the terminal:

```
#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/TightVNC
wine ./vncviewer.exe
```

I named the file **vnctest** and saved it in a directory called scripts, then:
```
user@computer:~$ cd scripts
user@computer:~/scripts$ chmod +x ./vnctest
user@computer:~/scripts$ vnctest
bash: vnctest: command not found
user@computer:~/scripts$
``` 

But if I do the steps manually I get this in the terminal...
```
user@computer:~/scripts$ cd ~/.wine/drive_c/Program\ Files/TightVNC
user@computer:~/.wine/drive_c/Program Files/TightVNC$ wine ./vncviewer.exe
fixme:spoolsv:serv_main (0 (nil))
fixme:advapi:CheckTokenMembership (0x68 0x127d80 0x33fb60) stub!
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
```
...and the program starts fine.

Have I done something wrong with the script?

---

### Post by forrestcupp on 2008-04-17
> **8daysaweek.co.uk said:**
> Thank you, I think that answers it for the program I was trying to run - I can't open it from the terminal anyway (behaviour as described above even when in the right directory).

*However*, I can't get the method to work for a program which ***does*** start from the terminal:

```
#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/TightVNC
wine ./vncviewer.exe
```

I named the file **vnctest** and saved it in a directory called scripts, then:
```
user@computer:~$ cd scripts
user@computer:~/scripts$ chmod +x ./vnctest
user@computer:~/scripts$ vnctest
bash: vnctest: command not found
user@computer:~/scripts$
``` 

But if I do the steps manually I get this in the terminal...
```
user@computer:~/scripts$ cd ~/.wine/drive_c/Program\ Files/TightVNC
user@computer:~/.wine/drive_c/Program Files/TightVNC$ wine ./vncviewer.exe
fixme:spoolsv:serv_main (0 (nil))
fixme:advapi:CheckTokenMembership (0x68 0x127d80 0x33fb60) stub!
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
```
...and the program starts fine.

Have I done something wrong with the script?
You just need to be in your scripts directory and type
```
./vnctest
```instead of just vnctest.

---

### Post by 8daysaweek.co.uk on 2008-04-17
Ah I see, thank you.  Do I need to use ./vnctest or just browse to vnctest (for instance) when pointing to this script in Startup Programs?

If I just browse to it I get **home/user/scripts/vnctest** in the "Command:" box, is that correct?

TIA,

---

### Post by danwood76 on 2008-04-17
Yeah just browse to it and it is fine, it will launch the script and load the program.

---

