---
title: "Thunderbird new mail alerts"
date: 2017-03-17
forum: General Help
---

### Post by r.stiltskin on 2017-03-17
In Xubuntu 14.04 LTS when Thunderbird received new mail its window button on the xfce4-panel began blinking.  I upgraded to Xubuntu 16.04 LTS recently and since then the window button no longer blinks to alert of new mail.  I can't find any relevant differences in system settings or in thunderbird preferences to account for this difference.  As it now stands, the only alert when new mail arrives is that the tiny indicator plugin mail icon changes from black to dark blue -- which is barely noticeable.  Any ideas as to how to get the window button to flash again?

A few years ago some people were complaining about this button flashing.  My complaint is the opposite -- I want it to flash.  I haven't found anything stating that this was changed in the panel code.

---

### Post by r.stiltskin on 2017-03-18
Some details that I omitted last night: I'm referring to a situation where Thunderbird is running in a workspace that is NOT the currently-visible workspace, and my window button preference for "show windows from all workspaces" is unchecked so the Thunderbird window button doesn't appear on the panel in my current workspace.  When a new email is received, the Thunderbird window button becomes visible on the panel of the current workspace, but it doesn't blink.  This problem is on my desktop machine that I upgraded to 16.04 LTS about a week ago.  Prior to the upgrade the window button would appear on the current workspace _and_ blink.

I've been experimenting with this some more.  On my notebook which I upgraded to the same Xubuntu  16.04 LTS about 2 weeks ago it's working correctly -- the Thunderbird window button becomes visible on the active workspace AND blinks to announce new email received.   Also, on the desktop, I set up a new user account and for the new user it's working correctly too.

I've determined that this function is controlled (at least in part) by the Firetray plugin to Thunderbird.  When I disable or remove Firetray and Thunderbird is running in a "background" workspace, the window button doesn't become visible in the active workspace to announce new mail.  Both machines have the same version of Thunderbird, 45.7.0,  and the same version of Firetray, 0.6.1, and the same settings in Thunderbird and in Firetray on both machines.

I tried replacing the Thunderbird profile in my primary user account -- actually I removed the entire .thunderbird directory so a completely new one was created.  This didn't change anything.  After setting up an email account and reinstalling the Firetray plugin it behaved exactly the same as before.  So there must be some other setting in my primary user account on the desktop that's preventing the blinking.  Any ideas on which setting or which file that might be?

---

### Post by r.stiltskin on 2017-03-20
Solved, more or less ...

It turns out that **de**selecting "Show flat buttons" on the Panel Preferences Window Buttons dialog, in addition to changing the appearance of the buttons also prevents the button from flashing when a new mail alert occurs.  Too bad, because I prefer the appearance of the distinct separated buttons, and I haven't figured out how to achieve that and also have the flashing button alerts.

But for anyone who wants to get rid of the flashing, just deselect "show flat buttons".

[Edit: sometimes you have to log out and log back in for the change in flashing/non-flashing behavior to occur.]

---

### Post by Habitual on 2017-03-21
Good job and well done.

---

