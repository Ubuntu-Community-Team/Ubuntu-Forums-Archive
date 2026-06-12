---
title: "Screen Freeze on old lock screen after upgrade Ubuntu 14.04"
date: 2014-04-01
forum: General Help
---

### Post by jellybabyassassin on 2014-04-01
Hi Forum People

So, I recently did an upgrade of from Ubuntu 13.10 to Ubuntu 14.04.
I am using Unity, cause I like the layout.
Everything appears to have gone ok, except for the new lock screen thing.

If I lock the screen myself with Ctrl+Alt+L it works fine. 
It goes to the new lock screen and it looks pretty and all the blah and I can get back in.

If I leave the computer idle and the system times itself out and locks the screen, the screen lock goes to the *old* lock screen (where the login is in the middle of the screen).
From this, I'm stuck. I can't do anything, the screen is frozen, and can't none of the keyboard or mouse things work. 
The only thing I appear to be able to do is reboot, with R_Alt+Prt_Scr+REISUB.

Where can I even start to look for the problem?

Any help would be appreciated, I can't leave my computer alone by herself ... :P

Regards
Brian

---

### Post by luizluca on 2014-04-01
Same here. Also upgrade from 13.10.

My machine uses AMD ATI with fglrx.

BTW, I can recover from this freeze by ctrl+alt+f1, log in, sudo /etc/init.d/lightdm restart

---

### Post by sandyd on 2014-04-02
Moved to Ubuntu+1

---

### Post by jellybabyassassin on 2014-04-03
Anyone? 
Can anyone direct me to where the "lock screen" settings are for when I press ctrl+alt+L and where the mechanism to lock the screen without my intervention is?

Regards

---

### Post by nitsuga1986 on 2014-04-19
I am having the same problem...totally anoying. I am recovering from this freeze by ctrl+alt+f1, log in, "sudo /etc/init.d/lightdm restart" but this is not a real solution....

---

### Post by cariboo on 2014-04-19
Moved to General Help seeing as Trusty has been released.

---

### Post by tkillby on 2014-04-21
I'm in a similar situation here. Except all was good for me, I installed sudo apt-get install xubuntu-desktop, then removed it, but I still have an ugly lockscreen unless I Ctrl+Alt+L, I'd love to be able to install the nice new 14.04 lockscreen and have it working like new.

---

### Post by Jon_VandeRiet on 2014-07-04
I am having the same problem. Recently installed Ubuntu 14.04 on a new Dell laptop. I also installed, then removed, lubuntu (trying to enhance performance). I don't think the problem started occurring until after that. Has anyone found a solution, aside from switching to tty1 and doing sudo service lightdm restart (which seems to work, though I think it resets the session)?

---

### Post by George_Ronald_Mayfield on 2014-07-14
I get this problem. If the computer times out and turns the screen off, I occasionally get a frozen screen when I move the mouse to come back to my session.
It's the same login screen as always (not the center log in screen). The user name is in a transparent window, but there is no box to type in the password. There is no icons at the top for help or onscreen keyboard. Clicking anywhere on the screen does nothing, as well as letting the computer sit and think about what it's done.
I've just been holding the power button to force the computer off and restarting it, but that can't be good.

---

### Post by johnemb2 on 2014-08-29
I am hit by this issue as well (14.04 release), and hope that someone will pick it up via [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1301125](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1301125)

---

