---
title: "Migration from Windows questions"
date: 2007-02-07
forum: General Help
---

### Post by aFoundling on 2007-02-07
Hi,

I'm new to Linux/Ubuntu - I only installed at the beginning of this week. I'm coming over from XP which I'm very familiar with so I'd like to ask a few questions on how to use Ubuntu mostly.

I apoligise if use the wrong terminology etc :) Please do correct me:)

1. I often find things crash - Updaters etc crash. Normally I'd go to Task Manager > Applications to see a list of programs and if they're responding. But I've heard the beauty of Linux is that programs don't respond anyway?? Is there an easy way of forcing programs to close? 

2. Is there an easy way to get WMAs to work with Banshee/Rhythm Box? 

I'm sorry if these are really dumb-*** questions lol 

Cheers for you help in advance :) 

Tom

---

### Post by rj686 on 2007-02-07
> **aFoundling said:**
> Hi,

I'm new to Linux/Ubuntu - I only installed at the beginning of this week. I'm coming over from XP which I'm very familiar with so I'd like to ask a few questions on how to use Ubuntu mostly.

I apoligise if use the wrong terminology etc :) Please do correct me:)

1. I often find things crash - Updaters etc crash. Normally I'd go to Task Manager > Applications to see a list of programs and if they're responding. But I've heard the beauty of Linux is that programs don't respond anyway?? Is there an easy way of forcing programs to close? 

2. Where is the equivalent "Program Files" folder? 

3. Is there an easy way to get WMAs to work with Banshee/Rhythm Box? 

4. How do you get to a command line? 

I'm sorry if these are really dumb-*** questions lol 

Cheers for you help in advance :) 

Tom

1) You can add Force Quit to your toolbar if the program does crash. So that way you just click force quit + click the window and boom g'bye misbehaving program.

2) Usually programs are intalled under /usr/bin, But unlike windows, linux doesn't duplicate libraries or (dlls in windows) so those located seperately.

3)w32codecs might do it for ya, but bare in mind some DRM'ed songs might not work

4) Applications > Accessories > Terminal


CHEERS

-RJ

---

### Post by allwin on 2007-02-07
I'm a dyed in the wool Windows user.  I share your newness but...

You often need to do things with terminal commands.   To get a terminal, look for "TERMINAL" in the menus.  This opens up what amounts to a DOS window or cmd.exe.

To display what is running, use the ps command (print stack?).  Like ps -x.  Each task has a number.  To stop the thing, you do "kill 12345" if 12345 was the name of the task.  Warning, this is like terminating a process in Windows.  Do the wrong one and you can be in trouble.

The "bin" subdirectories are where the "programs" are contained, but just like Windows they can be all over the place.  With Linux, there can be links to files, too, something not in Windows at all.  Allows you to place a reference to a file in a different folder, so you can access it from two places, basically, the containing folder, or another folder such as /bin where it's considered convenient, where the link is installed.

You can play WMA files if you load the codecs.  I don't know how to make the specific players you mention work.  There is a program called AUTOMATIX which you can use to install them all.  Install them and you may find that they work.  Use SYNAPTIC to install Automatix.

BTW, there is no registry.  Most config data is contained in text files in the /etc/ directory.  Also there are hidden files and an option in Nautilus (like Explorer) to show them.   They start with a ".".  Are all over the place.  Also, text files can be executable (like DOS BAT files) if their permissions are set to allow them to be "run" as programs.  Peek around a bit with the hidden files shown and familiarize yourself with them.  And remember, it's all case sensitive and the slashes go forward ///////.

AFAIK, the "windows" you see are produced by the X server which sits atop its own command line (tty).  Rather like the old days of Windows when you boot to DOS and then go "win".  Lose the X server, and you are placed at a command line again.  This can happen when things go awry, so you need to develop some "terminal FU" to get back to a GUI again, such as if you start playing with Beryl 3D desktops and various cutting edge video drivers.  Conceptually, all the things you do with the nice graphics you see are translated to DOS commands and fed to the "DOS prompt", and the result of those commands are translated back to graphics again.  That's a crude thumbnail of what goes on.

---

### Post by graigsmith on 2007-02-07
> **aFoundling said:**
> Hi,

I'm new to Linux/Ubuntu - I only installed at the beginning of this week. I'm coming over from XP which I'm very familiar with so I'd like to ask a few questions on how to use Ubuntu mostly.

I apoligise if use the wrong terminology etc :) Please do correct me:)

1. I often find things crash - Updaters etc crash. Normally I'd go to Task Manager > Applications to see a list of programs and if they're responding. But I've heard the beauty of Linux is that programs don't respond anyway?? Is there an easy way of forcing programs to close? 

2. Is there an easy way to get WMAs to work with Banshee/Rhythm Box? 

I'm sorry if these are really dumb-*** questions lol 

Cheers for you help in advance :) 

Tom

1. there are several ways.  for one. you can use the system monitor.  (system/administration/system monitor).  right click anything in there you want and kill it.   you can also add a mini system monitor to your taskbar, and click it it opens the system monitor.  this is the easiest way.

you can also kill programs by name from the command prompt.  by typing killall *nameofprogram*  like```
killall totem
```

you can also use the command line program "top" to kill programs.  (hit h in the program for help)  this is most useful to kill programs that are using too much cpu time.

2.  not sure. i try to steer clear of those formats.  i use ogg, mp3 and regular avi files and mpgs.

---

### Post by graigsmith on 2007-02-07
> BTW, there is no registry. Most config data is contained in text files in the /etc/ directory. Also there are hidden files and an option in Nautilus (like Explorer) to show them. They start with a ".". Are all over the place. Also, text files can be executable (like DOS BAT files) if their permissions are set to allow them to be "run" as programs. Peek around a bit with the hidden files shown and familiarize yourself with them. And remember, it's all case sensitive and the slashes go forward ///////.


there is something similar to the registry in gnome. called gconf-editor  just launch it from the command prompt.  you can change certain system settings in there that you cant get to otherwise.  for the most part you never need to go there. so it's probably a bad idea to mess with it if you don't need to.   I'm not actually sure if if gconf editor edits a bunch of text files or if it's just one text file more like microsoft's registry?

---

### Post by aFoundling on 2007-02-10
Ahh thankyou! I've realised I've got to learn a whole new "language" of sorts - I must admit I don't really use command prompts.

That Force Quit button will stay on my task bar :)

I must admit I'm new to forums; I've just realised that I may have impeded on some rules - Is there an extensive FAQ that you could recommend (and perhaps should have read before asking questions)?

---

