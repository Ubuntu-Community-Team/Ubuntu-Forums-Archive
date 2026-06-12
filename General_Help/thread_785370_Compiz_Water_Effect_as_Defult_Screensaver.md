---
title: "Compiz Water Effect as Defult Screensaver?"
date: 2008-05-07
forum: General Help
---

### Post by OZFive on 2008-05-07
So I was wondering if there was a way to use Water Effect as the Default screen saver, or did I say that already?

Well I am at work and I want to have the screen saver jump on when I am idle but I still want to see the desktop as I receive emails or when someone IM's me and can see the pop up alert. 

I can do this by disabling the screen saver and just enabling the Water Effect myself but there are times when I am not thinking about it and would like it to go automatic.

Anyone got any ideas?

---

### Post by sinbad#1 on 2009-02-07
This idea really interests me too! Does anyone know how to implement this?

---

### Post by setsuna on 2009-02-09
yeahh, i was wondering too. I want my Ubuntu have a wates splashy and aquarium screensaver like OSX Leopard ones. It's very nice!!

anyone know 'bout them? or have the tuts to make it real? he he he
thx a lot

---

### Post by johnjohn2 on 2009-02-09
would be nice to have this also

---

### Post by MrKlister on 2009-04-15
I just made such a script that works as a screensaver.

What it does is that it turns the water effect on when the computer goes into idle mode (when the screensaver usually starts) and then  turns off when the computer goes active again.

To use it just
turn off the option "Activate screensaver when computer is idle" in System -> Preferences -> Screensaver 

and
save the attached file and make it executable with the following command:
```
sudo chmod 754 waterscreensaver.py
```

and then 
add it to System -> Preferences -> Sessions so that it will start at startup.

---

### Post by Caleb.Robertson on 2009-04-28
I got the script up and working but it only works once and to get it to turn off I have to hit f9...any ideas.

---

### Post by Caleb.Robertson on 2009-04-28
Ok I re-downloaded the script and it will do it more then once now but I still have to turn it off with a key combination rather then it turning off when the computer is no longer idle. Any Ideas?

---

### Post by MrKlister on 2009-04-28
> **Caleb.Robertson said:**
> I got the script up and working but it only works once and to get it to turn off I have to hit f9...any ideas.

Sorry I noticed this myself. Sometimes it works a couple of times.

It seems that a message telling that the computer is no longer in idle mode is not senton the dbus. This is a bug probably somewhere in ubuntu.

Cant do much about it I think. Hopefully it will be fixed sooner or later. 

Sorry.

---

### Post by Bladtman242 on 2009-06-08
Nvm, turns out im just a noob:D

In case anyone else is as retarded as me its

```
sudo chmod 754 PATH/FILENAME
```I just typed exactly what MrKlister wrote:D

Example: if waterscreensaver is stored in home:

```
sudo chmod 754 /home/waterscreensaver
```I realise most people will roll their eyes at this post, but as a newb, i know how nice 
it is for newbs when other people simplyfy things like this :)

Thanks for the tip MrKlister, Really cool:D works like a charm

---

### Post by realzippy on 2009-09-01
here is a working one:

[http://ubuntuforums.org/showthread.php?t=1246897](http://ubuntuforums.org/showthread.php?t=1246897)

---

