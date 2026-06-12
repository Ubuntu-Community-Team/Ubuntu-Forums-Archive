---
title: "[SOLVED] How do I edit the us English layout(with dead keys)?"
date: 2007-10-01
forum: General Help
---

### Post by holihue on 2007-10-01
I need to edit the US. English (with dead keys) layout.

I have a English keyboard, and I want Norwegian keys.
And I've been using US English (with dead keys) for a while now. But when I'm programming in python I got one annoying thing:

The dead key changes from ' and ", to ´ and ¨.:(

So to get ' or ", I need to click RightAlt + ' or ".


Can someone explain me what to do?
I've searched for this, but I did not understand what to do to switch back the ' and ".


Thanks.

---

### Post by distroman on 2007-10-01
System > Preferences > Keyboard / Layouts / Add

No?

---

### Post by holihue on 2007-10-03
> **distroman said:**
> System > Preferences > Keyboard / Layouts / Add



I have done that, but the *U.S. English International (with dead keys)* have changed two keys (important in Python) and I really need these keys.

I have a English keyboard, and I need some Norwegian characters too.
If I change the layout to Norwegian, it will slow down when I'm typing...


What I need is to change these two characters (look in my first post).

---

### Post by ricardisimo on 2007-10-03
I'd love to be able to edit US International to get rid of the dead keys altogether, replacing them all with 3rd level - the <ALT> keys preferably. The layout of the characters is perfect. I just find the "dead" aspect tedious and annoying. I'm subscribing to this thread in the hopes you find something.

---

### Post by holihue on 2007-10-03
> **ricardisimo said:**
> I'm subscribing to this thread in the hopes you find something.


me too...:)

---

### Post by distroman on 2007-10-03
Ohh heh, I hope you get a solution :)

---

### Post by dabl on 2007-10-03
This will probably go over like a lead balloon, but I'll put it out there ....

Kubuntu has the "Regional & Language>Keyboard Layout" feature that lets you "add" a national keyboard layout, such as Norwegian, to your default layout.  It puts a flag of the "current" national layout on your taskbar, and if you click it, it toggles to the other ones that you have added.  So, it happens that once in a while I need the German umlauts, so I have the German layout added, and so when I click the US flag, it will toggle to the German flag and I can then use the appropriate keys (nearest to what a German keyboard would have) to produce the ö, or Ü, or whatever that I need.

:)

---

### Post by ricardisimo on 2007-10-03
It seems that in your situation this solution is perfect. I would imagine that you need the ü maybe once a day or less, so switching layouts momentarily is perfectly acceptable. My situation is different; I and everyone in my family are completely bilingual, so every other sentence - and sometimes every other word - can be either Spanish or English.

The characters in US Intl. w/ dead keys fall perfectly: ñ is either just <ALT>+n, or "~","n", where "~" is the dead key; á is either <ALT>+a or "´" followed by an "a". Perhaps you see the obvious problem: why should I put up with the annoying dead keys if <ALT>+[letter] gives me exactly what I need? Plus, I have way too many typos this way, where I get "Mary&#347;" instead of "Mary's", or ÿes" instead of "yes". If I don't <SPACE> the dead key alive I get some third option.

Thanks

---

### Post by holihue on 2007-10-04
I have been using the dead keys a while now, and (almost) every thing is perfect...

but instead of ' and " as the first key, it is ´ and ¨.
and to get ' and " I need to click RightAlt + ' or ".
That is my problem.
I want to just change that to get ´ and ¨(which I never use), I need to click RightAlt ' or " key.

I hope it is just to edit a simple text file to edit where the characters is.

---

### Post by holihue on 2007-10-15
I changed the /etc/X11/xkb/symbols/us file.:)

[Here is the tutorial I used.]("http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html")

---

### Post by ricardisimo on 2008-05-17
Someone upstairs may have been reading this thread; I finally installed Hardy on one of my machines and the layout altgr-intl (or gr-alt-intl?) appears to be exactly what I was looking for. Quotes are quotes and tildes are tildes, with no need to hit <SPACE> after them to activate the character. If you want a "special" character you hit <ALT>+something.

Nice work, whoever you are! Sadly I can't yet install Hardy on this comp, but soon, hopefully.

---

