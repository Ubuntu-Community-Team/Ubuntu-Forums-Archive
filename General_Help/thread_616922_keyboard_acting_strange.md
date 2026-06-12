---
title: "keyboard acting strange"
date: 2007-11-18
forum: General Help
---

### Post by tbrothers on 2007-11-18
There are certain keys that require me to press the space key before they appear.  For example, when I press the tilda ~ key it does not display until I press the space key.

I hope that make sense.

The keys affected are the tilda, single and double quotes (~ " ' )

Again, I press the single quote key and nothing happens.  The cursor does not move nor does the single quote appear.  But as soon as I press the space key it appears.  At this point I continue typing as normal until I need to type one of the 3 key again.

This happens in all applications including Firefox, text editor, terminals, etc.

Any ideas?

Thanks,
Terry

---

### Post by geraldm on 2007-11-19
A simple way was to test under different editors, which you have done, apparently confirming the behavior.  Another way is to start an xterm program, and in it type
```

xev

```
Another window containing a small square will appear.  Put the mouse pointer inside the small square.  Then type the keys whose code you are having problems with tilde, single quote,
double quote, and space.  The code that those keys produce will appear in the xterm window.
If it produces no code, it will tell.  You would be expecting two bytes for the space, I suppose.
Check it anyway.  To exit the program, change focus to the xterm window, and type CTRL + C

If you need to change any keys, use xmodmap.  The manpage has information.

Gerald

---

