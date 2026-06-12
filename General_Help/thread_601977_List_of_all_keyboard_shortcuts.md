---
title: "List of all keyboard shortcuts"
date: 2007-11-03
forum: General Help
---

### Post by sicofante on 2007-11-03
Is there any way to see a full list of the current set of keyboard shortcuts?

---

### Post by nick_h on 2007-11-03
Sysem->Preferences->Keyboard Shortcuts

---

### Post by sicofante on 2007-11-03
Thanks, but that list is very limited (is it just for Gnome?). What I'm asking for is a list of EVERY shortcut the system is ready to listen at some point.

For instance, now that Gutsy installs Compiz by default, a lot of new shortcuts are available on an empty workspace. If a particular app is opened, an additional list of shortcuts will be available.

What I'm asking for is a way to know what shortcuts the system is listening to "right now".

The reason I want this is because I want to customize the shortcuts dealing with windows (mostly Compiz shortcuts) and I want to make sure I'm not interfering.

If there's no user interface (GUI or CLI) to such list but there's an API to access it, I'd be happy to know about it too.

---

### Post by strabes on 2007-11-03
I think compiz has a feature that notifies you if you've created a conflicting keyboard shortcut.

---

### Post by k33bz on 2007-11-03
RELATED QUESTION:

Is there a way to see what keys are assigned to different things.  (Dont know how to word that right).

I have installed xbinding keys, and cant it to work right due to not knowing the key mapping.

---

### Post by sicofante on 2007-11-07
> **strabes said:**
> I think compiz has a feature that notifies you if you've created a conflicting keyboard shortcut.
Yeah, but only conflicting with itself. There's nothing preventing you from creating a shortcut that's already in use by other application.

---

### Post by Hatchetfish on 2007-11-07
I'm going to guess that what you're after doesn't exist.  Main reason is that keyboard shortcuts are handled at several different levels, the last one of them being each individual application.  While it probably is possible without -too- godawful much work to write something that can check all or most of the shortcut catching systems, the application level would be a nightmare, due to the varied ways shortcuts are specified and coded for every app out there.  I believe 'compliant' gnome apps (not just things that use the gtk toolkit, but things written to play nice with gnome) are supposed to use some sort of gnome wide system for this, but it's pretty unlikely you're -only- interested in them, and I still don't think there's a way to get a summary of it.

What's your goal in having the list?  Maybe there are other ways to accomplish the goal.  (If it's just that you want to know all the shortcuts in the known ubuntu universe because you like using them, I'm afraid you're probably just in for a lot of reading in help files.)

---

### Post by Hatchetfish on 2007-11-07
oops, missed that you explained the goal.  my only suggestion there is trial and error; pick a shortcut you like, press it, see if anything happens.  if you can't tell anything happened, use it.  if at some point something else does happen, because you finally happen to have the app that uses that shortcut open, go back and sort it out.  i'd guess most destructive shortcuts like save are fairly consistent, so it shouldn't be the end of the world if you eventually find a conflict, long as you stay away from common forms of save, quit, 'nuke drive and fry processor without confirmation' ;) or the like.

---

### Post by sicofante on 2007-11-08
I started with the idea to use the super key for actions relating to windows management, compiz, etc. (which I'll suggest for Hardy). Then I though it would be a nice idea to standardize shortcuts all over the desktop. I guess I do have a lot of help files reading ahead indeed :-) Or maybe I feel brave enough one of these days and start coding a "key listener" or something...

---

### Post by orbish on 2007-11-08
Here's all I can come up with... install advanced settings for compiz

sudo apt-get install compizconfig-settings-manager

system > preferences > "Advanced Desktop Effects Settings"

you can see what keyboard shortcuts are assigned to certain effects/tools... for example, when i click on the zoom properties, then the "actions" tab, it shows keyboard shortcuts for all zoom options with that plugin...

you can hop around in there and customize it to how you want it, unfortunately i don't know of a complete list... someone should make one :D

---

### Post by Hatchetfish on 2007-11-12
> **sicofante said:**
> I started with the idea to use the super key for actions relating to windows management...

I've done the same, seems to work nicely, since very little in the way of individual programs use it; they seem to stick to the old standbys alt ctrl shift.  At least they do unless you're into emacs, carpal tunnel, and 'shortcuts' like ctrl-alt-shift-esc-Q-cokebottle-backspace... shudder...  ;)

---

### Post by sicofante on 2007-11-13
I'll go ahead with that part, then, thanks! The final goal, however. is finding (and/or developing) a standard way to deal with shortcuts. This is one of the cases where choice is very bad. Maximizing a window should ALWAYS be F11 **OR** Ctrl-F, but not sometimes F11 and some other times Ctrl-F. I know it's up to the applications themselves, but enforcing it "from above" would be the right thing to do.

---

