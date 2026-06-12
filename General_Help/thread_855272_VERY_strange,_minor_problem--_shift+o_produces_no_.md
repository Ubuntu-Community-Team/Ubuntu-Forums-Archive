---
title: "VERY strange, minor problem-- shift+o produces no text."
date: 2008-07-10
forum: General Help
---

### Post by maoglone on 2008-07-10
Really weird, right?  The "o" key works, and the shift key works with every other key on the keyboard except for "o."  The capslock works with no glitches, but for some reason, I can't produce a capital o with the shift key--in fact, when I enter the combination, nothing happens.  I've never heard of this sort of problem on any computer, and I wouldn't even know where to begin to try to fix it.  

I'm using a Compaq c500t series running 8.04.  This is the only problem I've had since installing hardy.

---

### Post by maoglone on 2008-07-10
Bumpski...

---

### Post by SPr on 2008-07-10
I wonder if it's something to do with the keyboard. Plug in one you know that works or plug the suspect one into another computer to see what happens.

---

### Post by Execute_Method on 2008-07-10
> **SPr said:**
> I wonder if it's something to do with the keyboard. Plug in one you know that works or plug the suspect one into another computer to see what happens.

+1 keyboards are made in an array, so it is possible to have 2 keys that work individually and not combined. I suspect it is probably your keyboard.

BTW
Do you have any global shortcuts associated with those keys?

---

### Post by maoglone on 2008-07-10
> **SPr said:**
> I wonder if it's something to do with the keyboard. Plug in one you know that works or plug the suspect one into another computer to see what happens.

It's a notebook that I'm using, so I can't plug it into another, but I can plug another one into mine.  

I'm going to go back through all my keyboard shortcuts to make sure I don't have something weird set up w/ that combo.  I was close to arriving at that idea when I saw it in this thread.  Thanks for that.

---

### Post by editrix on 2008-07-10
There's a program called xev which you run from the terminal and it's supposed to tell you what's happening when you press a key.

I just tried it with Shift-o and didn't understand one thing, but then again I didn't RTFM :-)

Anyway, you might want to explore it. It *may* tell you what's going on.

Oh. And I seem to have xev installed by default, so you probably do, too.

---

### Post by maoglone on 2008-07-10
SOlved, sOmehOw.  I turned compiz off and then turned it back on.  Don't know what I had set as shift+o, but it must've been in there.  *facepalm*

---

### Post by MasterXandrex on 2008-07-10
You may want to look into your compiz settings, you could have a shortcut key associated incorrectly and the restart may have disabled the module -- or you could simply hope you're lucky enough that it won't happen again. :D


Xan

---

