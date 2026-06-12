---
title: "strange graphics on screen"
date: 2007-05-03
forum: General Help
---

### Post by marmiteOlz on 2007-05-03
ok  where do i start....

i installed ubuntu 7.04 using wubi
all installed  fine...
upon restart i got a fail on the fat block.. i can get exact name if it helps..

it continued anyway but this is where it goes wrong
i get the following image as my login screen [click for login image ]("http://www.samward.pwp.blueyonder.co.uk/images/login.JPG")
i have installed ubuntu 6.06  some time ago trying out linux  until my hard drive failed lol... so i know this was the login screen
so i typed my username  then tabbed  then password and was greeted with a slightly different screen image
[click for desktop image]("http://www.samward.pwp.blueyonder.co.uk/images/desktop.JPG")

i heard a sound after i entered my details and pressed enter  but i didnt have my headphones on.. i presume it was the welcome sound  similiar to xp greets u with

 as i said  months ago ( when i regged to these forums  if u after a exact date) i installed 6.06 from a live cd and it ran fine..
IF.... i select safe graphics ( i think was long ago)
then when i installed nvidia drivers  using automatix it was fine
but.. when i tried not using safe graphics it gave the same screen image as i posted above
i also tried 6.10 and had the same graphics  error as 7.04 and 6.06 non safe graphics

i would love to get linux running and swap from ms as checking out cedega site i can get the games i play running ( more hard work i guess lol)
and if its possible i want to do it...
using wubi   gives me the dual boot option without me destroying anything from windows as i have  a destructive set of fingers lol
any help would be much appreciated

---

### Post by vav on 2007-05-03
When you get to the login screen, press Ctrl+Alt+F2
This should get you to a text login. Login with your username.
Do this:
```

cp /etc/X11/xorg.conf ~/

sudo dpkg-reconfigure xserver-xorg

```
The first step will backup your old configuration to your home directory.
You'll then be prompted for your password, or for root's password. Enter whats requested.

This should get you to a few ascii-graphics screens which let you configure your graphical environment. After you're done, type
```

sudo reboot

```
The next time it should boot properly and show you your login screen...

---

### Post by marmiteOlz on 2007-05-04
hmm tried the first line  and it said no such file or directory
i did a cd /etc.... that was ok
then did cd /x11     then it said couldnt not find it    and froze

ill try a reinstall  knowing me i screwed something up lol
if no joy ill get a spare hard drive and do it on that from fresh
thanks for the help tho

---

### Post by marmiteOlz on 2007-05-04
nope tried reinstall and no joy
same result  no such file or directory

---

### Post by klytu on 2007-05-04
> **marmiteOlz said:**
> hmm tried the first line  and it said no such file or directory
i did a cd /etc.... that was ok
then did cd /x11     then it said couldnt not find it    and froze

ill try a reinstall  knowing me i screwed something up lol
if no joy ill get a spare hard drive and do it on that from fresh
thanks for the help tho

That should be a capital "X" in X11. It makes a difference; Linux is case-sensitive. Make sure you typed the command EXACTLY as it appeared in the previous post by VAV.

---

### Post by marmiteOlz on 2007-05-04
thanks for the  typo in my part  i printed off teh commands and the printer doesnt really make it easy to see the uppercase :(
anyway i tried  and all went accordingly
until  i came to the very end..
i rebooted but still the same
the only variation i tried was the keyboard layout,, just in case
it finds my graphics card fine ( nv 6800)

anyone know if wubi can be used with dapper drake as that run ok on mine before ( before hard drive died lol)

---

### Post by marmiteOlz on 2007-05-19
k i got ubuntu running again on my system
tried old drive and its running ok again.. odd  strange noise now n again but thats ok lol

---

