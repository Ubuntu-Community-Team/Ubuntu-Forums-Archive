---
title: "Mono freeze my computer while copying to clipboard"
date: 2013-07-14
forum: General Help
---

### Post by honeycup on 2013-07-14
I installed Keepass 2.21 on my Ubuntu 13.04 Laptop. The Keepass Window is freezing the whole System almost one time a day after I copied a password to the clipboard. Its not only with a special password, it could happen while copying everything from that program. That wouldnt be a big problem, but xkill isnt working then. The Keepass Windows will stay in the front, movies/music will continue playing normally so the system is working. If I press the "windows button" on my keyboard the menue is opening and when I press ALT+F2 I can enter xkill, but nothing happend. Before the windows is freezing I can use xkill to close Keepass, so generally it works.
The only thing I can so after the windows is freezing is to restart ubuntu. Do you have a solution for this fault?

---

### Post by honeycup on 2013-07-15
Nobody can help me? Got the same error some minutes ago :(

---

### Post by honeycup on 2013-07-18
What a pity. Ubuntu is really buggy for me.

---

### Post by ufbh on 2013-08-22
Same problem: Ubuntu 13.04 freezes after copying to clipboard with Keepass 2.21 since a few days.

---

### Post by D0ckW0rka on 2013-08-23
Same problem: (X)Ubuntu 13.04 freezes randomly (doesn't always freeze, sometimes it works) after copying to clipboard with Keepass 2.21.

---

### Post by sven4 on 2014-03-14
I have the same problem. While I haven't found a way to prevent the freeze from happening, I did find a way to "unfreeze" X.

If KeePass freezes X, press <Ctrl>-<Alt>-<F1> to switch to the text console. Then press <Alt>-<F7> to switch back to X. The window manager is responsive again.

I use Fluxbox and that's the only WM I tested with. I don't see a reason why it wouldn't work with GNOME, but YMMV :)

---

