---
title: "Bizarre keyboard bug"
date: 2013-01-23
forum: General Help
---

### Post by Phiwum on 2013-01-23
I recently upgraded my HP Pavilion DM4 from Ubuntu 11.10 to 12.10.  Since then, I have a very odd keyboard bug that I can't diagnose.

Every so often, the keyboard starts responding very slowly.  I have to press a key for (rough guess) half a second for it to register.  If I press any shorter time, it's the same as no press at all.  If I press longer, then the key will repeat, slowly.

I'm not positive, but I think that this occurs when I have let my fingers rest on the key modifiers for a while (shift, ctrl, alt).  I use Emacs and also try to use keyboard shortcuts in X and elsewhere, so I often have my fingers on the modifier keys as I pause to read something or decide what to do.  

The problem is fixed if I log out and log back in.  I suspect that simply restarting X would do it, but I've been using GDM, so X starts on login.  

I'm using enlightenment, though I don't know if this is a WM issue (restarting enlightenment without restarting X doesn't fix it), and X issue, a hardware issue (?) or what.  At this point, I'd be happy if someone could just give me a workaround less inconvenient than logging out.  I've been experiencing this bug about half a dozen times a day, more if I use my computer more.  Very annoying!

(By the way, if I switch to a virtual console -- which is hard, since the modifier keys act up when this bug hits -- the keyboard acts normal.)

---

### Post by nmyrick on 2013-01-23
I don't use 12.10, but here is just a thought.  Maybe your keyboard settings are automatically going to 'slow keys' if you rest your finger too heavily on a key for too long.  Have you checked your keyboard settings when this is happening? Your keyboard settings should be in the 'preferences' menu.

---

### Post by tgalati4 on 2013-01-23
Open a terminal and run xev.  Put the mouse in the small, white window, then open gedit or some other text editor and start typing.  Notice the keypresses in the console that are captured by xev.  Down presses and releases are recorded along with keycodes and what symbol they represent.  If you get lots of unpressed keys, take note of the value by hitting scroll-lock to freeze the scrolling.  Could be a dirty keyboard.  Have you turned the keyboard upside down and batted it to release the dirt?

---

### Post by dino99 on 2013-01-23
That issue is quite common: most of the time the key pressed is disturbed by dust, small piece of food, .... all kind of crap ....

so handle the keyboard upside down, check it, pulse compressed air or everything else to clean it a bit.

---

### Post by Phiwum on 2013-01-23
> **dino99 said:**
> That issue is quite common: most of the time the key pressed is disturbed by dust, small piece of food, .... all kind of crap ....

so handle the keyboard upside down, check it, pulse compressed air or everything else to clean it a bit.

I don't think that's it.  It's not consistent with the symptoms that (1) I have no problem when I switch to a virtual console and (2) the problem in X goes away without fail when I log out and back in.

---

### Post by Phiwum on 2013-01-23
> **nmyrick said:**
> I don't use 12.10, but here is just a thought.  Maybe your keyboard settings are automatically going to 'slow keys' if you rest your finger too heavily on  a key for too long.  Have you checked your keyboard settings when this is happening? Your keyboard settings should be in the 'preferences' menu.

That sounds like something to look at, but I'm using an alternate WM.  Which "preferences" menu do you have in mind and I'll try to find it.  Is this a gnome thing?  Is there a way to reach these settings from the command line?

Thanks.

---

### Post by Impavidus on 2013-01-23
This could be in the accessibility settings: Settings>accessibility>keyboard or something like that.

---

### Post by Phiwum on 2013-01-25
> **Impavidus said:**
> This could be in the accessibility settings: Settings>accessibility>keyboard or something like that.

That's it!  Messing about with those settings seems to have fixed the issue.

---

