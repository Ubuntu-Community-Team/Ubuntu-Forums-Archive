---
title: "keystrokes in terminal"
date: 2007-09-13
forum: General Help
---

### Post by wrathkeg on 2007-09-13
Hi All.
I have Ubuntu at work, and when I press Ctrl+left cursor in the terminal, the cursor jumps back to the previous space.  Very nice.  But here at home, doing the same thing just generates ";5D" (no quotes).  Does anyone know why this should be?  Or, more importantly, how to fix it? As you'd imagine, it gets pretty frustrating.
TIA
Wk

---

### Post by codesplice on 2007-09-13
Are you using the same terminal at home and at work (ie, gnome-terminal, xterm, etc)?

---

### Post by mali2297 on 2007-09-13
Try *Alt + b* instead. That should work everywhere. (*Alt + f* to jump forward.)

---

### Post by wrathkeg on 2007-09-13
> **codesplice said:**
> Are you using the same terminal at home and at work (ie, gnome-terminal, xterm, etc)?
So far as I know, yes: I am using gnome-terminal on each (though I am not at work to check for certain)
[QUOTE=mali2297]Try Alt + b instead. That should work everywhere. (Alt + f to jump forward.)[/QUOTE]
Thanks for the suggestion.   In gnome-terminal, for me Alt+b opens up the Tab menu, though.  And in xterm, it gives me a letter "a", with a circumflex accent over the top.  Weird.
WK

---

### Post by mali2297 on 2007-09-13
I don't use Gnome (and hence not gnome-terminal) but it should be possible to edit the keyboard shortcuts. See here:
[http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-usage.html.en#gnome-terminal-shortcuts](http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-usage.html.en#gnome-terminal-shortcuts)
Try *Disable all menu access keys*.

(I noticed that the suggested keystroke doesn't work in xterm. You can instead type Esc and b in turn but that isn't very useful.)

---

### Post by aaaantoine on 2007-09-13
Ctrl+Left works in Tilda.  I'll have to remember that.  Pretty handy feature.

---

### Post by mali2297 on 2007-09-13
From [IBM's site]("http://www-128.ibm.com/developerworks/aix/library/au-satbash.html#N1006F") I found this:
> 
To set a binding, you must specify the key sequence and the command to be executed, separated by a colon, with the key sequence escaped by a double quote (in extreme circumstances, you might need to escape this again with a single quote). For example, to change Control-B to go backwards word by word, use $ bind "\C-b":backward-word.


@aaaantoine:
There are more handy keybindings, see here
[http://linuxhelp.blogspot.com/2005/08/bash-shell-shortcuts.html](http://linuxhelp.blogspot.com/2005/08/bash-shell-shortcuts.html)
.. or run *bind -P | less*.

---

### Post by bernardfrancois on 2008-01-12
The keybindings mentioned should work by default. One reason why they might not work is because of a broken user account.

I solved the problem by re-creating my user account. I described the steps I took in the following post:
[http://ubuntuforums.org/showpost.php?p=4121195&postcount=2](http://ubuntuforums.org/showpost.php?p=4121195&postcount=2)

---

