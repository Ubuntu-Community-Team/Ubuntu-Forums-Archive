---
title: "Keyboard problem"
date: 2019-11-05
forum: General Help
---

### Post by letyphon on 2019-11-05
[COLOR=#000000][INDENT]Hello everyone,

I use a Turkish keyboard, except one problem everything is as I used to have in windows. The problem is the letters with grave accent which is [SIZE=5]([/SIZE] [SIZE=5][COLOR=#000000]**`**[/COLOR][/SIZE] [SIZE=5])[/SIZE] like this letter [B][SIZE=4]À[/SIZE], [B][SIZE=4]à[/SIZE].
[/B][/B]On my turkish keyboard normally this letter is typed by the combination of [SIZE=3]**alt gr + ` + a **[SIZE=2]you can see it in the picture attached. But when I do this combination what I get is two characters of **[SIZE=4]`a[/SIZE]** instead of a single character of [/SIZE][/SIZE][B][B][SIZE=4]à.
[/SIZE][/B][/B]
How can I fix this, If someone has any idea, I really appreciate it, if not I think I will go back to use windows :sad:

For the image of the combination that I'm talking about please open the link below.

[https://ibb.co/F0Q7ft1](https://ibb.co/F0Q7ft1)[/INDENT]
[/COLOR]

---

### Post by CatKiller on 2019-11-05
The key you're interested in is the Compose key, since it composes a glyph from parts. The default Compose key in many desktop environments - the ones that set it - is AltGr, but it can be changed to whatever you want. The means to configure the Compose key depends on which desktop environment you're using.

---

### Post by letyphon on 2019-11-05
So how can I change it ? I tried to do it with Tweaks application but it's still the same. Normally when I push the alt gr (compose key) button + the accent button (`) it should show me nothing until I push the letter a and then it should give me an [SIZE=3]**à**[/SIZE].

In this case as soon as I push the alt gr (compose key) and the accent button, it creates this ( ` ) on the screen.

---

### Post by CatKiller on 2019-11-05
In KDE and Cinnamon, which I use, it's just one of the keyboard layout settings. I don't use Gnome.

---

### Post by Holger_Gehrke on 2019-11-05
alt-gr+accent gives just the accent. alt-gr+shift+accent gives a 'dead' accent which gets combined with the next key pressed if possible. See the file /usr/share/X11/xkb/symbols/tr for details, that's the definition for the Turkish keyboard.

Holger

---

### Post by letyphon on 2019-11-06
> **Holger_Gehrke said:**
> alt-gr+accent gives just the accent. alt-gr+shift+accent gives a 'dead' accent which gets combined with the next key pressed if possible. See the file /usr/share/X11/xkb/symbols/tr for details, that's the definition for the Turkish keyboard.

Holger

Thank you so much alt-gr+shift+accent it works :)

---

