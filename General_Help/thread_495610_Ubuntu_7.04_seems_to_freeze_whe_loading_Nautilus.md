---
title: "Ubuntu 7.04 seems to freeze whe loading Nautilus"
date: 2007-07-08
forum: General Help
---

### Post by mister harbies on 2007-07-08
Ubuntu 7.04 seems to freeze when loading Nautilus (during splash screen).

And then I can't do anything. I have to click on the splash screen, and then it loads up. After a minute or so, it just without warning logs out....

The only thing I can do is login failsafe gnome, and I have control over the computer. 

What I think I might have changed was an xclient file which I did by going to the sessions option in preferences and saving the current session?

Im kinda new to hall this, so some help would be great

Thanks

---

### Post by OzzyFrank on 2007-07-08
Note sure if this will be of any help, since my problem seemed to be a crappy Compiz update affecting Metacity and Gnome, and seems to have been fixed up with another update. However, things were pretty bad but there were some work arounds, as you can read here:

[http://ubuntuforums.org/showthread.php?t=489206](http://ubuntuforums.org/showthread.php?t=489206)

Having other desktop environments installed is good insurance for times like this, or at least good for troubleshooting. If you don't have that luxury, I strongly suggest trying the boot options outlined in the thread. Good luck!

---

### Post by mister harbies on 2007-07-08
I am still havin g problems. I have uninstalled nautilus, or I think I did and tried thunar... logged in and nautilus seems to still be there and the computer still hangs trying to load nautilus.

Is there somewhere I can find a startup script to post here and be looked at?

---

### Post by mister harbies on 2007-07-08
oh and I should point out that I am also running beryl, but I have isolated that from being a problem.

---

### Post by zero244 on 2007-07-08
That is an odd problem. I havent heard to many stability problems with Nautilus before. There are several posts here with Feisty having some stability problems.
Are you sure its not beryl related......beryl is not setup right can be unstable.
Right now I have beryl running rock solid.
But I have had my share of beryl problems in the past.
I dont think you can uninstall Nautilus its built into the OS pretty well. In fact it might cause a problem if you did uninstall it.
Does thunar run ok or does it freeze up too.?
Sorry I cant help anymore.

---

### Post by mister harbies on 2007-07-09
thunar runs okay if I run it in xfce mode. Maybe it is not to do with nautilus? It might be gnome?

The system froze when I was trying to download some files using synaptic. Control, alt backspace was not working so used the reset button. Had a problem with a broken install, but had that fixed. Might be something to do with that, but it was only games I was downloading. Not system files, so.

---

### Post by mister harbies on 2007-07-11
Ahh! I found a fix in another thread.

All I did was change the ~/.gnome2/session file to ~/.gnome2.session.old and a new one was created on start up.

All is fine and dandy. I think the problem was when I tried to install the splash screen manager which required that I change some 'gnome' files. It was the gnome that did it!

Until my next problem.... ciao

---

### Post by OzzyFrank on 2007-07-13
Did you open both files to see what the differences were? I'd be interested to see what it was, as it was something in particular trying to load, not so much Gnome doing it (but reacting to it).

---

