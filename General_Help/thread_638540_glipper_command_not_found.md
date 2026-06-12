---
title: "glipper: command not found??"
date: 2007-12-12
forum: General Help
---

### Post by RobotJox on 2007-12-12
erh...I'm a bit confused...

I installed Glipper through synaptic, but I get this message when I try to run it:

The program 'glipper' is currently not installed.  You can install it by typing:
sudo apt-get install glipper

but, I have installed it.........

I then tried to install it from source, which went great....except...it's nowhere to be found. I get the same error, and it is not in the accessories menu, where it should be....

There's also no /usr/bin/glipper

any ideas? 

I'm on Gutsy

thanks!

---

### Post by r-mo on 2007-12-12
I  just installed it through synaptic and it works fine.

If you compile from source it will probably be in /usr/local/bin after you "sudo make install" unless you asked for it to go elsewhere

---

### Post by RobotJox on 2007-12-12
well, it's not there either... this is really weird - what can have caused this behaviour?

I did find the program installed here: /usr/share/glipper

and I can launch it with ./glipper:

SHARED_DATA_DIR: /usr/share/glipper
Binding shortcut <Ctrl><Alt>C to popup glipper
Running with options: {'standalone': False}

but there's no icon in my menus or my quick launch panel.

Maybe some old files conflicting? What's the best way to erase any references to the program and start fresh?

thanks

---

### Post by cmfrtblynmb on 2008-05-04
I have te same problem

Clipper  does not work for me neither, with exactly the same reasons that you have written

---

### Post by cmfrtblynmb on 2008-05-04
OK, I found sth that soved my problem

check this one

[https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/179148/comments/4](https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/179148/comments/4)

---

### Post by lofftjm on 2008-07-16
This is still an issue...has anyone found a workaround?

---

