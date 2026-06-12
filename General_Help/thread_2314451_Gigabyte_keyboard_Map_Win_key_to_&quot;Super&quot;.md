---
title: "Gigabyte keyboard: Map Win key to &quot;Super&quot; action"
date: 2016-02-21
forum: General Help
---

### Post by sergio38 on 2016-02-21
Hi!

I would like to know what is happening with my keyboard. I run Ubuntu 15.10 with a Gigabyte Force K7 keyboard, Wireless.

With any other keyboards I can use the Windows key to access the Dash, but here I can't.

Do you know how to do it? I've tried addiing a custom shortcut via System->Keyboard. But even when configuring the shortcut by pressing the key, it seems like Ubuntu even recognizing it as a key. If I press the Windows key, it does nothing. But if then I press enter, it tells me "Error, this key can't be used because it is used for other things...etc" So no clue

Thank you!

---

### Post by egeezer on 2016-02-21
In a terminal,type
```
xev
```
A small white window will appear.  Set the cursor in there (you'll see a lot of scrolling of text going on) and press the Win key.

You will see two blocks of text that begin with Keypress event - these are what the computer "sees" when the key is pressed.

If there is no such block, the computer does not recognize the key.

If the block shows "Super_L", it properly recognizes the key.

If the block shows something else, that is what the key does on your particular box.

---

