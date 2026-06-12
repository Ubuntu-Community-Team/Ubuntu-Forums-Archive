---
title: "BLACK bar at top of docky screen?"
date: 2014-05-25
forum: General Help
---

### Post by cmar6062 on 2014-05-25
Hello,

Just installed LUBUNTU 14.04 about 30 min ago. 

I installed docky and ran the command to get compositing to work but when logging into Lubuntu 14.04 I have this black bar at the top of the screen when docky loads at log in.. I am stumped on how to make it go away besides open and close docky when I need it / dont need it?

Any ideas?

Thanks,
Christopher



steps I took:
christopher@COMPAQ:~$ gksudo leafpad ~/.config/lxsession/Lubuntu/autostart

That didnt work :( to add the composting to start up and docky. 

but adding the @xcomp command to startup did get the composting to load at start and its working fine its not nagging me saying it needs tha xcomp to run correctly just this black bar is annoying.

---

### Post by bapoumba on 2014-05-25
[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1247118)
There is a bug where the autostart applications never autostart.
You can manually add it to Prefs > Default Apps > Autostart tab.

---

### Post by cmar6062 on 2014-05-25
Oh cool.... Now if I can just figure out the black shadow thing id be good! lol

Merci Becoup! ( sorry about the spelling lol)

---

### Post by bapoumba on 2014-05-25
De rien (you are welcome) :)
Not using docky, I had a look at their page. Maybe the theme you are using ?

---

### Post by cmar6062 on 2014-05-25
im using the default lubuntu theme just got done installing it almost 2 hours ago.

---

### Post by bapoumba on 2014-05-25
Then maybe a screenshot could help others give input :)

---

### Post by cmar6062 on 2014-05-25
[IMG]http://i886.photobucket.com/albums/ac69/CMAR606/LUBUNTU/2014-05-25-121358_1280x1024_scrot.png[/IMG]

---

### Post by Robbyx on 2014-08-11
Were you able to clear the  black band? I have got it as well.

R

---

