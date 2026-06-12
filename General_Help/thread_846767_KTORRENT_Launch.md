---
title: "KTORRENT Launch"
date: 2008-07-01
forum: General Help
---

### Post by ububaba on 2008-07-01
My **Ktorrent** has been working fine for months but suddenly yesterday something happened. 
Now when I click the icon on the panel it does not open. I can no more see which of the torrents 
are being downloaded or seeded.

I deleted **Ktorrent**, turned off the computer in between, re-installed the application through the 
**Terminal** but the situation remains the same. 

I installed even **BitTorrent** that too would not *open*. Any idea what has gone wrong?

---

### Post by qpieus on 2008-07-01
Open a terminal and type ktorrent at the prompt. If ktorrent does not open then you might see some error messages in the terminal window that will give some clue to what is wrong.

---

### Post by ububaba on 2008-07-02
> **qpieus said:**
> Open a terminal and type ktorrent at the prompt. If ktorrent does not open then you might see some error messages in the terminal window that will give some clue to what is wrong.

Thanks I did. The message is [COLOR="Blue"]"Ktorrent is already running!"[/COLOR]
That's all. No clue to the problem.

---

### Post by qpieus on 2008-07-02
That's strange. Is the ktorrent icon present near the clock? Perhaps ktorrent is set to load automatically when kde starts and it starts minimized?

---

### Post by ububaba on 2008-07-02
> **qpieus said:**
> That's strange. Is the ktorrent icon present near the clock? Perhaps ktorrent is set to load automatically when kde starts and it starts minimized?

The icon is there but when I do a left click nothing happens at all.
Right click gives one the possibility of Launching Ktorrent but it does 
not get launched. In launcher property it says[HTML]ktorrent %i %m -caption "%c" %u[/HTML]
Which, unfortunately does not say much to me. Where can one alter some value 
that it is not minimised automatically?

---

### Post by qpieus on 2008-07-02
ktorrent has a directory here:

~/.kde/share/apps/ktorrent

but in mine I did not see any kind of config file. Also, under the "configure ktorrent" menu selection I did not see any option for starting the app minimized.

I also browsed through the filesystem and did not see any other ktorrent config files.

You could try uninstalling ktorrent, then deleting the ~/.kde/share/apps/ktorrent directory, then reinstall ktorrent. Maybe there's something in that directory that's messed up. Browse through that directory before deleting - mine had some torrent caches in there that had downloaded file information. Better yet, rename the ~/.kde/share/apps/ktorrent directory so that you can restore it later if needed.

As far as autostarting applications, check in ~/.kde/Autostart and see if there is a ktorrent file there that would cause it to start automatically.

---

### Post by ububaba on 2008-07-02
I could not find any Ktorrent directory here[COLOR="DarkRed"] ~/.kde/share/apps/ktorrent[/COLOR]
but it is located here[COLOR="DarkRed"] /usr/share/apps/ktorrent[/COLOR] and as you said there is no possibility
to configure.

No Ktorrent in Autostart. I have done reinstalling as you said but it did not help.
Something else is wrong because when I click on Skype's icon it says an instance of
the application is already open....which I do not see.

---

### Post by qpieus on 2008-07-02
Well, I'm outta ideas :(  As you said, something else is causing this, it's not just a ktorrent problem if other apps are also affected.
Hopefully someone else will join in and help.

---

### Post by ububaba on 2008-07-02
Thanks anyway.

---

### Post by stoeptegel on 2008-07-04
Try $killall ktorrent

then see if you can restart ktorrent.

---

### Post by ububaba on 2008-07-04
> **stoeptegel said:**
> Try $killall ktorrent

then see if you can restart ktorrent.
```
 sudo killall -9 -r ktorrent;  ktorrent 1>/dev/null 2>/dev/null 
```
Some days back I tried the above but was no help.
however```
killall ktorrent
``` did the trick. Thanks

---

### Post by ububaba on 2008-07-07
Thanks for all the help.

---

