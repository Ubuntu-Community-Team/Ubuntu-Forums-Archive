---
title: "Lock Screen and Suspend from Command Line"
date: 2013-04-02
forum: General Help
---

### Post by NertSkull on 2013-04-02
The only way I can get my computer to suspend is with the following command. (This [thread]("http://ubuntuforums.org/showthread.php?t=2088696") is how I got that far)

```
sudo s2ram -f -m
```  

But that doesn't lock my screen before suspend.  So I thought I'd put together a little script to run all commands at once so I can lock my screen and then suspend in one motion.  Super simple I thought

```

qdbus org.freedesktop.ScreenSaver /ScreenSaver Lock
sleep 5
sudo s2ram -f -m
```

(I should note I added s2ram to my visudo file so I don't need a password for it to run)

This script does NOT work.  The screen locks, it tries to suspend but just hangs.  Then I have to restart my computer.

But, everything works separately.  For example.

If I first run ```
qdbus org.freedesktop.ScreenSaver / ScreenSaver Lock
```

It will lock my screen.  If I then ctrl+alt+1 to another terminal, I can then run my s2ram and it suspends correctly.  And awakes from suspend.

OR, for another example, if I run this.

```
sleep 5
sudo s2ram -f -m
```

And then in the 5 second sleep I push ctrl+alt+l (to lock the screen) the computer will suspend just fine.

So.... Why can't I combine the two operations into one script?  They clearly work together, what can I do to make them work at the same time in the same script?

Thanks!

---

### Post by Toz on 2013-04-02
Hello again NertSkull.

Out of curiosity, did you try [this]("http://ubuntuforums.org/showthread.php?t=1787043&p=10961829#post10961829") procedure? And if so, did it work? It should set uswsusp as the default suspend method (with the appropriate flags) so you don't have to run the script. For screen-locking, just use the built-in screen-locking mechanism (sorry but I don't have a kubuntu install handy to check what that mechanism is). There should be an option in the system settings somewhere.

---

