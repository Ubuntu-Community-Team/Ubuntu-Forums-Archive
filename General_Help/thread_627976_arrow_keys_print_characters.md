---
title: "arrow keys print characters"
date: 2007-11-30
forum: General Help
---

### Post by GreatestGravity on 2007-11-30
Hey everyone - 

I have a problem with my arrow keys. When in a terminal or in vim, sometimes when I hold down an arrow key, it starts printing characters. For example, if I hold down the right arrow key, it will sometimes go right one character and then start inserting the letter "C". (A for up arrow, and so on.)

Anybody have any idea why this could be?

---

### Post by arvevans on 2007-11-30
Maybe I can help.

Certain control keys (like the Arrow Keys) output keystroke sequences (multiple characters) instead of a single character.  Arrow keys are a good example.

In some editors, like vi, you can only move the cursor to locations that already have a character there.  If no character is in that location and you attempt to move the cursor there anyway, you will see all or part of the control sequence, usually the last character only because the initial character us usually a non-printing character.

Hope this helps.

Arv
_._

---

### Post by GreatestGravity on 2007-12-01
Nope, doesn't really help...

It's not localized to particular programs - I've had it do this to me on just the bash command-line, in octave or gnuplot command-line, when writing in pine through ssh, and so on... it doesn't happen at the ends of lines either, it happens in the middle. It's definitely inserting the last character of the control-character-sequence for that arrow key, but I don't know why it would do that insertion rather than moving the cursor, or why it's happening recently. (Could be either hardware slowly breaking, or the upgrade to gutsy that did it, or possibly something else.)

When I press the key slowly enough I don't get the problem as often, or when I don't hold down an arrow key...

---

### Post by arvevans on 2007-12-08
If you have a replacement keyboard, now might ba a good time to try it.

Also, go to System/Preferences/Keyboard (assuming you are running Gnome WM).  There you will find some control for keyboard speed.  If somehow this has gotten pushed way up to the top, this could be your problem.

Arv
_._

---

