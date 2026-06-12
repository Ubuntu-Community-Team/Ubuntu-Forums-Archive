---
title: "Autoindent in Nano"
date: 2007-03-16
forum: General Help
---

### Post by SBFC on 2007-03-16
Hello all. I was wondering if someone could help me out with getting autoindent to work in Nano.

I have 'set autoindent' in my .nanorc file, and inside Nano press M-I which displays 'Autoindent enabled', yet no autoindents are performed.

I can't figure out why this is...

If it helps, I'm editing a Python script.

Maybe I should clarify a lil bit, and now that I think about it, perhaps 'autoindent' in Nano isn't what I'm used to. I was hoping that after declaring a function the cursor would be automatically indented after hitting a carriage return following a ':'. But now after messing around, 'autoindent' in Nano seems that the cursor is still indented after making a carriage return following an indented line.

So, it's not possible to set it up to automatically be indented when hitting return when following a ':'?

---

### Post by lloyd_b on 2007-03-17
AFAIK, "nano" is not "code aware" - it doesn't know anything about the accepted indentation rules for a given programming language.  As I understand it (from the man page - I uses nano only very rarely), "auto-indent" just means that if a line is indented, then the line following it will be indented by the same amount.

If you install the "vim" package, and then modify the ".vimrc" to enable syntax highlighting, then it will automatically do "code aware" indentation.  The only problem with "vim" is that it does have a fairly steep learning curve (but, in my opinion, is well worth the effort for a developer).

Lloyd B.

---

### Post by SBFC on 2007-03-19
Thank you for your reply. I shall work on learning vim. I've used it, but only briefly, and obviously not in a real attempt to utilize it's features.

---

### Post by fragos on 2007-03-19
If you don't need to be using the terminal and command line, Gedit has that feature.

---

