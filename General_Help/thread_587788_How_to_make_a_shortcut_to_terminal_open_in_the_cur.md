---
title: "How to make a shortcut to terminal open in the current folder (just like KDE's F4)"
date: 2007-10-23
forum: General Help
---

### Post by bernardobraga on 2007-10-23
Hello guys,

I already got a right-click-open terminal in place shortcut, I've also got a keyboard terminal shortcut that opens the terminal in Desktop. What I need is a **keyboard** shortcut to open a terminal in the current folder, just like KDE's F4 key. Is there a way to do such thing in nautilus?
I'm using ubuntu 7.10
thank you.

---

### Post by ihcnet on 2007-10-23
I've never actually done this, but you should find this post helpful.
 [http://ubuntuforums.org/showthread.php?t=42404](http://ubuntuforums.org/showthread.php?t=42404)

---

### Post by dayvy on 2007-10-23
I believe this is what your want:

sudo aptitude install nautilus-open-terminal

d.

---

### Post by bernardobraga on 2007-10-23
dayvy, as I said, I already installed can open terminal by right clicking, I did it with nautilus-open-terminal. I want a **keyboard** shortcut. If there's not a way to make a keyboard shortcut with nautilus-open-terminal, that's not what I want.

In system>preferences>advanced desktop effect settings> general options I found that there is a terminal command line to start terminals, I know I can do "gnome-terminal --working-directory=DIRNAME" instead of DIRNAME is there a command so that it starts in the current folder?

I tried $1 but it opened the folder some other terminal was on... not the folder my nautilus was on.

---

### Post by bernardobraga on 2007-10-23
I look at nautilus-open-terminal source code, and realized it is not as simple as I imagined.
Is there a way to activate the script via keyboard, then?

---

### Post by bernardobraga on 2007-10-24
well I did a bit of research and I (hopefully mistakenly) concluded I'd have to hack into nautilus source code and somehow make a keyboard shortcut to run nautilus scripts...
Has anyone ever done that?
I love gnome but nautilus is such a pain...

---

### Post by strabes on 2007-10-24
You can create custom keyboard shortcuts using gconf editor. See [this page](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/) for more information.

---

### Post by bernardobraga on 2007-10-24
> **strabes said:**
> You can create custom keyboard shortcuts using gconf editor. See [this page](http://strabes.wordpress.com/2006/11/13/create-custom-keyboard-shortcuts-in-ubuntu/) for more information.
that page teaches how to make a keyboard shortcut. Doesn't say anything about opening a terminal in the same folder that the selected nautilus window is viewing.
Did you even read the thread?

---

### Post by tartley on 2008-06-19
Ah. I struggled with this for a while - none of the above answers seem to do it.

But finally I realised I can just use Nautilus "Alt-F T", which seems to do the right thing. If you have a directory selected, it opens terminal in that, otherwise in the current directory.

---

