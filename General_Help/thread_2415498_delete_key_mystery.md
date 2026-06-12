---
title: "delete key mystery"
date: 2019-03-26
forum: General Help
---

### Post by jgw on 2019-03-26
I noticed that my delete key, in the side block of my keyboard, doesn't work.  I then hooked up a different keyboard the same delete key didn't work.  One keyboard was an hp keyboard and the other is a dell.  I then tried one more keyboard to make sure.  I should also add that the delete key in the 6 key block (under the print screen, scrool lock and pause break keys DOES work!   I have no idea what is going on or how to fix it.  Seems that Ubuntu has cleverly stopped a delete key to no longer be accepted.

Thoughts?

---

### Post by him610 on 2019-03-26
No, Ubuntu did not cleverly disable the Delete key. I too have Dell and HP keyboards; the Delete key works on both.

In the terminal type a character, do not press Enter. If you place the cursor, using the left arrow key, under the character then press the Delete key, does it delete the character or not?

---

### Post by again? on 2019-03-26
Might seem obvious... but is numlock off.
Install numlockx if you have to ...
```
numlockx status
numlockx off
```

---

### Post by HermanAB on 2019-03-27
There is an obscure bug in X which causes it to sometimes forget a key.  I once had the T key disappear.  

The way I got it back, was to explicitly define it using xev and xmodmap.

---

### Post by jgw on 2019-03-27
thank you for the replies!

I found the answer!  I went to sudo dpkg-reconfigure keyboard-configuration and screwed up a keyboard (new problem to fix this one)  anyway, I was re-examining my settings and found that I had cleverly set the mouse keys to on universal setup <sigh>

I turned it off and got back my delete key!  (who would have guessed?)

I will mark this as solved.

---

