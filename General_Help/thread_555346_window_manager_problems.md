---
title: "window manager problems?"
date: 2007-09-20
forum: General Help
---

### Post by eclectic4 on 2007-09-20
I'm running Feisty with the Gnome desktop and Metacity window manager.  I also have Beryl installed and am using it most of the time. 

Something seems to be wrong with the gui when Beryl is not running, so I guess that means Medacity?

When the system starts up, or if I restart X, there are no title bars on any windows, and the workspace switcher I have in my bottom toolbar appears as a single line instead of a row of squares, and does not respond.  This is without Beryl running.  When I start up Beryl, everything runs fine.  If I use the Beryl Manager menu to switch back to Metacity, then Metacity has title bars and the workspace switcher works.

I cannot get Beryl to be my default window manager, which is my usual preference.   I go to System>Preferences>Sessions>New, add Beryl with beryl-manager, click OK, Close, and when I go back there to check, there is no sign of Beryl.  It will not save the change, and Beryl never starts up with Gnome.

I have tried using Synaptic to reinstall (guessing) gnome-panel and Metacity, at least, and it has not helped.

---

### Post by eclectic4 on 2007-09-20
sheesh, last night I posted about another problem in the evening and got so many quick responses it was like a party.  Maybe posting at 2:00 am est is not the best.  Anyway, this post here is a shameless attempt to see if it moves this thread back to a more visible spot on the site :)

---

### Post by eclectic4 on 2007-09-20
Now more and more is going wrong.  The problems described above were fairly stable, but after doing nothing other than what I described there and switching rapidly between window managers last night to test the problem before posting, I've got more problems.

When I click to open desktop icons, or menu links such as Places>Home, which open with Nautilus, the window often comes up blank, with no files or folders showing.  

After restarting X, my Desktop icons are all rearranged and I can not move them.

Often but not always, other program windows, such as System Monitor, will come up as frames with no content.

Please help me!!!

---

### Post by glantucan on 2007-09-26
I've got the same problem as you, but it didn't get worst as you said in the las post. 
So I'm glad to say you are not alone. But, though I'm working on it, I'm afraid I didn't get any solution yet :(

---

### Post by glantucan on 2007-09-26
Ok, it seems there is a permissions issue with the /home/<username>/.config/autostart directory. 
See [http://ubuntuforums.org/showthread.php?t=470411](http://ubuntuforums.org/showthread.php?t=470411)

```
sudo chmod 777 /home/<username>/.config/autostart
```

the password sudo asks for is your password you use to login.

where username is your home directory. (ex. /home/xang/.config/autostart )


It worked for me

Glantucan

---

