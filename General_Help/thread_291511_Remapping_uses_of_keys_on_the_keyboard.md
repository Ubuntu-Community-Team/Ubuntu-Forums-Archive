---
title: "Remapping uses of keys on the keyboard"
date: 2006-11-02
forum: General Help
---

### Post by benuski on 2006-11-02
How would I go about remapping say, my windows key, to some other purpose?  I ask because my cat jumped up on my keyboard and broke my backspace key, which now pops off every three or four times I use it, making it very annoying for me to type, as it gives me way more typos than I'm used to.
Thanks!

---

### Post by benuski on 2006-11-02
Anyone, anyone? Bueller?

---

### Post by chriscando on 2006-11-02
You might want to read about xmodmap.
I use it to remap some keys for my music.
What I did is type: xev in a terminal and put the mouse over the screen that pops up. Type the button you want to remap and look for the keycode number.
Then make a file with something like this:
```
keycode 123 = e
```
then run xmodmap file_with_mapping and you will have another button that works as 'e'

I think xmodmap is what you are looking for, there is plenty of info out there.

Hope this helps, let me know if you want me to clairify

---

