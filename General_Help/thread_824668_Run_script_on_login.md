---
title: "Run script on login"
date: 2008-06-10
forum: General Help
---

### Post by MacAnthony on 2008-06-10
I have a script that checks xrandr to see if my external monitor is connected and changes the config if it is that I would like to run each time I login to the computer with an X session. I am having trouble figuring out which file to put it in. I could run it as a startup file from kde, but would like it if it worked independent of the desktop environment.

---

### Post by skymera on 2008-06-10
Ermm not sure.

System > Prefs > Sessions

Add it there and log back in or restart to see if it works.

---

### Post by Rui Pais on 2008-06-10
> **MacAnthony said:**
> I have a script that checks xrandr to see if my external monitor is connected and changes the config if it is that I would like to run each time I login to the computer with an X session. I am having trouble figuring out which file to put it in. I could run it as a startup file from kde, but would like it if it worked independent of the desktop environment.

The natural place for such kind of scripts - interaction with system/hardware - it's call it from /etc/rc.local (add a line with your script full path before the existent exit 0)

You may need however to put the screen as boot service before X being load...

---

### Post by MacAnthony on 2008-06-10
I thought about putting them in init and I think I may have the same issue if it's in rc.local - but here is the question with that. Don't those run prior to some one logging in? X seems to use the external monitor when kdm loads, but after login, it seems like it resyncs and then only uses the main display - which was the reason for the script.

So it seems to me that it would just do what it's already doing by default then unless I'm wrong about when those files are executed.

---

### Post by MacAnthony on 2008-06-11
I thought I had read that the .profile is run each time some one logs in, but that must be only for terminal sessions as it had no affect.

Still looking for a solution though.

---

### Post by Rui Pais on 2008-06-13
Hi again, 
i'm quite sure what your script it's suppose to do...

I assumed that according to you have an external monitor connected or not it would change/replace X server configuration. 

Thats why i suggested run it at boot system level. But if it depends or run at user/desktop login level i doubt that it can change X server configuration.

If on contrary /etc/rc.local it's too late (X server already loaded) you can add the script to /etc/init.d/ and call it as a system service, before X server, by creating symbolic links for it named:
/etc/rc2.d/S01myscreenscript
...
/etc/rc5.d/S01myscreenscript

---

### Post by MacAnthony on 2008-06-16
it's just a simple xrandr script that looks to see if the external monitor is connected and if it is, runs an xrandr command to include the external monitor.

The reason I didn't think it would work is that on the login screen (which before it gets there, I assume it's running all the init.d and rc.local stuff) it uses the external monitor but changes to only the single monitor upon logging in. My script is likely my ignorant way of getting around an X config I don't understand, but it's easier than using bigdesktop or another solution.

The more I talk about this and the more I think about it. I think making a startup link for it in kde may be the way to go although I would have to do that in each desktop environment (I play around with others like xfce as well) if I would go that route, I think.

I'm probably overcomplicating this, but I'm just messing around to get it to work a bit smoother for myself.

---

### Post by dinbrca on 2008-06-16
just a bot question..
what language can i create a script that i can add to /etc/rc.local

---

### Post by bingoUV on 2008-06-16
Add your script in ~/.xsession. It will get run on X startup. Whether from KDE/Gnome/XFce or whatever desktop environment. Even if you use only a window manager like fluxbox.

---

### Post by MacAnthony on 2008-06-16
Awesome, bingoUV. I'll try that later tonight and post results.

---

### Post by MacAnthony on 2008-06-17
Ok, I put the contents of my file into a .xsession file, but that didn't seem to work. I'll mess around with a few things with it, but if you have any ideas in the mean time, it would be appreciated.

---

### Post by bingoUV on 2008-06-18
Does it have execute permissions?
```

chmod 755 ~/.xsession

```

---

### Post by MacAnthony on 2008-06-18
yes. There wasn't a .xsession file, so I just copied the script I had (which already had execute) and removed the #! line.

---

### Post by bingoUV on 2008-06-18
~/.xsession might get run when the X server is not fully initialized. This makes some X operations impossible through this file. To test, put "xterm &" in the beginning of the file. If you see xterm window after X starts, the script is getting run but X is not ready to do your stuff at that point in time.

You could also see in ~/.xsession-errors file if something got logged there.

Also, no need to remove the #! line, it might even help to have such a line in the beginning. At worst, it is just an extra line. At best, it could suggest X the correct interpreter to use to execute the file.

---

### Post by MacAnthony on 2008-06-18
I'll try adding the xterm line.

I did check .xsession-errors and nothing seemed to be related.

Thanks again for the suggestions.

---

### Post by Vivek788 on 2008-06-18
hey can i make a script to do automatic login?is it to be put in rc.local?

---

### Post by MacAnthony on 2008-06-18
Hmm. No xterm started and searched the .xsession-errors file for xterm but nothing.

---

### Post by MacAnthony on 2008-06-20
Ok, so tried a few more things.

I changed the content of the .xsession file to:
```

xterm &
exec kde

```

Which didn't have any effect. I then changed the exec to exec xfce to see if that would work. Again, no effect. Based on a tip from some one in the #xorg irc channel that kdm might actually start .xinitrc instead of .xsession, I created a symbolic link targeting it to my .xsession file. Still nothing. I even tried explicitly starting xfce to see if it was related to kde since kde saves my sessions (relaunches the apps that were open on last logout). Again, nothing.

I think I'm running out of things to try.

---

### Post by unutbu on 2008-06-20
Would you be satisfied with a solution that relies on kdm, or do you change login managers as well?

If kdm is a constant, then check out /etc/kde3/kdm/Xstartup. I'm getting this from an example at
[https://help.ubuntu.com/community/SynergyHowto](https://help.ubuntu.com/community/SynergyHowto)
Sorry I can't be more specific -- I don't have kdm installed.

---

### Post by MacAnthony on 2008-06-20
That should work fine for my solution. I'll check that out.

I am still bewildered why the .xsession file isn't working though. Kind of unnerving.

---

### Post by unutbu on 2008-06-20
man xsession:

```
       /etc/X11/Xsession is a Bourne shell (sh(1)) script which is run when an X Window
       System session is begun by startx(1x) or a  display  manager  such  as  xdm(1x).
       ([B]Some  display managers only invoke Xsession when specifically directed to so by
       the user[/B]; see the documentation for your display  manager  to  find  out  more.)
```

Xsession calls ~/.xsession via 
/etc/X11/Xsession.d/50x11-common_determine-startup
I believe. So if Xsession is ignored, so will ~/.xsession.

---

### Post by MacAnthony on 2008-06-23
Xstartup, as it turns out, executes when kdm starts up so prior to user logging in and therefore doesn't really serve my purpose. I did some reading through the other files and found out that the /etc/kde/kdm/Xsession file (which should be ran when X starts) calls the ~/.profile file. Even though I had tried that before, I am retrying that route to make sure that I did it correctly. I was doing some hardware repair on my computer this weekend so didn't get around to fully testing that. Should get to it this evening though. I'll post results.

---

