---
title: "Starting X for certain users only"
date: 2007-06-29
forum: General Help
---

### Post by SelrahCharleS on 2007-06-29
I'm looking for a way to have my computer boot into console mode(already have that figured out) and start X automatically when a certain user(s) logs in. I have a shared computer that gets left on all the time. I have it running a webserver to show photos to friends and family, and I'm trying to conserve resources when it isn't being used for anything else.
    
   I'm somewhat new to Linux, but I'm becoming comfortable with the command line and I use it for certain things. My other family members, on the other hand, only uses the computer for surfing the internet or transferring pictures. I don't want to run GDM all the time, but I don't want them to have to type in anything but their username and password, 

   I would like to be able to boot to console mode, login, and stay in console mode. If I want a graphical environment I can just type "startx /usr/bin/fluxbox" or whatever. But when my family members log in under their accounts I want it to start fluxbox automatically without them having to type in anything. I would appreciate if someone can tell me how I would go about setting that up.

   Another question, I'm trying to do this on a laptop that I want left on all the time, will it automatically turn the screen off after a certain amount of time like it does when X is running? I think xscreensaver does that? I've found that "xset dpms force off" also shuts the monitor off, but only when I'm running X I think. Is there a way to do that when X isn't running?(better yet, automatically after 20 minutes or so if it doesn't already)

Thank you,
Charles

---

### Post by energiya on 2007-06-30
> **SelrahCharleS said:**
> 
   I would like to be able to boot to console mode, login, and stay in console mode. If I want a graphical environment I can just type "startx /usr/bin/fluxbox" or whatever. But when my family members log in under their accounts I want it to start fluxbox automatically without them having to type in anything. I would appreciate if someone can tell me how I would go about setting that up.


Same here. (Consider this a bump)

---

### Post by SelrahCharleS on 2007-07-09
Here is my solution. This is for starting fluxbox automatically, if you just use startx without the extra things I say it will just do your default window manager. 

**Disable GDM:**
Go to the /etc/init.d directory and rename gdm(This step is probably not necessary but I saw in in another thread)
```
$ sudo mv gdm gdm.DISABLED
```

Then: 
```
$ sudo update-rc.d gdm remove 

```
(this step is necessary, unless you just want to uninstall gdm)

**Edit your .xinitrc**
You may have to make this file. It didn't exist on my computer. I use vim, but just substitute that with your preferred text editor(nano, gedit...)

```
$ vim ~/.xinitrc

```

and then add this line: *~/.fluxbox/startup*

(note that you can also do something like '/usr/bin/fluxbox' but that doesn't start up anything but fluxbox, the way I do it starts all of the apps in my fluxbox startup folder such as conky and wmmixer)

**Make startx run when you login**
All you have to do here is add the line '*startx*' to your '~/.bash_profile' or '~/.profile'.  
```
$ vim ~/.bash_profile
```

Restart the computer and you should now have a console mode login. If you login as the user you followed these steps with it will start fluxbox as soon as you log in. Please let me know if I made any mistakes, or if there is just a better way to do this. 

An alternative would be to put "*startx ~/.fluxbox/startup*" in your ~/.bash_profile instead of using the .xinitrc file. Both ways seem to work fine.

**Logout?**
I don't know how to get it to logout yet. When I click on exit in fluxbox or press ctrl-alt-backspace it just drops me back into the console and leaves me logged in.

---

### Post by energiya on 2007-07-09
You could further edit .bash_profile and make it automaticly startx only the first time (some bash scripting, shouldn't be that hard). I don't see how could disabling console help...

---

