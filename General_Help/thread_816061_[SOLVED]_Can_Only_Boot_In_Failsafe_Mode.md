---
title: "[SOLVED] Can Only Boot In Failsafe Mode"
date: 2008-06-02
forum: General Help
---

### Post by twoseids on 2008-06-02
Hardy ran pretty much flawlessly for the first week. Now, some of the time I can't entirely boot up. After logging in, I get my desktop background and Twhirl (via Adobe Air). That's it. No gnome-panel. Ctrl+Alt+Del doesn't work. I can get Gnome-Do to open with the keyboard shortcut, but nothing comes as a result of any commands I execute there. One other thing - I don't get my startup sound either. So when I hear my startup sound, I know the session will work; if I don't hear it, I know it won't. Ctrl+Alt+Backspace does work to close the session.

When I login in using the Failsafe Gnome session, everything seems to be okay.

How can I troubleshoot this? Is Compiz Fusion the culprit?

I'm on a Dell Latitude D520. Thanks!

---

### Post by twright on 2008-06-02
you could try removing all hidden files in your home directory (you will lose some settings if you do this)

to do this open naultilus, press ctrl + h then delete all files/folders beginning with .

---

### Post by twoseids on 2008-06-02
> **twright said:**
> you could try removing all hidden files in your home directory (you will lose some settings if you do this)

to do this open naultilus, press ctrl + h then delete all files/folders beginning with .
What's the rationale behind this?

(Not questioning you, just trying to learn a little something along the way.)

---

### Post by ibuclaw on 2008-06-02
> **twright said:**
> you could try removing all hidden files in your home directory (you will lose some settings if you do this)

to do this open naultilus, press ctrl + h then delete all files/folders beginning with .

Everything except "**.bash_logout**", "**.bashrc**" and "**.profile**". Those are the absolute neccessities for your account that can be replaced from the **/etc/skel** folder.

Regards
Iain

---

### Post by ibuclaw on 2008-06-02
> **twoseids said:**
> What's the rationale behind this?

(Not questioning you, just trying to learn a little something along the way.)

9 times out of 10, these sorts of things happen because you tweaked a certain setting and it's full effect didn't take place until after you reboot/logout.

And usually, it is very difficult to isolate these matters, as everyone has a different desktop layout. So a full reset back to original settings is usually the answer given
(Removing all hidden folders in your home folder removes all your user desktop settings and your default (stable) system settings are used instead).

If you are unsure, try creating a new user. Just to double check that it is indeed a setting in your account and not a fault of the system.

Regards
Iain

---

### Post by twright on 2008-06-02
> **twoseids said:**
> What's the rationale behind this?

(Not questioning you, just trying to learn a little something along the way.)
also these files sometimes become corrupted, when programs try to load the corrupted config files they often crash

---

### Post by twoseids on 2008-06-02
> **twright said:**
> also these files sometimes become corrupted, when programs try to load the corrupted config files they often crash
Thank you, twright and tinivole. I've just deleted all the files and folders of which I don't care if I lose the configurations, and will try to log in again in a bit. If that doesn't work, maybe I'll delete one by one.

I've got things I'm scared to delete if I don't have to, like .mozilla and .mozilla-thunderbird (profiles, yikes!), .gnome2 and .nautilus (sound important), .VirtualBox, and .xmoto (my high scores!)

---

### Post by ibuclaw on 2008-06-02
Sounds good to me! Although, if problems persist. **.gnome2** and **.nautilus** may have to go too (infact, those would be the first on my list to go).

And if you can't remove the "**.gvfs**" folder either, then you'll have to reboot into recovery and proceed into the root shell. (gvfs has proven to be a bit of hassle in the past).

Regards
Iain

---

### Post by twright on 2008-06-02
> **twoseids said:**
> Thank you, twright and tinivole. I've just deleted all the files and folders of which I don't care if I lose the configurations, and will try to log in again in a bit. If that doesn't work, maybe I'll delete one by one.

I've got things I'm scared to delete if I don't have to, like .mozilla and .mozilla-thunderbird (profiles, yikes!), .gnome2 and .nautilus (sound important), .VirtualBox, and .xmoto (my high scores!)you don't need to delete stuff like .mozilla but it is safe to delete .gnome2 and .nautilus as when they are deleted they will be automatically regenerated, those files are only user specific configuration all of the important files are stored in /usr

---

### Post by twoseids on 2008-06-02
Once again, thanks. Just rebooted and everything worked just fine. In fact, even better than fine. My mouse buttons got all messed up with too much tinkering (my middle scroll wheel was 'right click' and I think the right button was 'right and left click at the same time'), but now all the buttons are back to normal!

Only thing is that I have to re-enter many of the launcher properties in my panel, as they got wiped clean. But no problem, I remembered which ones they were (well, all but one - I'll figure it out).

I also have to do another Edit Menus since it looks like everything is being displayed on all menus, but that's no biggie. I even like doing that.

I love this community!

---

### Post by ibuclaw on 2008-06-02
Good, that is great to hear.

Although, just one note for the future. All Gnome Menu icons are in the **./local** folder.
And since generally nothing is stored in it (apart from Trash and Gnome Menu files). It was probably worth keeping.

I should have perhaps realised and given it a mention before you removed it :)

Ahh, well.
Nevermind.

Regards
Iain

---

### Post by twoseids on 2008-06-02
No harm done. And now I know something else! (And with Linux, "knowing something else" is really the name of the game.)

---

