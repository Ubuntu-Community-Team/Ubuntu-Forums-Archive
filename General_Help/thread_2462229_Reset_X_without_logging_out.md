---
title: "Reset X without logging out?"
date: 2021-05-16
forum: General Help
---

### Post by goemonburo on 2021-05-16
I am not positive this is an X problem so please let me know if it's not, but what happens, fairly frequently, is that a program hangs, often my file manager (PCManFM-Qt), and then I can't open my file manager, but additionally, my virtual desktop windows fail to clear, so that when I switch from virtual window 3 to 4, the background becomes whatever I was working on in 3 if there's not a window active in the same position on 4.  

The only solution I've found is to log out and log back in again, but it's a huge hassle as it means shutting down numerous applications only to restart them again.  Is there any way to get this problem solved without logging out by some command line tool?

Thank you!

(Sorry:  Adding Lubuntu 20.04LTS as the OS.)

---

### Post by guiverc on 2021-05-16
You haven't provided any OS & release details... which maybe helpful.

Your mention of `pcmanfm-qt` makes me think of Lubuntu and thus using LXQt as a desktop, but is it what you use?

In LXQt,  `pcmanfm-qt` is more than just a file-manager, but handles a lot of your desktop, so if it hangs, LXQt may  also be impacted too, and functions like switching virtual desktops may have issues as it's `pcmanfm-qt` that puts the wallpaper on your LXQt screen...

I personally would look for the cause of the issue, which you didn't elaborate on.

  You also didn't mention OS & release, and may not be using Lubuntu/LXQt so none of my comment may apply.

---

### Post by dddman on 2021-05-17
Seen your thread and thought this is something I could also use, a reset.

So off I went on my quest.  First thing I found out is it's not possible to reset x without getting logged out.  Also found out that X is old school and I need to update my thinking.

Searching gnome3 I found restart session and reset shell.

$ killall -3 gnome-shell

This may serve as a reset, I tried it and it won't log you out.  Just don't know if it will do any good, needs to be put to the test.

@guiverc
Crap, I don't know these things.  I'm posting anyhow.

---

### Post by goemonburo on 2021-05-17
Hi.  You were right about Lubuntu (added it above).  And yes, for some reason it's seemed those are linked -- when my window manager fails, other things go wrong too.  But as far as a cause, there's nothing specific that I am doing.  It's not a repeatable thing.  It might happen, for example, when I plug in a CF card (that's worked fine 300 times before)...and it hangs the window manager and then...virtual desktops go haywire...It might be a program that hangs and I try "End Process" to no avail and...same thing.  Right now it seems to be Kdiff3 that's done the trick...it stopped reading directories about 15 mins ago and I'm pretty sure I'm going to be logging out yet again to get things back to normal.

---

### Post by guiverc on 2021-05-17
Lubuntu uses `openbox` as it's window manager (as LXQt and LXDE before it doesn't perform those functions).

Are you `diffs` running using network shares?  I do on occasion have network issues where I lose for a time access to my network shares (and some processes hang waiting for it to return), but it doesn't really fit your situation as it doesn't impact my whole desktop (that I'm aware of anyway; though I recognize the issue & work to resolve it so likely don't notice the effects much).

CF card though is local I assume, which doesn't fit a network issue.

I know older intel CPUs used to slow if the temperature was rising, so a *not-working-well* fan can cause a slower box (*as the CPU slows [runs wait-states] as a means of temperature control*), so I'd likely explore that, especially if your box is older.  I'd also test your hardware out using a *live* system so it's not working from your current configs & software, but different software on the *live* media.

But these are just thoughts/guesses from your description, as I have no real idea sorry.

---

