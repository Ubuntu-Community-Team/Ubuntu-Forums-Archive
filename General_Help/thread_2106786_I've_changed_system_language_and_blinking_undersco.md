---
title: "I've changed system language and blinking underscore has appeared"
date: 2013-01-20
forum: General Help
---

### Post by yaapelsinko on 2013-01-20
My system is that -  Core i5, P55A-UD3R, Radeon HD 6970, 12GB ram.

I've installed Ubuntu 12.10, updated and upgraded it to the limit.
Then installed some software, etc, rebooting several times, and all was working fine for a day (except that ubuntu often can't reboot by itself after any system changes - it just suspending on the shutdown screen with 4 white dots and 1 red - so I have to push reset).

Then I've decided to change system language for my user account. So, I did it, reboot (again it suspends, I've pushed reset) aaaand here he go - blinking underscore on the screen.

System is working, but I have that 'underscore' in front of any window on the screen.
It doesn't look like actual underscore, it just a many periodic small black dashes in specific area (narrow line near the top) on the screen, and two of them blinking gray.

The only thing I've changed before that is user account's language. Before that I was working about a day without any system reconfigurations, have several reboots without any problems.

All I've found about 'blinking underscore' for this moment is only relating intel GMA bugs and somewhat about installation and boot. Which is probably not my case.

I've installed/reinstalled latest AMD drivers - didn't helped.

'nomodeset' solution also didn't work, if it ever have to.



Any solutions? :confused:

---

### Post by yaapelsinko on 2013-01-20
Ok, I've found an 'workaround', but it's not the solution.

After boot (underscore is blinking), I logging in (it's still blinking).
Then I logging out - and it's gone.
Logging in again and have not any dashes, lines, underscores and other trash on the screen.

But I have to do all this ritual after every reboot.

Again, it's not the solution, but may be it give idea to somebody what the real problem is?

---

### Post by Impavidus on 2013-01-20
When you log off X is restarted. It seems X is unable to start properly the first time, but manages the second time. It could be related to not properly shutting down. Have you tried first logging off and then shutting down? It asn't a solution, but it might give you a clue.

---

### Post by rnerwein on 2013-01-20
> **yaapelsinko said:**
> Ok, I've found an 'workaround', but it's not the solution.

After boot (underscore is blinking), I logging in (it's still blinking).
Then I logging out - and it's gone.
Logging in again and have not any dashes, lines, underscores and other trash on the screen.

But I have to do all this ritual after every reboot.

Again, it's not the solution, but may be it give idea to somebody what the real problem is?
hi
you are right to say it's no solution. the error is still there. try following with your workaround. on the login-screnn change to a console-window (CTRL+Alt+F1) then login and have a look in ~/.xsession-errors may you can find some errors you can interpret. i know that's no solution but may be a way to figure out what's going on.
good luck
ciao

---

### Post by yaapelsinko on 2013-01-20
I've tried open terminal (ctrl+alt+f1) after boot, but it seems that terminal does not work while 'blinking underscore' is present. But it became clear that 'underscore' is actually underscore - it's just terminal/keyboard input, that somehow getting into graphic 'surface'. After trying to open terminal that underscore became movable and clearly reflecting keyboard input.

So, i can't provide errors just after boot, but can do reboot and login log, and then clear it and make logout (when X restarts) log. I've attached two files. Some errors are in russian, so i  translated it. The only unclear thing there, you'll see, '[Victory or Win?]'. There is '&#1055;&#1086;&#1073;&#1077;&#1076;&#1072;' in log - that seems like incorrect russian localization, Victory or Win are two ways to translate it back to english, and i have no idea what that means (well, words meaning is clear, of course, but...).

Maybe someone can get any idea from this? Because I can't. :confused:

---

### Post by yaapelsinko on 2013-02-08
It's a joke or what?
 
As nobody knows about that glitches decribed, I decided to install 12.04.
No system reconfigurations at all, just installed, updated, downloaded some programms and working with it.
 
But, as I believe, those who making updates and putting them to update center, so I bravely installing any offered updates.
 
First, after another update, that glitches are returned. Funny, now I had to login twice, as first time screen just blinking and returning me to login screen again. But, at least I was able to work without any trash on screen after second one.
 
And finally, after last update (hey! there is some updates of x.org! defenitely i'm not the only with that problem, may be they already made some fix!) Ubuntu is loading in 'low graphic mode', offers to some useless debugging options and also offers to finally load and work in that 'low graphic mode'. It offers but it don't loading. It just suspends at some stage, and only I can do is to switch between consoles. 
 
What. The. Hell?

---

