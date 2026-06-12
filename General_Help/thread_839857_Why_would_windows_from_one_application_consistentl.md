---
title: "Why would windows from one application consistently open BEHIND windows from another?"
date: 2008-06-24
forum: General Help
---

### Post by Excalibre on 2008-06-24
For some reason, when I open pictures from file managers (either nautilus or thunar), when I open them with either gpicview or eye of gnome, they consistently open BEHIND the file manager window. Why would this happen? (How could something like this EVER be the proper behavior? What genius came up with this? Honestly, why is this even possible? Shouldn't new windows always open in the ******* front?)

So, uh, is there some way I can fix it?

---

### Post by cwbar_1 on 2008-06-24
It's been a while since I've used Xubuntu, but somewhere in the system preferences, under the windows behavior, you may have ticked the "Mouse over" effect for selecting windows.  Hope this helps.

---

### Post by lisati on 2008-06-24
Another possibility is that some programs have an "always on top" option.....

---

### Post by Excalibre on 2008-06-24
> **cwbar_1 said:**
> It's been a while since I've used Xubuntu, but somewhere in the system preferences, under the windows behavior, you may have ticked the "Mouse over" effect for selecting windows.  Hope this helps.
Uh, wouldn't you think that option would be pretty obvious? I mean, it'd be hard to miss windows getting selected every time I moused over them.


[quote=lisati]Another possibility is that some programs have an "always on top" option.....[/quote]
I checked that.

---

### Post by cwbar_1 on 2008-06-24
Sorry, I didn't mean to imply any negativity.  Like I said before, it's been a while since I've used Xubuntu.  Good luck, hope someone has the answer.

---

### Post by sdennie on 2008-06-24
Are you running compiz?  If so, try:

```

sudo apt-get install compizconfig-settings-manager

```

Then go to System->Preferences->Advanced Desktop Effects->General Options->Focus & Raise Behavior.  Play around with Focus Prevention Level.  I have mine set to "Low" and don't have anything like you are describing.  Also make sure "Focus Prevention Windows" is set to "any".

---

### Post by Excalibre on 2008-06-25
> **vor said:**
> Are you running compiz?  If so, try:

```

sudo apt-get install compizconfig-settings-manager

```

Then go to System->Preferences->Advanced Desktop Effects->General Options->Focus & Raise Behavior.  Play around with Focus Prevention Level.  I have mine set to "Low" and don't have anything like you are describing.  Also make sure "Focus Prevention Windows" is set to "any".
Thanks for the suggestion, but my compiz settings were already what you describe, so no dice.

I know it's a tiny thing to get irritated about, but it's so weird and it's so inexplicable when it seems like the normal behavior would be for a new window to always open in the front. It's not a tragedy if I can't fix it, just an admittedly minor annoyance.

---

### Post by LMP900 on 2008-06-25
I noticed that this only happens when I have a picture already open. So basically, the first picture I select opens normally (i.e. above the file manager) but every other picture opens behind it.

---

### Post by Excalibre on 2008-06-25
> **LMP900 said:**
> I noticed that this only happens when I have a picture already open. So basically, the first picture I select opens normally (i.e. above the file manager) but every other picture opens behind it.
Okay, I'm glad I'm not the only one. Except I haven't ever noticed what you're describing.

On further reflection I realize that I don't see this consistently; sometimes, they open in front, sometimes they open behind, but if I open a bunch at once they all act the same way. I'm not sure if maybe it changes when I reboot or something.

I think I got used to this enough (it happened to me in Gutsy too) that I stopped paying attention, but checking it out now it only happens to me sometimes. I'm not sure of any pattern to it, though.

---

### Post by LMP900 on 2008-06-25
> **Excalibre said:**
> Okay, I'm glad I'm not the only one. Except I haven't ever noticed what you're describing.

On further reflection I realize that I don't see this consistently; sometimes, they open in front, sometimes they open behind, but if I open a bunch at once they all act the same way. I'm not sure if maybe it changes when I reboot or something.

I think I got used to this enough (it happened to me in Gutsy too) that I stopped paying attention, but checking it out now it only happens to me sometimes. I'm not sure of any pattern to it, though.

That's strange. The behavior I described seems to be consistent for me. I suppose you can try to duplicate it to see if it's the case for you as well:

Make sure there are **no** Eye of Gnome instances running and open a picture in Nautilus. Eye of Gnome should launch the picture on top of the file browser. Now, **without closing** the previous Eye of Gnome window, open another picture. This one will open behind the file browser.

---

### Post by Excalibre on 2008-06-25
> **LMP900 said:**
> That's strange. The behavior I described seems to be consistent for me. I suppose you can try to duplicate it to see if it's the case for you as well:

Make sure there are **no** Eye of Gnome instances running and open a picture in Nautilus. Eye of Gnome should launch the picture on top of the file browser. Now, **without closing** the previous Eye of Gnome window, open another picture. This one will open behind the file browser.
I was really sure that that wasn't what was happening to me, but ****, you're right. This is probably the pattern I've been seeing all along and I just didn't put it together.

Okay . . . so of course the first EOG window ends up behind the others when you click on Nautilus again. I'm guessing the second one ends up behind Nautilus because the first one was by the time the user clicked it; that is, I'm guessing it's a misbegotten feature that looks at the stacking order of the currently open windows and tries to put new windows from the same application near their fellows.

I don't think this is the window manager, though, because I tried both with and without compiz and got the same results (or maybe compiz and metacity both do this). OTOH, I haven't seen this with gpicview at all. At least once (since it's what motivated me to start this thread) it opened *all* of the pictures I tried, starting with the first, behind the Nautilus window, but I'm trying over and over and can't get it to do what EOG does.

---

### Post by txbbq on 2008-08-11
Had the same problem and found the cause.  Had an HP printer installed. It had an app running called HP systray.  It just was a small icon in the upper left hand corner of my desktop.  Found it was set to "always on top" and it caused all windows that opened to open at the very back of any windows I already had open.  Changed that setting and everything works fine now.  Small thing that caused me lots of head scratching and frustration.  So see if you may have something running on your desktop doing the same thing.

Hope it helps

---

### Post by Linneo on 2008-10-29
Thanks txbbq!!
I had this annoying problem and that was the cause.
Thanks for your help!

---

