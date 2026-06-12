---
title: "Ubuntu 14.04LTS -- disable screen blanking in the lock screen"
date: 2016-01-27
forum: General Help
---

### Post by leka0024 on 2016-01-27
Hello,

I need to lock my screen when I leave the computer.

After I lock the screen, it soon after fades to black, which causes my monitors to go into standby mode. I do not want that to happen, I want the desktop background to stay on the screen and my monitors to stay active.


What is the best way to accomplish this? I'm running ubuntu 14.04 LTS.


Please let me know whatever other info you need about my system.


Thanks!

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
> **leka0024 said:**
> I want the desktop background to stay on the screen and my monitors to stay active.If that means you want it to show whatever it would be showing if it weren't locked - you just don't want it to respond to keyboard or mouse input until you unlock it you want xtrlock. That is both the name of the package and the command. It's quite elegant and minimalistic.

If you mean you literally want it to show whatever image (assuming it is an image) you have set for the desktop background and nothing else, then I'd suggest a script like this:
```
PSEUDOCODE: open the image in an image viewer of your choice in full screen mode
xtrlock
PSEUDOCODE: you might could figure out something here to close the image automatically when xtrlock is unlocked to save yourself the trouble of doing it manually
```

I don't know what you use for a screenlocker now. There maybe settings within it that can accomplish your goal. Try ```
man whatever-the-package-is-named
```

Personally, I don't trust any screenlocker to be as secure as xscreensaver, although it can be a bear to make it do anything beyond run one of the standard hacks. I use it when I don't need to see what is going on with whatever I left running and use xtrlock when I do.

---

### Post by leka0024 on 2016-01-27
Thanks for the reply. I think my desire is simpler than your suggestions.

For example, when I need to get up and leave the workstation for some time, I just press the Windows Key and L (I think this is "super+L") and the screen changes to just showing the background images and a login prompt.

I want those background images and login prompt to stay on the screen. However, currently they'll fade away to black within a minute. Once that happens my monitors go into standby mode.


I just want to disable that "fading to black".


Thanks

---

### Post by Dreamer Fithp Apprentice on 2016-01-27
I see. I misunderstood. So when you do that it shows something like a slide show for a while and then goes black?

That might still be something under software control. I haven't used the full blown flagship distro in several years, not since the Unity/G3 event, so I'm not up on what is the standard software for the screen locker, power management, etc.

But do you have "Gnome Control Center"? If you have an adaptive menu, like the Debian menu, it might be under Applications, System, Administration.

Or you can invoke it from the command line with```
gnome-control-center
```

From there, under "Hardware", click "Power".

There you have drop down menus to set "Suspend when inactive for", one for when on battery power, one for when plugged in. You can set them to "do not suspend".

If you don't have this program, and you installed the whole ball of U/G3 wax, you probably have something similar. What you want to look for is "power management". If you have an adaptive menu, maybe you can find it there. Try the same path I gave for gnome-control-center and look for something with an likely looking name. Or you may have one of those dinguses where you type in words associated with what you are trying to do (I'd try power management first) and it suggests programs. Pretty sure Unity used to have one of those.

Or if you cant find anything you can install it:```
sudo apt-get install gnome-control-center
```When it asks for your password, enter it and press enter, etc.

I HAVE had a system where none of this worked and only strange workarounds would keep the monitory from shutting down. No point in going into that unless it turns out to be the case and that isn't likely.

---

### Post by mc4man on 2016-01-27
Unfortunately no means to test tonight, only have a live session where locking the screen is the last thing that will happen in that session (no means to recover

But you could try - open system settings > Brightness & Lock.
Disable Dim screen & set Turn screen off.. to never. (top part of screenshot, ignore the screenie Lock settings, you want to leave that as is, ie. enabled
Then see what happens

---

### Post by leka0024 on 2016-01-28
Thanks for the replies, guys.

Dreamer Fithp Apprentice --> I already have that setting set to "Don't Suspend" (in System Settings -> Hardware -> Power). My system never suspends when I'm actively using it (ie, not in lock screen)

mc4man --> I already have that setting set to "Never" (in System Settings -> Personal -> Brightness & Lock). My monitors never shut off when I'm actively using the system (ie, not in lock screen).


I don't think there is a setting in the Systems Setting menu that enables/disables the screen fading out when lock screen is active.


Does anyone know how/if this can be disabled??

---

### Post by mc4man on 2016-01-29
There doesn't appear to anything (schema) associated with the screen blanking when locking the screen (super+l) which here starts about 5-6 sec. after going to lockscreen.
However if you create activity (move mouse, whatever)  once the fade-out starts then it seems the displayed lock screen will stay for the period of time based on the system settings > Brightness & Lock >  Turn screen off.. setting.
So that seems the best you may be able to do, ie. lock screen, wait a few sec.'s, move mouse or hit a key..

---

### Post by leka0024 on 2016-01-29
Thanks mc4man!!

While it seems a bit odd to me, if I lock the screen with Super+L and then immediately type "aaaa" into the password prompt, the screens will sit there indefinitely without blanking out. That is an acceptable workaround for me.


Does the thread title need to be changed to add a [SOLVED] prefix? Or maybe a mod can do that for me?

---

### Post by mc4man on 2016-01-29
you can go to top of thread > thread tools & set as solved
(- typing anything right after invoking lockscreen (not waiting a bit) seems to also work so I guess it's just lock the screen > activity then puts the timeout back to the user setting..

---

### Post by leka0024 on 2016-01-29
Thanks again for the help. I'm going to unsubscribe from this thread now. I've marked it solved.

---

