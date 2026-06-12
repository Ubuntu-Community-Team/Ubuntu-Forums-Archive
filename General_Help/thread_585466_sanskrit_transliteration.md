---
title: "sanskrit transliteration"
date: 2007-10-21
forum: General Help
---

### Post by amerikkanu on 2007-10-21
***Update***:  I recently posted a better solution in the [tips and tricks]("http://ubuntuforums.org/showthread.php?t=646207&highlight=sanskrit+transliteration") section than what's posted below.  I'd recommend trying that out instead, and resorting to the method below only if that one fails.

__________________________________________________

First, I should come clean:  I hate transliterated Sanskrit.  It's annoying to read and very inelegant compared with a cleverly designed syllabary like Devanagari.  And with great tools like scim/m17n, the wonder of unicode, and good &#2344;&#2366;&#2327;&#2352;&#2368; typesetting possibilities (various flavors of TeX, etc.), I would love never to have to see or use transliterated Sanskrit again.  But, unfortunately, it's still required for many scholarly publications, etc., and for westerners interested in Sanskritic culture but too busy to learn its script(s), it's still useful.

Here is a simple (copy and paste simple!) way to set your keyboard up for skt transliteration:  From [Steve Fraser]("http://www.esotericteaching.org/moodle/mod/forum/discuss.php?d=252"):

> Simply add the following to .Xmodmap in your home (~/) directory to activate them:

keycode 116 = Mode_switch
clear mod3
add mod3 = Mode_switch

keycode 38 = a A 0x01000101 0x01000100
keycode 31 = i I 0x0100012B 0x0100012A
keycode 39 = s S 0x01001E63 0x01001E62
keycode 30 = u U 0x0100016B 0x0100016A
keycode 40 = d D 0x01001E0D 0x01001E0C
keycode 43 = h H 0x01001E25 0x01001E24
keycode 46 = l L 0x01001E37 0x01001E36
keycode 58 = m M 0x01001E41 0x01001E40
keycode 57 = n N 0x01001E47 0x01001E46
keycode 27 = r R 0x01001E5B 0x01001E5A
keycode 28 = t T 0x01001E6D 0x01001E6C

keycode 10 = 1 exclam 0x01000310
keycode 11 = 2 at 0x0100015B 0x0100015A
keycode 12 = 3 numbersign 0x01001E45 0x01001E44
keycode 13 = 4 dollar 0x01001E5D 0x01001E5C
keycode 14 = 5 percent 0x010000F1 0x010000D1

Use the command xmodmap .Xmodmap to avoid restarting your desktop manager.

Of course, if, like me, you don't already have an .XModmap file, you can just open gedit and create a new one by saving it with that title in your home directory.  Unfortunately, the keyboard mapping is not all intuitive (using the numbers), but after the wasted time I've spent looking for a way to do this, I have no complaints!

See the following key; for capitals, just use shift plus the following combinations.  "RWin" means the right windows key.

&#257;     RWin + a
&#299;      RWin + i
&#363;     RWin + u
&#7771;     RWin + r
&#7773;     RWin + 4
&#7735;      RWin + l
&#7745;    RWin + m
&#7717;     RWin + h
&#7749;     RWin + 3
ñ     RWin + 5
&#7789;     RWin + t
&#7693;     RWin + d
&#7751;     RWin + n
&#347;     RWin + 2
&#7779;     RWin + s

Hope this is of use to other sanskritwalas out there.

---

### Post by amerikkanu on 2007-12-18
p.s. for those who don't have a right win key, you can map the same characters against the left win key by substituting "115" for "116" in the code above.

---

### Post by Arjunanda on 2007-12-22
For me the right win key (Menu-key) activates the right-click menu. I tried to diable that functionality, but did not succeed. Any ideas where the menu function can be disabled in order to enable this?

---

### Post by amerikkanu on 2008-01-01
I had the same problem on my laptop, which is why I was happy to find that you could simply use your left win key instead by substituting "115" for "116" in the code above (see previous msg.).  Now updating this thread to point to a better solution than this dead-key approach in the tips and tricks section.

---

