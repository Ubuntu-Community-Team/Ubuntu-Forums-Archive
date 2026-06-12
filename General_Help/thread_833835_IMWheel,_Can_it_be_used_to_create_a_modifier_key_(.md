---
title: "IMWheel, Can it be used to create a modifier key? (Such as holding down Alt?)"
date: 2008-06-19
forum: General Help
---

### Post by Leefmc on 2008-06-19
Well, i've gotten IMWheel to work with my MX Revolution, but alas, it seems unable to hold down a key such as holding down Thumb1 to hold down Alt, or Shift.

Is it possible to create a thumb button as an Alt/shift/ctrl? with IMWheel?

Ubuntu seriously needs some proper mouse and general input management. This should not be this hard.. :/

---

### Post by cubeist on 2008-06-19
> **Leefmc said:**
> Well, i've gotten IMWheel to work with my MX Revolution, but alas, it seems unable to hold down a key such as holding down Thumb1 to hold down Alt, or Shift.

Is it possible to create a thumb button as an Alt/shift/ctrl? with IMWheel?

Ubuntu seriously needs some proper mouse and general input management. This should not be this hard.. :/


see the link in my signature... since you already have your mouse working you can skip to the imwheelrc section...


But for quick reference, here is what an entry in your .imwheelrc would look like:

```
"^[Nn]autilus"
None, Thumb1, Alt_L|Left
None, Thumb2, Button1, 2

```

---

### Post by Leefmc on 2008-06-19
Yea, and that works fine, the problem is that is not a standalone modifier. Heck, thats not even holding down a button, that is a "Once Repeated Button". If you try to hold down any of the buttons, do they work? Can you bind a button to "h" and hold it down with a result of "hhhhhhhhhhhhhhh"? I haven't been able to, and more importantly, i haven't been able to bind one of the buttons to a modifier (Ctrl/Alt/Shift) and have it work the way a modifier _needs_ to work, by holding it down.

I'm thinking its flat out impossible, because if you look at the man page for imwheel, you'll see there are 3 optional arguments. Repeats, Time before Release, Time before Next Release. The arguments themselves seem to hint that there is no ability to hold a button down, as imwheel will only fire it once and immediately release (unless you specify a time requirement before releasing).


Can you confirm if its possible to hold a modifier down? I already spent several hours on this damn thing and i'd hate to spend more, if its not even possible. You seem to know how to use it, so care to illuminate my question? :)

Man, such a simple thing has been so insanely hard. My MX Revolution.. and hell, all extra button mice, are useless to me until this gets fixed. "Holding Down" a button is a **_requirement_** for me, i use it for holding pie menus(popup menus) open in certain applications, etc.

---

### Post by cubeist on 2008-06-20
> **Leefmc said:**
> Yea, and that works fine, the problem is that is not a standalone modifier. Heck, thats not even holding down a button, that is a "Once Repeated Button". If you try to hold down any of the buttons, do they work? Can you bind a button to "h" and hold it down with a result of "hhhhhhhhhhhhhhh"? I haven't been able to, and more importantly, i haven't been able to bind one of the buttons to a modifier (Ctrl/Alt/Shift) and have it work the way a modifier _needs_ to work, by holding it down.

I'm thinking its flat out impossible, because if you look at the man page for imwheel, you'll see there are 3 optional arguments. Repeats, Time before Release, Time before Next Release. The arguments themselves seem to hint that there is no ability to hold a button down, as imwheel will only fire it once and immediately release (unless you specify a time requirement before releasing).


Can you confirm if its possible to hold a modifier down? I already spent several hours on this damn thing and i'd hate to spend more, if its not even possible. You seem to know how to use it, so care to illuminate my question? :)

Man, such a simple thing has been so insanely hard. My MX Revolution.. and hell, all extra button mice, are useless to me until this gets fixed. "Holding Down" a button is a **_requirement_** for me, i use it for holding pie menus(popup menus) open in certain applications, etc.

I hear ya, mice in linux are one of the most frustrating things... I went years without being able to use my extra buttons.

If I understand you, you want to map your extra buttons to hold a modifier down (just like holding the shift or alt key down on the keyboard)

This is really easy!  For example, if I want to type the letter "a" continiously with my thumb button by holding it down (same as on the keyboard), your .imwheelrc entry should look like:
```
"^[Gg]edit"
None, Thumb1, a, enter

```

ps. - the only reason I use the ^[] to begin the name of a program is it seems foolproof compared to some of the other methods out there...

cheers

---

### Post by Leefmc on 2008-06-21
bah, my hopes were so high :o.

Still no luck man. I can ofcourse make the a key print 500 lines, but while holding the Shift_L command and typing, it does not make anything uppercase.

Infact it only once, briefly did that, but not even consistently. I held down that button, typed maybe 30 letters, and it captitolized three of them. Note that right after, to make sure i pressed the "a" button (i have them bound to thumb1 and thumb2) to make sure it was working, and indeed, i got 500 "a"s.

Here is my code:
```

".*"
None, Thumb2, a, enter
None, Thumb1, Shift_L, enter

```
Note that "a" works in both of these, to prove that Thumb1 does indeed work.
```

".*"
None, Thumb1, a, enter
None, Thumb2, Shift_L, enter

```

---

### Post by cubeist on 2008-06-22
I am sure this can be done, but not directly in imwheel.  Try reading through the man pages for xmodmap.  Especially the section on keysyms/keycodes.  It may require some trial and error.

Also, I don't know what program you want to use this for, but several programs have built-in key commands, such as blender and the gimp, probably others too...

---

