---
title: "Mapping Game Keys"
date: 2007-02-06
forum: General Help
---

### Post by r0pe on 2007-02-06
I just got a Merc Gaming Keyboard and I'm having trouble getting the game keys to work. How can I bind the arrow keys to W A S and D? I have been able to get keys to bind with programs but I don't know how to bind them to other keys. Any help would be appreciated. Thanks.

---

### Post by daou on 2007-02-06
xmodmap will let you map certain keys to other ones.

have a look at the xmodmap manual:
[http://www.xfree86.org/4.2.0/xmodmap.1.html#sect5]("http://www.xfree86.org/4.2.0/xmodmap.1.html#sect5")

You can place xmodmap commands in your ~/.Xmodmap file and they should automatically load. Or you can temporarily bind them with the xmodmap command. Use xev to find out what the keycode of the button is that you want to bind the arrow keys to.

example command in your terminal:

```
xmodmap -e "keysym KP_Left = XX"
```

temporarily binds left arrow to keycode XX.
or just add the line to the .Xmodmap file:

```
keysym KP_Left = XX
```

---

### Post by r0pe on 2007-02-07
Thanks for that, daou. I got all the keys configured with xmodmap but most of them don't repeat making them useless for gaming. Is there a way to make these keys repeat like normal ones?

---

### Post by daou on 2007-02-08
Good point... you could try xbindkeys and xvkbd. It's a bit more of a hassle but should allow repeats.
You need to install xbindkeys and xvkbd.

Then make a ~/.xbindkeysrc file and add lines in there. For example,

> "xvkbd -xsendevent -text "w""
c:98

This outputs "w" when I press the up key. 98 is the keycode xev gave me. I tested it and holding it down repeats the character.

Have a closer look at the [xvkbd manual]("http://homepage3.nifty.com/tsato/xvkbd/") and [xbindkeys manual]("http://hocwp.free.fr/xbindkeys/xbindkeys.html"). With xvkbd you can also change repeat delays etc.

To make the config file work, you either need to add xbindkeys to your startup programs or run "xbindkeys &" whenever you want the buttons mapped and "killall xbindkeys" when you want to stop them.

---

