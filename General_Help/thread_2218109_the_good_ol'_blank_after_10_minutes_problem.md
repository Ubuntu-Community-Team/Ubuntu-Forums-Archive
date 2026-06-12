---
title: "the good ol' blank after 10 minutes problem"
date: 2014-04-19
forum: General Help
---

### Post by nLpPyXR on 2014-04-19
I'm on Lubuntu (core) 14.04, installed over the Trusty Tahr Ubuntu mini.iso...

Back when I was running 13.10 I had to install xscreensaver and add it to autostart just so this wouldn't happen. Currently I've tried adding "xset -dpms" and "xset s off" to autostart, finding the xorg.conf file (which I didn't find), and I've looked into editting the .bashrc file though I don't know how.

I adore Linux, Ubuntu, Lubuntu and Trusty Tahr, but this problem has been around since I shifted permanently to Nix and it's very annoying to have to install xcreensaver just so it doesn't happen.

Please, someone give me a real, permanent solution.

---

### Post by 23dornot23d on 2014-04-19
I found someone had written a script to stop it doing that here ......

[http://ubuntuforums.org/showthread.php?t=2183646](http://ubuntuforums.org/showthread.php?t=2183646)

There are a lot of answers on askubuntu too ..... 

[http://askubuntu.com/questions/171143/how-to-prevent-my-screen-from-either-dimming-or-the-screen-lock-starting-when-wa](http://askubuntu.com/questions/171143/how-to-prevent-my-screen-from-either-dimming-or-the-screen-lock-starting-when-wa)

but from what I have read some of them seem not to work in later versions of ubuntu ..... 
but the first link I posted worked in 14.04 when I last used it.

---

### Post by mikewhatever on 2014-04-19
Does Lubuntu core contain stuff like lightlocker or xfce4-power-manager? Both have settings to turn the screen off.

Well, **.bashrc** is a hidden file inside your home - note the . in front. Hidden files can be revealed by **ctrl-h**, then you just open it with a text editor (leafpad by default), edit, save and exit.

---

### Post by mikewhatever on 2014-04-19
> **23dornot23d said:**
> I found someone had written a script to stop it doing that here ......

[http://ubuntuforums.org/showthread.php?t=2183646](http://ubuntuforums.org/showthread.php?t=2183646)

...

Hm.., lots of gsettings there. Is it going to work on Lubuntu?

---

### Post by 23dornot23d on 2014-04-19
Its something that works on mine - and it switches screensaver mode on and off ..... 

I just tried it again on my own system and its working ..... but as you say ..... gsettings ( gnome-settings )

I have lots more things installed to do with gsettings ...... than the user probably has ..... so I cannot test
it out properly ...... there are the other links to askubuntu though to check out as well ...... but its only a script
if it works all well and good ......... if it does not then it was just a matter of cutting and pasting it 
into a 

[B]gedit screen.sh

chmod u+x  screen.sh

./screen.sh[/B]

if run like this it just toggles the screensaver on and off ...... or you can specify on or off.

I am getting 2 warnings though that its not finding things ......

```

keith@keith-K53SV:~$ ./screen.sh

-on or -off not specified: will toggle power savings mode.

Switching on power saving mode
No such key 'idle-dim-ac'
No such key 'idle-dim-battery'

keith@keith-K53SV:~$ ./screen.sh

-on or -off not specified: will toggle power savings mode.

Switching off power saving mode
No such key 'idle-dim-ac'
No such key 'idle-dim-battery'

keith@keith-K53SV:~$ ./screen.sh

-on or -off not specified: will toggle power savings mode.

Switching on power saving mode
No such key 'idle-dim-ac'
No such key 'idle-dim-battery'

keith@keith-K53SV:~$ ./screen.sh

-on or -off not specified: will toggle power savings mode.

Switching off power saving mode
No such key 'idle-dim-ac'
No such key 'idle-dim-battery'

keith@keith-K53SV:~$ ./screen.sh

-on or -off not specified: will toggle power savings mode.

Switching on power saving mode
No such key 'idle-dim-ac'
No such key 'idle-dim-battery'

keith@keith-K53SV:~$ ./screen.sh

-on or -off not specified: will toggle power savings mode.

Switching off power saving mode
No such key 'idle-dim-ac'
No such key 'idle-dim-battery'

I did a small video of it working but it is hard to show when something
is making a difference or not ... also looked at the wallpaper changer
as that might do the same thing ..... but that did not work at all for me.

There is a updated script in the thread further down too that runs better than the first one

K53SV:~$ ./screen2.sh

-on or -off not specified: will toggle power savings mode.

Switching on power saving mode

keith@keith-K53SV:~$ ./screen2.sh

-on or -off not specified: will toggle power savings mode.

Switching off power saving mode


```

---

### Post by ibjsb4 on 2014-04-19
Xfce4-power-manager (6M download) is part of lubuntu-desktop, but not included in a lubuntu-core install.

[ATTACH=CONFIG]252256[/ATTACH]

---

### Post by nLpPyXR on 2014-04-19
> **23dornot23d said:**
> I found someone had written a script to stop it doing that here ......

[http://ubuntuforums.org/showthread.php?t=2183646](http://ubuntuforums.org/showthread.php?t=2183646)

There are a lot of answers on askubuntu too ..... 

[http://askubuntu.com/questions/171143/how-to-prevent-my-screen-from-either-dimming-or-the-screen-lock-starting-when-wa](http://askubuntu.com/questions/171143/how-to-prevent-my-screen-from-either-dimming-or-the-screen-lock-starting-when-wa)

but from what I have read some of them seem not to work in later versions of ubuntu ..... 
but the first link I posted worked in 14.04 when I last used it.

not working for me :(

> **mikewhatever said:**
> Does Lubuntu core contain stuff like lightlocker or xfce4-power-manager? Both have settings to turn the screen off.

Well, **.bashrc** is a hidden file inside your home - note the . in front. Hidden files can be revealed by **ctrl-h**, then you just open it with a text editor (leafpad by default), edit, save and exit.

Oh I know where .bashrc is located and how to edit it, what I mean is when someone types "add this and that to .bashrc" they never say if one should add it at the very beginning, or after the "fi" bit in the very last line...

and no, Lubuntu-core doesn't have lightlocker nor xfce4-power-manager: [http://packages.ubuntu.com/trusty/lubuntu-core](http://packages.ubuntu.com/trusty/lubuntu-core)

> **ibjsb4 said:**
> Xfce4-power-manager (6M download) is part of lubuntu-desktop, but not included in a lubuntu-core install.

[ATTACH=CONFIG]252256[/ATTACH]

If downloading that fixes it for sure, I'd do it in a heartbeat, but I remember the XFCE PM came with Lubuntu Desktop 13.10 by default and it didn't prevent the screen from going blank after 10 minutes no matter what its settings were.

----------------------------------------------------------------------------------------------------------------------------------------------------

there's a mysterious file in my home folder called .xscreensaver despite the fact that I certainly never installed XSS, nor is it in the included packages of Lubuntu-core. Inside it reads "mode: blank".

---

### Post by ibjsb4 on 2014-04-19
Changing the power manager settings to 'never', works for me (no screen saver installed).

---

### Post by nLpPyXR on 2014-04-20
> **ibjsb4 said:**
> Changing the power manager settings to 'never', works for me (no screen saver installed).

downloaded and tried xfce4-pm...

no dice, just like in 13.10.

You'd think there'd be a better way than having to forcefully install xscreensaver :-?

---

### Post by mikewhatever on 2014-04-23
> **nLpPyXR said:**
> 

Oh I know where .bashrc is located and how to edit it, what I mean is when someone types "add this and that to .bashrc" they never say if one should add it at the very beginning, or after the "fi" bit in the very last line...



The end of file is usually the safest place.

---

