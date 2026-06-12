---
title: "joy2key, rejoystick, qjoypad, etc"
date: 2008-03-28
forum: General Help
---

### Post by psychofish25 on 2008-03-28
I have been frantically searching all over the internet in order to use my Rock Band drums with hydrogen. To do this, I need to convert hitting a drum into pressing a key. I realize I can use one of the mentioned programs, but no where on the internet can I find how. Nothing seems to work for me at all and it's becoming extremely frustrating. Could somebody please just tell me how get this thing to work. 

Thanks,
Jordan

---

### Post by samel_tvom on 2008-03-31
The first you need to do if you think you can use any of joy2key, rejoystick, qjoypad etc. is to find out if your Rock Band drums will show up (or rather, act) like a joystick. Otherwise you're out of luck with those programs.

So, the drums will show up as a joystick if /dev/input/js0 (or js1, js2, etc or something) or /dev/js0 exists. So, open a terminal and enter
```
test -e /dev/input/js0 && echo exists
```
alternatively
```
test -e /dev/js0 && echo exists
```
If you get the output "exists" then it exists. (Or you could check in the /dev/input or /dev dir)

If it exists then there shouldn't be any problems with either of the programs. I would recommend qjoypad or rejoystick though since joy2key is a bit messy to configure. Qjoypad is written in qt (as is KDE) and rejoystick is written in gtk (as is GNOME).

Otherwise, try the following, open up a terminal and enter
```
xev
```
Then play the drums. If you're lucky they'll generate key codes. In that case try to simply keybind them. 

In GNOME you could use the "System" menu and find the sub menu "Properties" (or something, mine is in swedish right now) and try to find "key shortcuts" or something. I don't know how you should do with KDE.  Anyways, you could always try with openbox; [http://icculus.org/openbox/2/](http://icculus.org/openbox/2/) That site will also explain how you should do to integrate openbox (which is a window manager) with KDE or GNOME. It's a little harder to configure keys with though, I think you have to edit some text files. Try with ordinary buttons that really will work first so you get a hang of keybinding. Like, try to keybind F10 or Pause or something to open up a terminal or whatever.

If neither works, I really don't know. Anyway, let us know!

---

### Post by begemot. on 2008-05-08
**samel_tvom**
Thank You! Your post made my situation much more clear.
But, unfortunately, my case is exactly "unlucky" (:
I mean, i have no /dev/js* or /dev/input/js* files and "xev" output gives nothing.

I have made a solder of my "Sega Genesis" joystick to LPT-port connection following by this schema called "Linux":
[IMG]http://www.geocities.com/deonvdw/Docs/Diagrams/Sega/SegaLinux.gif[/IMG]

And now i have something looks like this:
[IMG]http://tehnik.kv71.ru/gamesystem/pictures/genesis/006.jpg[/IMG]

And this crazy device works perfect in windows (tested with "xyzmodeb" driver). But i used exactly "Linux" schema to make it works in OS Linux, of course.

I found a driver with unambiguous name "[Linux Joystick Driver]("http://atrey.karlin.mff.cuni.cz/~vojtech/joystick/")", but i can't realize - will it works with that connection-schema?!

Maybe, You can give me advice?
Many thanks.

---

### Post by samel_tvom on 2008-05-08
Hi!

Sorry, can't help you there. If your gamepad isn't supported by the generic joystick driver in linux, you're out of luck since I think SDL uses that driver only (not sure though) to interface the joystick.

Sorry :(

---

### Post by begemot. on 2008-05-08
It's so sad...
But why than the author of this connection schema called it "Linux"???
I think there must be a way to make it works.

---

### Post by begemot. on 2008-05-12
I did it! (:
This [document]("http://www.mjmwired.net/kernel/Documentation/input/joystick-parport.txt") reached me in hardware sphere and certify me that this connection schema "Linux" is absolutely right. And that [advice]("http://ubuntuforums.org/showthread.php?t=61745") gave to me exactly what i have been searching for about "/dev/input/js*".

And i found [rejoystick]("http://rejoystick.sourceforge.net/") tool the most useful among others, cuz it has friendly GUI for configuring and nice deb-package is available.

---

### Post by bhuthogg on 2008-05-25
> **begemot. said:**
> I did it! (:
This [document]("http://www.mjmwired.net/kernel/Documentation/input/joystick-parport.txt") reached me in hardware sphere and certify me that this connection schema "Linux" is absolutely right. And that [advice]("http://ubuntuforums.org/showthread.php?t=61745") gave to me exactly what i have been searching for about "/dev/input/js*".

And i found [rejoystick]("http://rejoystick.sourceforge.net/") tool the most useful among others, cuz it has friendly GUI for configuring and nice deb-package is available.

i have been trying rejoystick but its as if the program is closing when i try to use the analogue sticks 

ant ideas?

---

