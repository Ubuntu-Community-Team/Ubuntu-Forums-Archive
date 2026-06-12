---
title: "Ubuntu doesn't see the Gx keys"
date: 2014-10-22
forum: General Help
---

### Post by Ktost on 2014-10-22
Hey guys, I bought a new keyboard (A4Tech X7 G800V) that has 15 additional G keys. The problem is, Ubuntu doesn't see them when I'm pressing them. For example I have tried to assign G1 to 'Show workspace 1' shortcut, but Ubuntu didn't notice the key. Can you help me?

---

### Post by JazzPotato on 2014-10-22
Do the G keys trigger keypress events when you run 
```

xev

```
in a terminal?

---

### Post by Ktost on 2014-10-22
> **JazzPotato said:**
> Do the G keys trigger keypress events when you run 
```

xev

```
in a terminal?
No, they don't.

---

### Post by JazzPotato on 2014-10-22
Unfortunately I myself can't help you further in that case, perhaps you could try some more googling? (Some casual searches on my part revealed similar articles to this: [https://help.ubuntu.com/community/MultimediaKeys](https://help.ubuntu.com/community/MultimediaKeys) )

Sorry I couldn't help more

---

### Post by tgalati4 on 2014-10-22
You can use the *setkeycodes* command to assign scan codes to keycodes then use *xmodmap* to map keycodes to actions.

```
man setkeycodes
```

You can search *setkeycodes* and *xmodmap* in the forums for other examples.  Here's how I got 23 extra keys to work on an old HP multimedia keyboard:  [http://ubuntuforums.org/showthread.php?t=921870&highlight=setkeycodes](http://ubuntuforums.org/showthread.php?t=921870&highlight=setkeycodes)

It's an old thread, but the basic procedure is the same.  Post the procedure that finally works for you.

It will take a few tries to get it set up.  Everything is fixable.  It just takes patience.

Some keys will not remap, regardless of how hard you try.  These keys tend to be controlled by the BIOS (ACPI specifically) and some of them can be altered by changing the action scripts in /etc/acpi and /etc/acpi/events.  Other keys require a proprietary Windows driver to interpret the gibberish they produce when pressed--which means you will have little luck getting them to do anything in Linux.

---

### Post by Ktost on 2014-11-11
Bump, still don't know how to fix.
But I have drivers on Windows, and I was able to asign shortcuts to these keys, like I could asign CTRL+C to G1 etc and it works on Ubuntu too.

---

