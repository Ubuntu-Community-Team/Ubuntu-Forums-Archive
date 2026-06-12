---
title: "Session manager problems"
date: 2007-06-10
forum: General Help
---

### Post by zorblek on 2007-06-10
Hi! I'm a relatively new Ubuntu user, and I'm having some problems with the session manager in Feisty.

I'm attempting to set Beryl to start automatically at startup, but it's not working. Here's what happens: I go to System > Preferences > Sessions, and attempt to add a program to the startup list. It seems to work fine, and the entry shows up on the list. So far, so good. But when I close the session manager and restart the system, the program doesn't load, and the entry is gone from the list. In fact, the entry disappears from the list as soon as I close it. I'm pretty sure that this is a problem with the session manager and not with Beryl, as I have tried the same procedure with other programs and had the same problem.

Any help would be greatly appreciated. Thanks!

---

### Post by futz on 2007-06-11
> **zorblek said:**
> Hi! I'm a relatively new Ubuntu user, and I'm having some problems with the session manager in Feisty.

I'm attempting to set Beryl to start automatically at startup, but it's not working. Here's what happens: I go to System > Preferences > Sessions, and attempt to add a program to the startup list. It seems to work fine, and the entry shows up on the list. So far, so good. But when I close the session manager and restart the system, the program doesn't load, and the entry is gone from the list. In fact, the entry disappears from the list as soon as I close it. I'm pretty sure that this is a problem with the session manager and not with Beryl, as I have tried the same procedure with other programs and had the same problem.

Any help would be greatly appreciated. Thanks!
What are you putting as the command for starting Beryl? The command should be:
```
beryl-manager
```

---

### Post by zorblek on 2007-06-11
That's the command I'm using. (I've also tried just "beryl", and also "firefox" and "gedit" for the hell of it. None of them stayed on the list.)

---

### Post by futz on 2007-06-12
> **zorblek said:**
> That's the command I'm using. (I've also tried just "beryl", and also "firefox" and "gedit" for the hell of it. None of them stayed on the list.)
How strange. I always have mine start up firefox and beryl-manager on all the machines here. Never had any problems with it.

Don't be offended by this next dumb newbie question. I'll ask it just in case: You do know the first line is just a label, and not the actual command, right? The second line is where the command goes. On pre-Feisty session manager there was only one line where you put the command.

---

### Post by zorblek on 2007-06-12
Yes, I did know that. :) (Although I tried switching them around at one point just to make absolutely certain...)

---

### Post by xang on 2007-06-13
There is a permissions issue with the /home/<username>/.config/autostart directory. 
Open up a terminal session and do the following:

sudo chmod 777 /home/<username>/.config/autostart 

the password sudo asks for is your password you use to login.

where username is your home directory. (ex. /home/xang/.config/autostart )

Once you do this..you should be able to add entries into the session manager and they will execute on boot and stay put!

Enjoy.

---

### Post by zorblek on 2007-06-14
Thank you, xang! That did the trick.
=D>

---

### Post by Depressed Man on 2007-10-23
Tried that on Gutsy and things till won't stick :(. Navigating to the .config folder doesn't show an Autostart (anything). However creating it says that it already exists..

---

