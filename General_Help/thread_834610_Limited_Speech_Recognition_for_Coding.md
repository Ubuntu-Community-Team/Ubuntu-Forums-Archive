---
title: "Limited Speech Recognition for Coding"
date: 2008-06-19
forum: General Help
---

### Post by teich on 2008-06-19
Hi,

After some wrist trouble I've been looking into various speech recognition options for Ubuntu.  It would appear that there isn't much, and that writing something from scratch is quite difficult.  

I'd like to suggest a simpler first step.  The majority of my typing time is spent writing code in emacs, and I suspect the same is true for many of us.  This is a vastly simpler problem than general speech recognition as there is a very limited vocabulary: only those tokens that are valid within that block of code.  String literals and comments and such still need to be typed, but getting the sheer volume of typing down would be great.  

I'd imagine the workflow looking something like this: first, train the system on general-use commands like cursor movement, then on common tokens for the language you are programming in (i.e. "if", "for", "switch", "case", "return", etc.).  When writing a new function or declaring a new variable, you train the system to recognize that new word.  Speech recognition considers only words that correspond to variables declared in that block, legal function calls, cursor movement commands, and that sort of thing.  The vocabulary size would be way smaller and more manageable than commercial speech recognition software.

Also, I would guess that a hybrid speech recognition / normal typing system like this one for coding could be much faster than normal typing alone, making this perhaps interesting to all coders, not just those who have RSI.

Anyway just a thought.  Also, if anyone has suggestions about speech recognition for Ubuntu that work for them, please let me know.

Thanks.
teich

---

### Post by nikgare on 2008-06-19
Dragon Naturally Speaking 7 sorks under Wine here.
It seems to cope quite well with my strange accent!

---

