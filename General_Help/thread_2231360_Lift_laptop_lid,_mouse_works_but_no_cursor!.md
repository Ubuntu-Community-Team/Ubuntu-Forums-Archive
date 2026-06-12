---
title: "Lift laptop lid, mouse works but no cursor!"
date: 2014-06-25
forum: General Help
---

### Post by Bucky Ball on 2014-06-25
Hi all, 

As per the title. Fresh 14.04 LTS minmal install with xfce4 desktop and a few apps. The mouse is a wireless mouse which puts itself to sleep after a period of time (I think it's ten minutes). This function could have something to do with this issue (but I'm doubting that).

Currently ripping my hair out over this, and what befuddles me more is that during my research, and there has been plenty, I see this same bug dating way back in Ubuntu, but no fix, or only clumsy workarounds and nothing that works for me. It amazes me it is still around now, but here it is. As this is a minimal install, perhaps I have overlooked installing something, but apart from this 'invisible mouse' glitch after sleep, the system is working faultlessly. Quiet, fast and cool.

* Everything is working fine when I close the laptop lid. Computer goes to sleep, no noise, fan off and screen to black. Open the lid, everything is as it was, but no mouse cursor! Mouse still works as I can navigate to logout, and when I logout, mouse reappears. Login and all good.

* If I install xfce4-power-manager, close lid, the machine doesn't go to sleep, but the screen does go black. Open lid, everything as was and the mouse is visible (probably because the machine never actually goes to sleep). 

* So, with xfce4-power-manager, mouse fine when I open laptop lid but closing laptop lid only blanks the screen, doesn't put the computer to sleep;
* Without xfce4-power-manager, close lid and computer sleeps fine, open lid and mouse cursor has disappeared, even though the mouse still 'works', just can't see it!

Weird. I would surmise that bring the laptop out of sleep fails to switch the mouse back on, but that is not altogether true, as the mouse is still operational, just has an 'invisible' cursor. 

Any help or ideas greatly appreciated. This is an install for my wife's machine, I have spent way longer than expected on it, this is the final hurdle (for now) and I'd just like to get it out of the way and move on. The disappearing cursor is a deal-breaker, though, as this machine is on 24/7 and is put to sleep often. Having a mouse when it wakes up is essential.

TIA. ;)

PS: I have an inkling this is specific to this machine and perhaps something missing as I have an xfce4 14.04 minimal working faultlessly on my own machine and it has xfce4-power-manager, which is incidentally ticked in 'Sessions & Startup>Auto start apps', and the sleep/wake sequence works faultlessly. I tried exactly the same setup on the problematic machine and no joy. Which gives me a clue there is something different about this setup. Or could it be hardware?

---

### Post by Bucky Ball on 2014-06-27
Just to update this, I have duplicated the power manager setup of my own 14.04 minimal install on the problematic Compaq 610. Currently I don't have xfce4-power-manager  installed, nor do I have gnome-powermanager installed, and I have all power managers switched off in the Session and Startup menu. 

Now when I shut the laptop lid, back to square one. The machine goes to sleep fine, screen goes black, but when I lift the lid, no mouse cursor.

If I go to a tty with ctl+alt+f1 then back with f7, magic, cursor returns. I picked this tip up on my travels described as a workaround. It is that, but save having to log out and in.

I had an inkling it may have something to do with the power-saver USB mouse so I tried a mouse that doesn't have power-saving and no different. I also tried another mouse with power-saving. No different.

Ripping my hair out trying to figure this out. Thinking about posting this as a bug or adding to existing bug reports. Any thoughts?

---

### Post by Toz on 2014-06-29
Bucky Ball, have you tried unloading and reloading the psmouse kernel module?

---

### Post by Bucky Ball on 2014-06-30
> **Toz said:**
> Bucky Ball, have you tried unloading and reloading the psmouse kernel module?

Thanks for the suggestion. No, haven't thought of that angle. Where would I find that/how would I do that? I'll have a dig a bit later as have to go out for awhile. 

Thanks again. ;)

---

### Post by Luke M on 2014-06-30
Invisible cursor has nothing to do with the mouse. It's strictly a graphics issue. Normally the cursor is handled by dedicated hardware, which explains how it can mess up (due to a driver bug) without affecting anything else. What graphics chip/card are you using?

---

### Post by Toz on 2014-06-30
> **Bucky Ball said:**
> Thanks for the suggestion. No, haven't thought of that angle. Where would I find that/how would I do that? I'll have a dig a bit later as have to go out for awhile. 

Thanks again. ;)

Granted its a bit of a stretch, but in the past has solved mouse issues on resume in some cases. On resume, from a terminal:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```

@LukeM makes a good point though. Especially since a vt switch brings back the cursor.

---

### Post by jon.ti on 2014-07-29
I'm having pretty much the same situation that Bucky Ball describes, except that for me the bug of the disappearing mouse cursor on suspend doesn't occur every time, just very often.

My workaround has been to force the user to sign-in after a suspend. In Settings Manager, Light Locker Settings, switch 'Lock on Suspend' to ON.

---

### Post by Bucky Ball on 2014-07-29
Sorry all, forgot about this!

It is possible the fix was that I uninstalled all power managers and screensavers (and Light Locker, which I'd installed, from memory) and things were fine. I'll check that machine later and see if I've documented a fix there. The xfce4 power manager is not installed by default with a minimal and think I got into trouble doing some ad-hoc diddling and installing of my own. Put it down to some kind of conflict between xfce4 power manager, light locker, Power-Manager, and I think a couple of screen savers got a look in, too!

Cheers all, and solved.

@jon.ti: Welcome. If none of the ideas on this thread for you work, please start a new thread with a title describing your problem. Cheers and good luck. ;)

PS: Come to think of it, I think I did leave Light Locker so the screen would be locked when the laptop lid was lifted. And it works fine. On an install that's I've just finished on a dinky Dell D420 I haven't installed any power managers and shutting the lid/suspend works perfectly and the mouse/network both come up when I lift the lid, and that's without doing anything. Just installed a minimal then xfce4 and a couple of other things. No power manager.

---

