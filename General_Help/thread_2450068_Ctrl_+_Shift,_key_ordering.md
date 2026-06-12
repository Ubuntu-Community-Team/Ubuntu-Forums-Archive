---
title: "Ctrl + Shift, key ordering"
date: 2020-09-06
forum: General Help
---

### Post by oreo-u on 2020-09-06
The behaviour of pressing Ctrl first and then Shfit key is different from Shift first and then Ctrl. i.e. in the text editor, the prior will select new line (Ctrl then Shift then Up Arrow), while the latter (Shift then Ctrl then Up Arrow) does nothing.
Is there a way to change them to behave the same? somewhere in settings?
Thanks!

Edit: Check out xev. Solved by turning off "Locate Pointer" in Settings > Universal Access. I'm using Ubuntu 20.04.1 LTS.
Thanks again!

---

### Post by The Cog on 2020-09-07
I have never heard of that before. What version/flavour of Ubuntu are you using, and what editor?

---

### Post by Impavidus on 2020-09-07
What text editor?

I see no difference between ctrl, then shift, or shift, then ctrl in mousepad or an input box in firefox, but in principle any application is free to make a distinction. I once made a game that discriminates between left and right shift and ctrl (it made sense: left shift+n &#8594; open the doors on the left side of your vehicle, right shift+n &#8594; open the doors on the right, left shift+right shift+n &#8594; open all doors). It could be a limitation of your keyboard. Some keyboards are wired in such a way that they cannot detect all imaginable combinations of keypresses.

Use **xev** to see what keypresses your systems detects.

---

### Post by oreo-u on 2020-09-07
Thanks for replying! I am using a fresh install of Ubuntu 20.04.1 LTS, OS Type 64-bit, GNOME Version 3.36.3, and Windowing System X11.
It happens in the default editor that comes with the install, and also in Sublime text.

---

### Post by oreo-u on 2020-09-07
Thanks for pointing me to xev.
It turns out that my Left-Ctrl key press triggers a FocusOut event. Whenever Ctrl is hit after Shift it cancels any key combination I am using.
To solve this I turned off Locate Pointer in Settings > Universal Access > Pointing & Clicking.
Ha Thank you!

---

### Post by The Cog on 2020-09-08
Nice one. Thanks for the explanation - others may well find this thread useful.
You can mark the thread solved by the pull-down "Thread Tools" menu, top right.

---

