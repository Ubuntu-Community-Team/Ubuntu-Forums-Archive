---
title: "beryl and xgl on dapper"
date: 2006-11-18
forum: General Help
---

### Post by Dark_Omen on 2006-11-18
I installed beryl and xgl, and it seemed to install fine. Everything works except windows. The frames around them (which includes the minimize, and exit buttons) just blinks really fast, they are still usuable (if you happen to catch it when the frames are there for a split second). I am using dapper drake, and I have an ATI graphics card.
Thanks

---

### Post by philippe_carlo on 2006-11-18
I had the same thing going on: two 'emerald --replace' processes end up replacing each other to infinity. Here's the fix (from a terminal window):
```

killall emerald
emerald --replace

```
If you do not manage to open a terminal window, go to a virtual console and run this command in between the two above commands:
```

export DISPLAY=:0

```
(Change the 0 into 1 if you are using ATI)

You typically get this when you start beryl from the session file or something, s.t. the session starts beryl and restores another beryl from the last session at the same time.

---

### Post by Dark_Omen on 2006-11-18
It didn't work. Well it did work, just when I close the console nothing show up instead of it flickering. When the console is still open the windows seem to be fine.

---

### Post by aliyanage on 2006-11-18
what happens when you ctrl+alt+backspace?
I know it's not a permanent solution but I just wonder whether it makes any difference...

---

### Post by Dark_Omen on 2006-11-18
no restarting it didn't do anything.

---

### Post by Random20230808 on 2006-11-19
First of all, does Xgl work fine with Metacity manager (Gnome default)?
You have to be sure about that before you proceed with Beryl check out.
To make sure Xgl is running in your current session, just run ps -e | grep Xgl from a terminal. If there is output it is running.
(Last line taken from [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl"))

---

### Post by Dark_Omen on 2006-11-20
Ok, so I got it working. :)
Thanks

---

