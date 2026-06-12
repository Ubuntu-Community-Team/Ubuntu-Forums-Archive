---
title: "How can I lock/unlock keyboard on mouse gesture?"
date: 2008-06-24
forum: General Help
---

### Post by Cygoku on 2008-06-24
I recently bought a cat, it's 8 weeks old and it walks on keyboards at night.  This morning I woke up with a computer playing 97 video at the same time and one afternoon, after work Megadeth was playing at loudest volume.  Baby upstair couldn't do his afternoon sleep.  

There is less chance that my cat would do a mouse gesture before starting to play with the keyboard.  Is there anyway I can lock and unlock keyboard with a mouse gesture?

TIA

Cygoku

[IMG]http://bp0.blogger.com/_DY3YhPwA0lI/R9Kf4xFdwrI/AAAAAAAAATM/A4hdbDRXsqk/s1600-h/computer-blue-screen-death.jpg[/IMG]

---

### Post by iaculallad on 2008-06-24
What about pressing Ctrl+Alt+Del key and selecting "Lock Screen" when leaving your System turned on so that any key pressed and mouse movement/click won't affect your system?

---

### Post by molotov00 on 2008-06-24
I'm intruiged but this one. It's a cool idea. Here's what I Found:

[http://ubuntuforums.org/archive/index.php/t-146100.html](http://ubuntuforums.org/archive/index.php/t-146100.html)

> Get xbindkeys and xbindkeys-config (apt can get both of those, they're in the universe repositories)

3. Start xbindkeys and then xbindkeys-config, that will bring up a GUI and you can add a new one or modify the pre-existing ones. Set a name... the Action to "xscreensaver-command -lock" then click "Save & Apply & Exit" ...

Note the command to lock ;) 'xscreensaver-command -lock' you may need to install it (sudo apt-get install xscreensaver)

Then... it looks like this is a tutorial to install mouse gestures:
[http://www.ubuntugeek.com/gestikk-mouse-gesture-recognition-in-ubuntu.html](http://www.ubuntugeek.com/gestikk-mouse-gesture-recognition-in-ubuntu.html)

If I were you I'd just set a shortcut like CTRL+L to lock or something. The first link is a little dated. Experiment with your version to see if there is a similar 'keybind' feature already there, without installing some of the packages.

---

### Post by Cygoku on 2008-06-24
Thanks for your advice, but I forgot to mention that I would also like to be able to watch a movie while the keyboard is lock.

Cygoku

---

### Post by Cygoku on 2008-06-24
*bump*

Cygoku

---

### Post by rubicon on 2008-06-24
Do you have a USB keyboard or is it PS/2 one? USB keyboards are safe to hot-plug :D

---

### Post by molotov00 on 2008-06-24
Then what you really want to do is temporarily disable the keyboard, not lock/unlock.

It's a stupid request because then you leave your computer crippled unless you can 'enable' it again. Now, you can use a mouse gesture as you've indicated but if it goes to sleep or does something else unexpected you'll be stuck booting into recovery mode. But I'm not even sure that will work properly because you've pro-actively disabled a keyboard. You might have to hook another one up or switch ports.

Either way, here's the best description I could find about how to disable keyboards. Ignore that it's dealing with laptops.

[http://sudan.ubuntuforums.com/showthread.php?t=725199](http://sudan.ubuntuforums.com/showthread.php?t=725199)

You'd have to write a script to disable/enable the keyboard then have your mouse gesture program call that. It's certainly possible but I wouldn't recommend it. Also, this isn't a Ubuntu thing. This is a very strange request and the only way to disable the keyboard in Windows is to get into the registry, as far as I know. You're dealing with a pretty low level device -- there aren't options in driver apps.

---

