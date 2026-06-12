---
title: "Run app in Virtualbox direct from linux"
date: 2007-03-14
forum: General Help
---

### Post by Matchless on 2007-03-14
Hi,
   Does anyone know how to run a windows application in Virtualbox directly from a menu icon in ubuntu? Instead of opening Virtualbox, then XP, then running the app.
Thanks

---

### Post by LotsOfPhil on 2007-03-14
It's in here using rdesktop

[http://www.ubuntuforums.org/showthread.php?t=361528](http://www.ubuntuforums.org/showthread.php?t=361528)

---

### Post by Matchless on 2007-03-16
Thanks, but not exactly what I am looking for. It seems as if rdesktop and seamlessrdp requires Virtualbox and XP to be running.
What I want to do is create a launcher that opens VirtualBox, then runs XP and then runs the required XP application, thus all after one mouse click in Ubuntu. Does anyone know if this is possible?

---

### Post by daengbo on 2007-04-25
> **Matchless said:**
> Thanks, but not exactly what I am looking for. It seems as if rdesktop and seamlessrdp requires Virtualbox and XP to be running.
What I want to do is create a launcher that opens VirtualBox, then runs XP and then runs the required XP application, thus all after one mouse click in Ubuntu. Does anyone know if this is possible?

The answer is that you can do it, but it will be painfully slow. You will need for VirtualBox to start, then boot XP, then start the program. I'm thinking over a minute, at least. 

You might be better off starting Virtualbox with the comman-line manager (in the background) and connect to it with RDP from the Ubuntu desktop.

---

### Post by qpwoeiruty on 2007-04-25
[http://cryopid.berlios.de/](http://cryopid.berlios.de/) would help alleviate the need to boot and shutdown Windows in VirtualBox every time you want to run it  It can pause process and save to disk: think hiberanate for a single process, and can restore it again later.

---

### Post by kyphi on 2007-04-27
In VirtualBox you have the option, when logging out, of "powering down" or "save the machime state".

If you use the latter, whatever programme you have open will be reloaded on startup in a matter of seconds.  Closing down that programme gets you back to Windows.

As to having to click only once to open your desired programme in VirtualBox, you will find an application launcher in Panels (right click on the top or bottom panel, add to panel and use one of the "application launchesr").

That should do it.

---

### Post by Matchless on 2007-04-30
Thanks, This should work and I will try it as soon as Ii have completed the new Feisty install. I really just want to run Quickbooks and nothing else, so the 'hibernation' type approach should not be a problem unless I close it down as per habit.
Thanks again.

---

### Post by ezramorris on 2008-03-26
> **Matchless said:**
> Hi,
   Does anyone know how to run a windows application in Virtualbox directly from a menu icon in ubuntu? Instead of opening Virtualbox, then XP, then running the app.
Thanks

For anyone else reading this post, i thought of another way this could be done. Virtualbox comes with a program called vboxmanage, which allows you to run a VM directy. From a command line (or a launcher or menu item) you can run 
```
vboxmanage startvm "Windows XP"
```
(replace Windows XP with your machine name.)

As for running a windows app, this would be harder, since you need to control the windows machine. If you wanted it to run at every boot, though, you could always right click on the start menu > explore, then browse to programs > startup, and put a shortcut in there.

---

