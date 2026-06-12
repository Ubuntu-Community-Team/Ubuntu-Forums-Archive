---
title: "overide default ubuntu keyboard shortcuts"
date: 2008-01-25
forum: General Help
---

### Post by c_emery on 2008-01-25
I recently installed ubuntu 7.10 gutsy on my dell laptop and have been incredibly happy with the experience (I use Debian Etch at work and all I can say is wow, what a difference).

One small annoyance I've been trying to resolve is a missing option in Pidgin to open my buddy list with a keyboard shortcut (ctrl-b). I found an item in the pidgin release notes that hints at the cause:

Removed keyboard shortcut preferences for ctrl-B/I/U; enabled by
default, but won't interfere with bindings set by the GTK theme

In the default gnome theme, ctrl-b is bound the the 'make shortcut' dialog for nautilus. I am assuming I need to either remove or override this binding in a gtk config someplace or something, but haven't been able to find the file or format to use.

btw. I have looked in the System, Preferences, Keyboard shortcuts menu, ctrl-b isn't defined there. 

Thanks for any help,

---

### Post by c_emery on 2008-01-28
bump.

I find it hard to believe that it is impossible to override this keybinding. 

Someone on this list must know where Ctrl-b is being set to open nautilus... please?

A workaround that provides an alternate keybinding for opening pidgin buddy list would also be ok (though I suspect more difficult and not necessarily ubuntu specific).

---

### Post by c_emery on 2008-01-31
Ok, for anyone who stumbles upon this post with a similar problem, I was able to get Ctrl-b mapped to open the buddy list in pidgin. 

This option is available in a package called pidgin-hotkeys which adds a plugin to pidgin which allows you to configure global hotkeys.

---

