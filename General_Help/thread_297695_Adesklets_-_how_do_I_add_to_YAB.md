---
title: "Adesklets - how do I add to YAB ?"
date: 2006-11-11
forum: General Help
---

### Post by zami on 2006-11-11
I've got adesklets yab (yet another bar) running but I'm having a horrible time adding to it.

What I THINK is the pertinent info in the conf.txt file is

 'icons': [('emacs.png', 'GNU Emacs', 'emacs'),
           ('firefox.png', 'Firefox', 'firefox'),
           ('gimp.png', 'The GIMP', 'gimp'),
           ('terminal.png', 'Terminal', 'xterm'),
           ('xmms.png', 'XMMS', 'xmms')]}

So, I would ASSUME that I could simply add to that list in the same format, like so -

 'icons': [('thingy.png', 'Thingy', 'thingy'),
           ('emacs.png', 'GNU Emacs', 'emacs'),
           ('firefox.png', 'Firefox', 'firefox'),
           ('gimp.png', 'The GIMP', 'gimp'),
           ('terminal.png', 'Terminal', 'xterm'),
           ('xmms.png', 'XMMS', 'xmms')]}
but... apparently I can't.

Does this bar only hold five launchers?  Is there a setting elswhere in the configuration file I'm missing?

All the other changes I've made to the config.txt (colors, icon size, etc) I save, then restart the bar, and so far that's gone fine.

But everytime I try to add a launcher to that list, the bar just never comes back and I have to go through "killall -e adesklets" and "adesklets --nautilus" again from the terminal, after deleting the launcher I tried to add.  

blaadablablada!!  I've been wrestling with this and a gdesklets toolbar too, for a solid hour now.  Making me crazy!

Any help would be appreciated!

-zami

---

### Post by zami on 2006-11-11
Alow me to talk to myself a moment here.

::clears throat::

I figured out my problem.  For anyone else who stumbles across this post with the same problem, the solution is that you can not have the same icon (.png at least) in the list twice.

For example:
Below is me trying to set up two shortcuts to folders in my home directory called "Pics" and "Misc".
```

 'icons': [('folder.png', 'Misc', 'nautilus Misc'),
           ('folder.png', 'Pictures', 'nautilus Pics'),
           ]}
```
Crashes the yab.


```

 'icons': [('folder.png', 'Misc', 'nautilus Misc'),
           ('folder2.png', 'Pictures', 'nautilus Pics'),
           ]}
```
Loves the yab.

You can apparently have a title or command listed twice, just not an icon.
Having a bogus icon will also crash the yab.

Might I add... I now LOVE the yab.  :D  Much more configurable then anything I found from gdesklets.

-zami

---

