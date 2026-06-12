---
title: "Wine hell"
date: 2007-06-04
forum: General Help
---

### Post by blueyelabs on 2007-06-04
Wine is absolutely killing me; three problems:

[HISTORY]
Basically, I installed the newest wine on the 3rd (yesterday) whichever the newest is, and I was pretty darn excited, have to say. Basically this is an old machine with a partitioned drive, part win98se part Xubuntu. It is not all that powerful, but it can actually run most older games (eg Black and White, Red alert 2, age of empires 2, rise of nations + expansion etc).
Problem is, the games (for some unknown reason) just won't start on the windows side, and ever since I've been trying to get this Xubuntu partition running fully.
I also managed to install the nVidia glx legacy drivers for the geforce ti 4200 on here, and that (eventually) worked.
[END HISTORY]

So, after I got wine working, I tried to install black and white (love that game) and the install worked damn well. Then I realised that this partition didn't really have enough space on it so I tried changing the "C:\" section in winecfg. Only then did I think "damn, now I can't uninstall B&W" but I solved that and (also eventually) found the .wine dir.

However, now I can't uninstall anyway (I get the message:
[COLOR="Red"]"The InstallShield Engine (iKernel.exe) could not be launched
(0x80070002)"[/COLOR]

So I look around, and find nothing, that's the first problem.

Second problem is that I found a no-cd crack for B&W (otherwise it wouldn't work, even if I ran it from the CD ("unload the debugger and then continue" or some such annoyance).
When I tried to run the game, the first time it killed me and crashed Xubuntu and all I got was a lousy black screen and game music. I had to ctrl+alt+F1 and restart the X-server.
I got it to work once, when the load screen and music all worked fine but then I could never again. I just get a black screen, and then eventually the "enter your name" box, but loads of things don't work, it's really jerky and well, it just doesn't work: keeps going back to a black screen.
Other games fail as well. "The Settlers IV" shows the right splash screen, but then the start video disappears, the window resizes itself three or four times and then I get a weird 1/2 screen where the mouse is out of place and nothing works properly.

I don't know where to turn, help would be very much appreciated (and if you got this far I congratulate you on having patience).
Also, please not TOO much linux-tech jargon, I'm relatively new to it.

---

### Post by benmoreassynt on 2007-06-04
Have you looked at [www.winehq.org?](www.winehq.org?) Do a search for the games you are interested in and see what it says, and if there is specific advice for the game and/or Xubuntu.
 
If you expect stuff to 'just work' with Wine, you are likely to be very dissapointed I'm afraid. It is a rough and ready way to get Windows apps working under Linux at the best of times. Why won't they work on the Windows partition?

---

### Post by Robin T Cox on 2007-06-04
See:

[http://frankscorner.org/]("http://frankscorner.org/")

---

### Post by stchman on 2007-06-04
> **blueyelabs said:**
> Wine is absolutely killing me; three problems:

[HISTORY]
Basically, I installed the newest wine on the 3rd (yesterday) whichever the newest is, and I was pretty darn excited, have to say. Basically this is an old machine with a partitioned drive, part win98se part Xubuntu. It is not all that powerful, but it can actually run most older games (eg Black and White, Red alert 2, age of empires 2, rise of nations + expansion etc).
Problem is, the games (for some unknown reason) just won't start on the windows side, and ever since I've been trying to get this Xubuntu partition running fully.
I also managed to install the nVidia glx legacy drivers for the geforce ti 4200 on here, and that (eventually) worked.
[END HISTORY]

So, after I got wine working, I tried to install black and white (love that game) and the install worked damn well. Then I realised that this partition didn't really have enough space on it so I tried changing the "C:\" section in winecfg. Only then did I think "damn, now I can't uninstall B&W" but I solved that and (also eventually) found the .wine dir.

However, now I can't uninstall anyway (I get the message:
[COLOR="Red"]"The InstallShield Engine (iKernel.exe) could not be launched
(0x80070002)"[/COLOR]

So I look around, and find nothing, that's the first problem.

Second problem is that I found a no-cd crack for B&W (otherwise it wouldn't work, even if I ran it from the CD ("unload the debugger and then continue" or some such annoyance).
When I tried to run the game, the first time it killed me and crashed Xubuntu and all I got was a lousy black screen and game music. I had to ctrl+alt+F1 and restart the X-server.
I got it to work once, when the load screen and music all worked fine but then I could never again. I just get a black screen, and then eventually the "enter your name" box, but loads of things don't work, it's really jerky and well, it just doesn't work: keeps going back to a black screen.
Other games fail as well. "The Settlers IV" shows the right splash screen, but then the start video disappears, the window resizes itself three or four times and then I get a weird 1/2 screen where the mouse is out of place and nothing works properly.

I don't know where to turn, help would be very much appreciated (and if you got this far I congratulate you on having patience).
Also, please not TOO much linux-tech jargon, I'm relatively new to it.

You sould only need the legacy drivers for GeForce 2 or older cards.  I installed Edgy on my brother's PC which has a GF3 ti200 and it works great with the newer drivers (87.55).

---

### Post by blueyelabs on 2007-06-05
> **stchman said:**
> You sould only need the legacy drivers for GeForce 2 or older cards.  I installed Edgy on my brother's PC which has a GF3 ti200 and it works great with the newer drivers (87.55).
I originally installed the new drivers from the ubuntu repository... they didn't work to put it simply.

then after some searching I found the drivers off the Nvidia website [COLOR="Red"][Nvidia-Linux-x86-1.0-9639-pkg1.run][/COLOR] and they work fine.

---

### Post by blueyelabs on 2007-06-05
> **benmoreassynt said:**
> Have you looked at [www.winehq.org?](www.winehq.org?) Do a search for the games you are interested in and see what it says, and if there is specific advice for the game and/or Xubuntu.
 
If you expect stuff to 'just work' with Wine, you are likely to be very dissapointed I'm afraid. It is a rough and ready way to get Windows apps working under Linux at the best of times. Why won't they work on the Windows partition?
I don't necessarily just *expect* apps to work, it'd be nice though wouldn't it ;)

nah, I understand that Microsoft is hardcore in to all that proprietry stuff... hard to deal with sometimes...

I don't really understand why the apps don't work in windows, mostly they just freeze as soon as the game starts, but weird stuff also happens, sometimes they just don't start.

---

### Post by blueyelabs on 2007-06-05
> **benmoreassynt said:**
> Have you looked at [www.winehq.org?](www.winehq.org?) Do a search for the games you are interested in and see what it says, and if there is specific advice for the game and/or Xubuntu.
 
If you expect stuff to 'just work' with Wine, you are likely to be very dissapointed I'm afraid. It is a rough and ready way to get Windows apps working under Linux at the best of times. Why won't they work on the Windows partition?
ooo and I just checked, and it appears that there are problems :(

oh well...
I'll just try a different game.

---

