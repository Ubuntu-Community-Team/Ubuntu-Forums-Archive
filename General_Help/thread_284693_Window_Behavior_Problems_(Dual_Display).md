---
title: "Window Behavior Problems (Dual Display)"
date: 2006-10-26
forum: General Help
---

### Post by noripcord7 on 2006-10-26
Hello all,

Just tonight, after following the following instructions (the prelude to installing Edgy, which is up and running nicely), I started having some weird issues with window/desktop management.

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

I already suffer from the following bug, which makes it impossible to access the display module in the system settings window.

[https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/39603](https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/39603)

Basically, the problem is this: Striking alt-tab only switches between open windows on that screen (I have a dual-display setup) instead of all the open windows on both screens (on that desktop). Also, windows launch to the screen which has the currently active window, instead of the one currently housing the mouse pointer.

I believe the problems started immediately after I reinstalled the kubuntu-desktop package (see the first link). Any ideas?

Thanks
Dan

---

### Post by noripcord7 on 2006-10-26
More things to note:

In the window behavior module, in focus/navigation, when "show window list while switching windows" is unchecked, window switching works between the two screens. However, the windows switch in the wrong order: cycling through all open windows instead of back and forth (when alt-tab is pressed and released).

It's kind of late, I'm not sure how much of this is making sense. Perhaps I'll revisit it in the morning. Thanks again.

Dan

---

### Post by noripcord7 on 2006-10-26
Alright, another update (good and bad):

I found a temporary fix for the alt-tab problem. First, I edited ~/.kde/share/config/kwinrc and added the following line in the [Windows] list:

SeparateScreenFocus=false

Then, I ran the following command:

> kwin --replace --config ~/.kde/share/config/kwinrc

This sort of fixes the problem: now when Alt-Tabbing through windows, those on both screens are shown (though the Window list appears on whichever screen contains the window under focus). This fix seems temporary, though, since I can't figure out how to make the setting stick when kwin is restarted without writing an init.d file or something.

Another, probably unrelated problem: In the first post I complained that I couldn't view the display module (I was hoping there were xinerama settings within). Well, I followed the fix listed at the bottom of the second link in my first entry, and it worked, sort of. For a time I could access the display module (though there are no relevant settings, apparently), but now the module has disappeared from KControl and System Settings altogether! What gives?

Ugh. Frustration is mounting, but at least I can Alt-Tab through all my windows for now.

---

### Post by noripcord7 on 2006-10-26
The fix described also seems to change the window style from crystal to plastik for some unknown reason. Does anyone know where these kwin settings are actually located?

---

### Post by noripcord7 on 2006-10-26
Resolved! (I hope)

> kcmshell kwinfocus

And check "Separate screen focus" (and "Active mouse screen"). I swear I looked at these options at least 20 times and it never occurred to me that they were what I wanted. Perhaps more accurate or lengthy descriptions would be nice.

Still no word on why my display module is missing, I'll post back when/if I figure that one out.

---

### Post by neouser99 on 2007-05-05
i must agree... those options don't seem to have anything to do with the problem, but i'm glad i stumbled upon this post. i don't remember this being that difficult in the past, and i think there was an option that did what it said, but i can't remember it 100%

-neo

---

### Post by jokester01au on 2007-09-13
I have a related problem.

It is annoying me no end that with "separate screen focus" ticked,after closing a window, the new window in focus is the one that was underneath the now closed window. This behaviour is ridiculous. For example:

1. Open kate.
2. Open the "open" dialog.
3. move the dialog to the opposite screen (sometimes it opens there by default).
4. open a file.

The window now selected is the one that was underneath the open dialog!

Deselecting "separate screen focus" fixes this problem but has the distinct disadvantage of being unable to alt-tab over to windows on the other screen.

There doesn't seem to be a way to get both working simultaneously.

---

