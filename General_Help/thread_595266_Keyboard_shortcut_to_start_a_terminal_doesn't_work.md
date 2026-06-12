---
title: "Keyboard shortcut to start a terminal doesn't work"
date: 2007-10-28
forum: General Help
---

### Post by Excalibre on 2007-10-28
So all the other keyboard shortcut settings in "Keyboard Shortcuts" seem to work, but the one to Start a Terminal doesn't. I'd like to bind that to one of my shortcut keys, but no dice.

---

### Post by ed-koala on 2007-10-28
Which shortcut are you trying to map it to?

Lots of things could be interfering with it ... some other action already mapped, compiz might have that shortcut (if you have compiz), keyboard layout can affect things (as I found out helping someone else with shortcuts), and so on.  Please give as much info as you can and we'll try to get ya going.  :)

---

### Post by Excalibre on 2007-10-28
Uh, it says "0xec". It's one of those media keyboard buttons. I can successfully map it to several other actions (launch mail program, launch browser, etc), but that particular action doesn't do anything, either with this keyboard button or any normal key combination I attach to it. Note that Ubuntu successfully - automatically - mapped the volume and mute keys to those actions. It's just this one "open terminal" action doesn't seem to work no matter what key I try to attach it to.

And yeah, I am running compiz. Does that have something to do with it?

---

### Post by ed-koala on 2007-10-28
Compiz shouldn't be interfering with it.  Mapping a shortcut to open terminal works fine for me.  Since everything else works fine, I'd hesitate to change things like keyboard layout option or other things.

Perhaps as a mouse shortcut you can add Terminal to the panel, so it is only a click away.

Anyone else have any ideas?

---

### Post by avik on 2007-10-28
The same thing happened to me.  I don't know if I ever got it working, but Compiz already has its own Terminal shortcut.  By default, its Control-Alt-M.  You can change it in the Compiz preferences under General Options->Actions if you have CCSM.

---

### Post by Excalibre on 2007-10-28
Yeah, okay, if I add a key to the Compiz one, it works, but I can't seem to map the keyboard buttons to it.

I already have it on my panel. I mean, it's not something I can't possibly live without, but it would be really nice.

---

### Post by falkaholic on 2008-03-07
Found this in a pre-post search.

I had the exact same problem. Terminal wouldnt open via keystroke. I had set it in the basic Keyboard Shortcuts panel. It stopped working around the same time I installed compiz advanced settings. I think a reboot it was actually put it into action, blocking  the Terminal keystroke. I tried other keystrokes for Terminal but none worked.

Anyway, looks like avik was right. The General Options has the same option and appears to override the system one with no warning; even though it was set to Disabled.

It would be nice if Gnome had a more standard/central keystroke control. Maybe I'll write it when I get better at programming.

Let this be found by future troubleshooters.

---

