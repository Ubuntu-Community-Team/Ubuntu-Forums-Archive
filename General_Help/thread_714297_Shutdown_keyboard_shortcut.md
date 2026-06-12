---
title: "Shutdown keyboard shortcut"
date: 2008-03-03
forum: General Help
---

### Post by b4rt on 2008-03-03
Hello,

My goal today was to create a keyboard shortcut (for my IR remote control) to be able to shutdown my computer (using that remote). Any ideas?
I'm using Ubuntu 7.10 with GNOME desktop environment.

Thanks in advance,

Bart Goyens, Belgium

---

### Post by SpaceTeddy on 2008-03-04
just a guess - can lirc to that ? it is not exactly gnome... but i think it can do it... maybe :)

---

### Post by gfixler on 2008-03-04
You can make your own hotkeys in the Configuration Editor, which should be in Applications->System Tools->Configuration Editor, or just run it from a shell:
```
$ gconf-editor
```

Under /apps/metacity/keybinding_commands, you can put in a shutdown command for any of the numbered commands, and in the global_keybindings section next to that, put in your hotkey (use <Shift>, <Control>, <Alt>, and <Super> (Windows key) to indicate those), and that should do it.

The downside is that I think the only two ways of shutting down from a command like that are:
```
$ sudo halt
```
and
```
$ sudo shutdown -h now
```
meaning you have to be root, meaning you probably have to enter your password to do it, which kills the point of the remote. Perhaps someone can fill in some details to help out here.

---

### Post by gfixler on 2008-03-04
I thought I'd add that unrelatedly, I was looking at a tutorial on the new TrueCrypt GUI for Gutsy, and found a way to turn off the need for a password for certain specified apps, or utilities. I'm sure this isn't recommended from a security standpoint for halt, and shutdown, but hey, it's your machine :)

[How to remove sudo's need for a password]("http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10-p2"). Just modify the TrueCrypt specific parts to your needs.

---

### Post by b4rt on 2008-03-05
Thanks for the tips,

It worked!

Greets!

---

