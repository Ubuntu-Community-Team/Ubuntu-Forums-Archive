---
title: "Cinnamon not working on Ubuntu 12.04"
date: 2013-05-08
forum: General Help
---

### Post by linuxvstheworld on 2013-05-08
I run a small server with a GUI on ubuntu, that GUI being Cinnamon, it was all working normally, now, it looks like this: 
[IMG]http://i.minus.com/iywtnH5aXWqfg.png[/IMG]
The window buttons don't even show up, any help?

---

### Post by 25tom on 2013-05-09
I had a similar problem with LXDE once, but can't remember exactly how I solved it... 

A bit of a shot in the dark here, but try entering the command for whatever window manager you're using, be it Metacity, Compiz, Openbox, or whatever, into the terminal. This should hopefully start your window manager back up again, as it looks to me like it has for some reason stopped running. Just a quick check - have you tried rebooting? I'd try that first if not... but I am not really experienced that much with servers...

Hope this helps anyway :)

---

### Post by linuxvstheworld on 2013-05-09
> **25tom said:**
> I had a similar problem with LXDE once, but can't remember exactly how I solved it... 

A bit of a shot in the dark here, but try entering the command for whatever window manager you're using, be it Metacity, Compiz, Openbox, or whatever, into the terminal. This should hopefully start your window manager back up again, as it looks to me like it has for some reason stopped running. Just a quick check - have you tried rebooting? I'd try that first if not... but I am not really experienced that much with servers...

Hope this helps anyway :)

I'm using the default window manager, or whatever window manager cinnamon comes with, i can't do the keyboard shortcut to even run a command. My plan is to ssh into it, log out of it, and switch the DE, will post results.

---

### Post by 25tom on 2013-05-09
It seems that the window manager for Cinnamon is 'muffin'. Try using the command ```
muffin --replace
``` to restart it, if that's possible over SSH. Good luck anyway :)

---

### Post by linuxvstheworld on 2013-05-09
> **25tom said:**
> It seems that the window manager for Cinnamon is 'muffin'. Try using the command ```
muffin --replace
``` to restart it, if that's possible over SSH. Good luck anyway :)

The thing is, even the bottom bar doesn't show up.

---

### Post by 25tom on 2013-05-09
Hmmm, maybe you should try another DE. Did that command do anything at all (if it was possible to run it)? Do you have another DE installed already? And if so can you logout, then login to that other DE?

---

### Post by linuxvstheworld on 2013-05-09
> **25tom said:**
> Hmmm, maybe you should try another DE. Did that command do anything at all (if it was possible to run it)? Do you have another DE installed already? And if so can you logout, then login to that other DE?
```
muffin --replace
``` did not work.... I am going to attempt the second plan I had in mind, will post results of that as well...

UPDATE: Every time I attempt to start a program or a script it comes up with this result
```
haidawe@haidawe:~$ muffin --replace
muffin: command not found
haidawe@haidawe:~$ docky
[Info  16:59:21.087] Docky version: 2.1.4 Release
[Info  16:59:21.164] Kernel version: 3.2.0.41
[Info  16:59:21.166] CLR version: 4.0.30319.1
[Warn  16:59:21.201] [Gtk] cannot open display: 
haidawe@haidawe:~$ compiz --replace
compiz (core) - Fatal: Couldn't open display
```
I tried getting Docky so I can have a small amount of functionality left, no luck either...

---

### Post by 25tom on 2013-05-09
Hmmm, I'm a little out of my depth now... what are your hardware specs, in case it's a graphics problem? And how long has this been a problem? Because knowing if it's a sudden problem on a system that's worked fine for a while or problems with a fairly new system will narrow down the possibilities...

---

### Post by 25tom on 2013-05-09
Not sure if it's the same problem, but this MAY help: [http://askubuntu.com/questions/31167/how-can-i-restart-compiz-from-tty-related-how-can-i-set-up-a-fallback-wm](http://askubuntu.com/questions/31167/how-can-i-restart-compiz-from-tty-related-how-can-i-set-up-a-fallback-wm)

---

### Post by linuxvstheworld on 2013-05-09
FIXED! I had to reinstall cinnamon in its entirety, I believe the update through update manager messed it up.
For future people who may have this issue, try this and reboot: 
```
 
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable        
sudo apt-get update         
sudo apt-get install cinnamon

```[INDENT]
[/INDENT]
 This code was provided from [here]("http://community.linuxmint.com/tutorial/view/1246"). Thanks for everyone's help!

---

### Post by 25tom on 2013-05-09
Glad it's working for you now :)

---

### Post by d.atanasov on 2013-05-09
I had some experience with Cinnamon a while ago. It was freezing all the time and I found this command which you can run from terminal 

[http://forums.linuxmint.com/viewtopic.php?f=47&t=122375](http://forums.linuxmint.com/viewtopic.php?f=47&t=122375)

I hope that your problem can be fixed. 

cheers

---

### Post by linuxvstheworld on 2013-05-09
> **d.atanasov said:**
> I had some experience with Cinnamon a while ago. It was freezing all the time and I found this command which you can run from terminal 

[http://forums.linuxmint.com/viewtopic.php?f=47&t=122375](http://forums.linuxmint.com/viewtopic.php?f=47&t=122375)

I hope that your problem can be fixed. 

cheers

It has been fixed, I'll keep the commands in the link in mind, check my previous post on this thread, thanks!

---

### Post by 25tom on 2013-05-10
You should mark this thread as [SOLVED] - apologies if you have already done so by the time this post is read! Go to your first post, click 'edit post', then 'go advanced' and finally change the prefix from [ubuntu] to [SOLVED]. 

:)

---

### Post by linuxvstheworld on 2013-05-10
> **25tom said:**
> You should mark this thread as [SOLVED] - apologies if you have already done so by the time this post is read! Go to your first post, click 'edit post', then 'go advanced' and finally change the prefix from [ubuntu] to [SOLVED]. 

:)

Odd how they changed the location of where to change the prefix, you used to do it via 'thread tools'.

---

