---
title: "Emesene always shows at centre of screen"
date: 2008-05-24
forum: General Help
---

### Post by initialxy on 2008-05-24
Hello all,
I just started using emesene on my xubuntu 8.10 and i'm loving this thing so far. however there is only one thing that bothers me. everytime i launch emesene, it always shows up at the centre of my screen. but i would like to stay at the right side of screen kinda like a panel. so i drag it to my right side, close it and launch again, it still shows up at centre.

Does anyone know how to fix this? pidgin didn't seem to behave this way. but i really need offline messenging feature of emesene.

Thanks, 
any help is appreciated.

---

### Post by treris on 2008-05-31
I have the same problem, I've been looking through the various config files, but somehow have not been able to fix it yet.

I didn't encounter this problem in Gutsy, btw, did you?

Otherwise nice little app, certainly equal to pidgin if you're only using msn. Integrates much better than aMSN, but has less features and is less advanced imho.

If I find a cure I'll let you know

---

### Post by Zorael on 2008-05-31
I'm not getting this, but then I'm using an svn version (rev 1388) and not the one available from the repositories. It can be installed alongside your current version if you want to try it out.

[http://emesene.org/trac/wiki/SVN](http://emesene.org/trac/wiki/SVN)

---

### Post by treris on 2008-05-31
I've just installed the svn version, was not a hard thing to do indeed, just had to recreate the launcher in the menu. 
BUTTT, the problem is still there unfortunately. Strangely enough the problem only occurs with me when I have no other windows maximized. As soon as I have another window open, maximized or not, emesene opens up right where I want it to.

Quit strange behavior really, but of course not a real showstopper or anything, just annoying

---

### Post by initialxy on 2008-10-18
Thanks for replying, appreciated.

I got pretty annoyed at this issue and decided to take a look at emesene's source code. I soon discovered that emesene will reset itself to the centre of the screen when either previously recorded x or y coordinate of the main window is 0 or less. In my case, I removed the top tool bar and snapped emesene main window to the right top corner causing y = 0. That's why it resets the main window to centre all the time. Many people probably didn't remove the top tool bar or didn't snap the main window to either top or left edge of the screen, so they didn't get what I mentioned. I'd consider this as a bug in emesene since it doesn't make much sense to me (at least in common sense).

I'd like to offer a fix. You will have to edit emesene's source code (located under /usr/share/emesene by default). Open MainWindow.py, around line 134, change it from...

```

    def show(self):
        '''Shows itself'''
        if not (self.x <= 0 or self.y <= 0):
            self.move(self.x, self.y)
        gtk.Window.show(self)

```

to...

```

    def show(self):
        '''Shows itself'''
        if not (self.x < 0 or self.y < 0):  # Fix for snapping main window
            self.move(self.x, self.y)
        gtk.Window.show(self)

```

Since it's Python, you just need to close emesene and start again for changes to take effects.

I might check emesene's SVN and post a bug report, but I'm feeling kind of lazy... Anyways thanks again for helping.

---

