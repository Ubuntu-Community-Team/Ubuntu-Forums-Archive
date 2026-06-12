---
title: "Crash when updating software..."
date: 2007-01-27
forum: General Help
---

### Post by sixfoottallrabbit on 2007-01-27
Hi,

When I either try to:

1) Use Applications>Add/Remove... to install a new piece of software, when I click "Apply" or
2) Use the software update thing that pops up as the orange box in the task bar, when I click "Install updates"

my screen flickers for a moment, then fades darker, and stays like that. I can move my cursor around but nothing else. I can't click anything, I can't use my keyboard to do anything. The only thing I can do is hit Ctrl+Alt+F1 to get to the terminal to reboot.

I think it may have something to do with the latest SVN version of Beryl. I only noticed it even doing the fade to dark thing at all once I got the latest update for it. I'd never seen it before.

Any help?

Thanks a lot.

---

### Post by JamieC on 2007-01-27
It's because a password prompt has been invoked as anything administrative requires root privileges. The prompt however did not come into focus and thus you are unable to do anything until you provide a password.

Can you ALT + TAB at all? If not, a temporary solution is to focus your desktop when performing such tasks.

---

### Post by sixfoottallrabbit on 2007-01-27
Ahhh.. it would seem as though you are partially correct.

It is indeed trying to pull up the password prompt, but, assuming that the prompt is by default shown in the center of the screen, it is not even starting. Infact, the box for the prompt in the program task bar at the bottom of my screen says "Starting adminis..." or something like that. So it doesn't seem like the prompt is even loading at all.

Any fix for this?

Thanks.

(ps. no, I can't Alt+Tab)

---

### Post by JamieC on 2007-01-27
> **sixfoottallrabbit said:**
> Ahhh.. it would seem as though you are partially correct.

It is indeed trying to pull up the password prompt, but, assuming that the prompt is by default shown in the center of the screen, it is not even starting. Infact, the box for the prompt in the program task bar at the bottom of my screen says "Starting adminis..." or something like that. So it doesn't seem like the prompt is even loading at all.

Any fix for this?

Thanks.

(ps. no, I can't Alt+Tab)

The prompt will have loaded, it says "Starting Administ..." because it's starting the task you chose and to start it requires a password.

I had this happen to me before on one occasion. I've never had it since, how often does this happen?

---

### Post by sixfoottallrabbit on 2007-01-27
It appears to happen every time I should be prompted for a password... and I don't know any way around it.

Plus, is there an easy way out of the screen darken fade rather than rebooting? That wastes time.

---

### Post by JamieC on 2007-01-27
CTRL + ALT + BKSP will restart the X server (and bring you back to the login screen).

What window manager are you using?

---

### Post by bazcor on 2007-01-27
My beryl system does the same, sometimes showing the password prompt, sometimes not. I have found that if the prompt doesn't come up I can type in my password followed by return and it works fine!

---

### Post by sixfoottallrabbit on 2007-01-27
> **bazcor said:**
> My beryl system does the same, sometimes showing the password prompt, sometimes not. I have found that if the prompt doesn't come up I can type in my password followed by return and it works fine!

Aha! That works.

Thanks a lot!

I guess I'll just have to get used to it. I'm guessing it's Beryl that's causing it to happen. Hopefully the next version will be fixed.

---

### Post by JamieC on 2007-01-27
> **sixfoottallrabbit said:**
> Aha! That works.

Thanks a lot!

I guess I'll just have to get used to it. I'm guessing it's Beryl that's causing it to happen. Hopefully the next version will be fixed.

It is indeed a Beryl bug with nVidia cards (referred to as the 'black screen bug'). The thing is, Beryl blame nVidia but the real source of the problem is undetermined. How did you install the nVidia drivers?

---

