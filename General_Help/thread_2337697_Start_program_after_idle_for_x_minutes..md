---
title: "Start program after idle for x minutes."
date: 2016-09-20
forum: General Help
---

### Post by deadtom on 2016-09-20
I'm looking for something that will run a script when there is no mouse movement detected after a certain length of time. It doesn't have to stop the program when the mouse moves again, I just want it to start the program.

Does anyone know of anything that will do this?

---

### Post by izznogooood on 2016-09-20
You could look in to the screensaver, maybe modify it and fork it to what you need?
[https://launchpad.net/ubuntu/+source/xscreensaver](https://launchpad.net/ubuntu/+source/xscreensaver)

---

### Post by deadtom on 2016-09-20
> **izznogooood said:**
> You could look in to the screensaver, maybe modify it and fork it to what you need?
[https://launchpad.net/ubuntu/+source/xscreensaver](https://launchpad.net/ubuntu/+source/xscreensaver)

I've been messing with xscreensaver but haven't been able to find any way to make it run a command.

---

### Post by izznogooood on 2016-09-20
Depending on your skill level, here´s a start.
[http://unix.stackexchange.com/questions/120957/run-a-command-when-system-is-idle-and-when-is-active-again](http://unix.stackexchange.com/questions/120957/run-a-command-when-system-is-idle-and-when-is-active-again)

---

### Post by CantankRus on 2016-09-20
Have a look at xautolock.
I used this years ago so not sure how it performs with kubuntu.
```
sudo apt install xautolock
```
see **man xautolock**

_Example use:_
After 1min idle runs gedit... 
```
xautolock -time 1 -locker 'gedit'
```

Sends a message 5 seconds before specified idle time is up so you can reset by moving mouse.
```
xautolock -notify 5 -notifier 'notify-send "Gedit will start in 5 seconds"' -time 1 -locker "gedit"
```
```
xautolock -notify 5 -notifier 'notify-send "Script will start in 5 seconds"' -time 1 -locker "[COLOR="#808080"]/path/to/script[/COLOR]"
```

---

