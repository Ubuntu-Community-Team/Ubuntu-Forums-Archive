---
title: "terminal issue"
date: 2018-12-02
forum: General Help
---

### Post by cmcanulty on 2018-12-02
The last few days no matter how I open a terminal I can't type right away. There is a small empty box and I have to click in the terminal and then the empty box changes to a filled in box and I can type. Is there a way to prevent this? I am attaching a screenshot of the empty box. I can't get a screenshot of the filled in box. Thank you

[ATTACH=CONFIG]281856[/ATTACH]

---

### Post by CatKiller on 2018-12-02
There's not a lot to go on there, but the behaviour you're describing is that the window doesn't have focus. If you Alt-Tab away from the window you'll see exactly the same thing.

As to how you're launching things without them automatically getting focus, I have no idea. I haven't used Xfce in a long time.

---

### Post by cmcanulty on 2018-12-02
That was it, why it changed all the sudden is a mystery. I went to settings-window manager- and checked automatically give focus to newly created windows and it is working fine now. I find the focus settings pretty obtuse as their are several options in Window Manager Tweaks and several more in Window Manger. I am attaching 2 screenshots in case someone wants to explain them. Thanks

[ATTACH=CONFIG]281859[/ATTACH]

[ATTACH=CONFIG]281860[/ATTACH]

---

### Post by Impavidus on 2018-12-02
I had something similar a few days back. With multiple overlapping xfce-terminals, changing workspaces, I sometimes found a terminal with an open cursor as if it didn't have focus. However, the colour of the title bar showed it had focus and I could type. I can't reproduce it right now.

---

