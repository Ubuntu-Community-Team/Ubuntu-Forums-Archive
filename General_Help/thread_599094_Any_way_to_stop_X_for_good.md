---
title: "Any way to stop X for good?"
date: 2007-11-01
forum: General Help
---

### Post by Cojawfee on 2007-11-01
I am trying to stop X so I can install the nvidia drivers. No commands I can find on the internet seem to do anything. Gdm stop stops gnome, but I need X to stop.

Ctrl alt backspace stops X, but then Ubuntu decides to bring it back up for me. Killing the process does the same thing. Telinit 2 and 3 do nothing. With telinit 1, the driver wants me to compile a new kernel, which I obviously don't need to do. And telinit 2 or 3 again simply restarts X and brings me back to the login. 

I tried to use nvidia-glx but it doesn't recognize my video card (FX 5600). It also decides to tell me that it can't recognize my card every time i start up. So I am worse off than I was before I started. Not only am I getting a sluggish desktop with a few windows open, it's also 640x480 and it tells me that my video card doesn't exist when I boot up.

Is there ANY way to positively kill X and not have something start it back up for me? I searched these forums, nothing seems to work for me. I googled it and none of those things seem to work either. I just want to install drivers, why is Ubuntu working against me?

---

### Post by notatoad on 2007-11-01
does killall x do it?

---

### Post by Cojawfee on 2007-11-01
Just says "x: no process killed" I doubt it would work, as killing the pid just brought it back.

---

### Post by bingoUV on 2007-11-01
> **Cojawfee said:**
> I am trying to stop X so I can install the nvidia drivers. No commands I can find on the internet seem to do anything. Gdm stop stops gnome, but I need X to stop.

Ctrl alt backspace stops X, but then Ubuntu decides to bring it back up for me. Killing the process does the same thing. Telinit 2 and 3 do nothing. With telinit 1, the driver wants me to compile a new kernel, which I obviously don't need to do. And telinit 2 or 3 again simply restarts X and brings me back to the login. 

I tried to use nvidia-glx but it doesn't recognize my video card (FX 5600). It also decides to tell me that it can't recognize my card every time i start up. So I am worse off than I was before I started. Not only am I getting a sluggish desktop with a few windows open, it's also 640x480 and it tells me that my video card doesn't exist when I boot up.

Is there ANY way to positively kill X and not have something start it back up for me? I searched these forums, nothing seems to work for me. I googled it and none of those things seem to work either. I just want to install drivers, why is Ubuntu working against me?

```

sudo telinit 3

```

Your problem is that you are in runlevel 5 (which runs X whatever you do). The command above takes you to runlevel 3, where X is optional. Here you have to do a startx to launch X. To go back to runlevel 5, 
```

sudo telinit 5

```

---

### Post by Cojawfee on 2007-11-01
I've tried that. With a terminal while in Ubuntu, it does nothing. And I am running it as a super user. In a virtual terminal, it does nothing. X is still running when I do telinit 3. If I run telinit 3 and then kill the X process, it still starts back up. I've tried even going to the recovery console and then running telinit 3, it just starts X.

---

### Post by bingoUV on 2007-11-01
> **Cojawfee said:**
> I've tried that. With a terminal while in Ubuntu, it does nothing. And I am running it as a super user. In a virtual terminal, it does nothing. X is still running when I do telinit 3. If I run telinit 3 and then kill the X process, it still starts back up. I've tried even going to the recovery console and then running telinit 3, it just starts X.

Sorry, my age showing here. I am still holding on to old concepts. The init replacement (upstart) does not understand runlevels.

---

### Post by mikewhatever on 2007-11-01
Have you tried the recovery mode (usually the second boot option)? If I am correct, X never even gets started there.

---

### Post by Cojawfee on 2007-11-01
Ok, I finally figured it out.

I found out that Ubuntu is starting in runlevel 2. It has gdm loading in run level 2, so I simply removed gdm.

Restart, brings me to the terminal, with no X running. I install the driver, everything goes as planned. I copy S30gdm from from rc3.d back over to rc2.d and restart.

It loads up X and then once again says starts in low graphics mode saying it can't recognize my FX 5600. So now I am back to where I was in the first post. I don't understand why I can't get the drivers to just work properly. I got everything working in 6.06, don't remember what I did though.

---

### Post by ruibernardo on 2007-11-01
To stop Gnome/Xorg logout from your session, press alt+ctrl+F1, login on that tty console and then type:

```
sudo /etc/init.d/gdm stop
```For KDE (kubuntu) do the same thing but on the console type:

```
sudo /etc/init.d/kdm stop
```Note that you must logout (so that you don't loose any data) and you must do this on a tty console (alt-ctrl+F1), not from a terminal on Gnome.

---

