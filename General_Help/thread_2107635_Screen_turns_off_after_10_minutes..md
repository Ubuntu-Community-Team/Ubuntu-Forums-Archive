---
title: "Screen turns off after 10 minutes."
date: 2013-01-22
forum: General Help
---

### Post by Champlin93 on 2013-01-22
So this problem seems pretty common  but I've already tried the usual solutions. Xscreensaver has been removed and purged and in my settings it says:
> Turn screen off when inactive for:  NEVER 
This is extremely annoying when  am trying to watch videos so please help.
So what else could be causing my screen to turn off?

---

### Post by Laiquendi on 2013-01-22
Check in "Brightness & lock"

---

### Post by bryanl on 2013-01-22
If you set all the screensaver and lock settings to avoid screen blanking and still get the screen blanking, try using 'xset s 0 0' at the command line and see if that works. 

If that works, you can add the line to the end of '/etc/profile' so it will be a part of the login script.

xset is the user preference utility for X. I find that the screen blanking by X keeps coming back up every now and then. It seems that the various parts of the stack from video driver up to user interface all have their own ideas about screen blanking and sometimes get out of sync.

I used to modify the X config file in etc but later versions often don't have one. So I am using xset and it solved the problem that showed up in 12.10 for me. (and thanks to the dude on these forums who clued me in to xset!)

---

### Post by matt_symes on 2013-01-22
Hi
 
You can also disable dpms using xset. That may be the issue. (I would need to double checki the command as i am on a windows PC at the moment but it's somtthing like...)
 
```
xset -dpms
```
 
It is rather drastic purging xscreensaver as well.
 
Take a look at 
 
```
xscreensaver-command
```
 
You can write a simple script to exit the screensaver when you start to watch a video and start it again when the video is finished.
 
That's what i do when uing mplayer from the console.
 
Kind regards

---

### Post by Champlin93 on 2013-01-25
Thanks xset dpm didn't do anything for me but xset s 0 0 worked like a charm and i put that at the end of my /etc/profile
And I purged xscreensaver only because i never use it and wanted to be sure it wasn't causing my problem.

---

### Post by Champlin93 on 2013-01-25
Thanks! That worked perfectly. I put the command in /etc/profile and will see if it works on restart.

---

### Post by Balthier1979 on 2013-02-07
I'm having the same problem
 
[http://ubuntuforums.org/showthread.php?t=2110791&highlight=xscreensaver](http://ubuntuforums.org/showthread.php?t=2110791&highlight=xscreensaver)
 
What does xset s 00 do? I can't see it disabling dpms or setting standby/suspend/off to 0, when running xset q
 
And what does entering commands in /etc/profile do? Is that a list of commands that are run at the start up?
 
I have found that if I set dpms to off, it only stays off until I restart the computer, then it gets turned back on. The only way I can keep it off perhaps, is to start xscreensaver and xscreensaver-demo at start up. But then I'd need to close the xscreensaver-demo window after it has been starte dand set dpms to off.

---

### Post by matt_symes on 2013-02-09
Hi

> **Balthier1979 said:**
> I'm having the same problem
 
[http://ubuntuforums.org/showthread.php?t=2110791&highlight=xscreensaver](http://ubuntuforums.org/showthread.php?t=2110791&highlight=xscreensaver)
 
What does xset s 00 do? I can't see it disabling dpms or setting standby/suspend/off to 0, when running xset q

> xset -dpms   The -dpms option disables DPMS (Energy Star) features.

from bthe  man pages, dpms is used to control the energy saving on the monitor.

> s       The  s  option  lets  you  set  the screen saver parameters.

***xset s  ***is used to control the screen saver parameters.
> 
This option accepts up to two numerical parameters, a
               'blank/noblank' flag, an 'expose/noexpose' flag, an 'on/off' flag, an 'activate/reset' flag, or the 'default' flag.
 
> 
And what does entering commands in /etc/profile do? Is that a list of commands that are run at the start up?
 
I have found that if I set dpms to off, it only stays off until I restart the computer, then it gets turned back on. The only way I can keep it off perhaps, is to start xscreensaver and xscreensaver-demo at start up. But then I'd need to close the xscreensaver-demo window after it has been starte dand set dpms to off.

info on /etc/profile

```
http://publib.boulder.ibm.com/infocenter/pseries/v5r3/topic/com.ibm.aix.baseadmn/doc/baseadmndita/etc_prof_file.htm
```

and from the man pages
> 
When  bash  is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads
       and executes commands from the file /etc/profile, if that file exists.

Please post the output of /etc/profile.

Kind regards

---

