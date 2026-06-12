---
title: "Notification area not working."
date: 2008-01-15
forum: General Help
---

### Post by shafin on 2008-01-15
I am using Ubuntu 7.10 Gutsy. Recently icons in the notification area are not responding. A right click on any of these icons only displays the menu that applies to the notification area.Sometimes one or two icons work,but most of the times,none works.I am having considerable trouble running apps like pidgin,deluge,stardict etc. If I remove the notification area and then add it again the problem remains.

Please help.

I dont know if the [other problem I am having with Gnome panel]("http://ubuntuforums.org/showthread.php?p=4140808#post4140808") is related to this one.

---

### Post by reyasuk on 2008-01-15
Wish I could help but I am suffering the same problem and haven't solved it yet.  I've also got a problem with amsn and that's how I noticed the icons in the notification area were not responding.  I've seen a few others mention of this in the last couple of days and I'm wondering if it's a recent update.  I'm still learning how to use linux so I hope someone with more experience will come to the rescue. ](*,)

---

### Post by shafin on 2008-01-15
I also think it was a recent update,it has started after I updated last time

In the meantime,I'm using AWN with its core applets.You can try it too.

---

### Post by era506 on 2008-01-15
Hi!!! I'm having the same problem with the notification area and the window list (the problem you linked above), they seem to be related. I'm using Linux Mint 4.0 and the problem started when I accidentaly removed the notification area, when I add it back it didn't respond, then after rebooting the problem persisted but this time the window list wasn't working either, I can just minimize and unminimize the first window in the list but I can't do it with the rest and the previews are there but if click on the list it is like if I had clicked an empty panel area. At the notification area some apps work sometimes but almost all the time they don't. I'm desperate and I wan't my panel working again! (I really don't want to use awn or something else...) HELP!!

---

### Post by era506 on 2008-01-17
Seems like the "Show desktop" applet is not working either!!!! And mintMenu some times, though it works again after killall gnome-panel, window list and notification area still don't work. Meanwhile I'm using Trayer and AWN... :(

---

### Post by snakerbot on 2008-01-20
I'm having the exact same problems.  The notification area doesn't work, and the window list won't let me select anything other than the first window.  I haven't even removed either and had to replace them.  They just stopped working.  I'm using ubuntu gutsy.  I actually reinstalled ubuntu earlier in the day, because this happened before.  I only got my graphics card running properly yesterday, so I didn't think it would be a big deal to just get the drivers and follow the tutorial again, but since it happened again, I don't want to reinstall this time.

---

### Post by chaosrl on 2008-01-25
Blah. I've just experienced the same problem, but it appears that it did happen after the last update. I updated yesterday (I think, if my memory serves me correctly), and today when I booted up it stopped working. Has anyone come up with a fix for this?

---

### Post by era506 on 2008-01-25
Nop, the problem is still there, I'm desesperate!!!

---

### Post by reyasuk on 2008-01-25
I'm still looking for an answer but I have now realised that if there's just one icon in the notification area it will respond normally.  However any other additions do not work.  Just wondering if the size of the notification area would have anything to do with it, and where would the size be set? :confused:

---

### Post by chaosrl on 2008-01-25
Mine doesn't even work with just one. It's weird and quite annoying, as i had it working just yesterday.

---

### Post by chaosrl on 2008-01-29
I hate to do this, but I have to bump this thread. Has anyone found a solution to this yet?

---

### Post by reyasuk on 2008-01-29
Still haven't found an answer for this, only people with the same problem!  Two days ago it started working again and I could access all icons in the notification area.  Then yesterday nothing worked yesterday, and this morning only two are working at the moment. Very strange :confused:

---

### Post by reyasuk on 2008-01-29
Someone suggested that I turn compiz off and that fixed my problems.  The notification area works and the two programs causing problems also started responding to the mouse.  I turned compiz back on with all plugins disabled and then, switching on those I use one by one, I found that it was Freely Transformable Windows that was the main cause of the problems for me.  The programs affected were amsn and todiscgui.  I still not sure that amsn is working consistently but at least I know where to look now. :)
Hope this might give a clue for others to investigate.
Jen

---

### Post by era506 on 2008-01-29
It has to be freewins!!! I disable it, restart and everything is working great now!!!

---

### Post by chaosrl on 2008-01-29
well. reyasuk, you're absolutely fantastic! freewins was doing it for me too (and while it's a cool thing to have, it's just a piece of "i can do this and you can't" for me). disabling it gave me my notification area back! THANKs!

---

### Post by era506 on 2008-01-29
Thanks reyasuk!! I have my mintMenu, window list and notification area working again!!! 
Should we report this bug to freewins creator? Maybe he/she can fix it, I like to have it activated to say to my friends "i can do this and you can't" !

---

### Post by chaosrl on 2008-01-30
I do think that we should contact the creator of freewins. I'm not sure how to fiel a bug report, but I've gone on the Compiz Community Forums and found warlock, who I believe to be the creator of freewins, and pm'd him. I do think it's a cool show-off feature to have, just for kicks. :) But of course, the notification tray is more important. :P

---

### Post by chewearn on 2008-01-30
Thanks *reyasuk* !  This problem has been driving me crazy for a while now.

---

### Post by reyasuk on 2008-01-30
I have just found this post in the compiz fusion forum and added my comment to it.  My thanks go to Michael on the ubuntu-uk mailing list for his solution. :)

[http://forum.compiz-fusion.org/showthread.php?t=6839](http://forum.compiz-fusion.org/showthread.php?t=6839)

---

### Post by shafin on 2008-01-31
I got the solution in the compiz fusion forum today and came back to see the situation here.Seems like you guys got it too.

BTW,I really loved freewin.Hope they'll fix this bug.

---

### Post by SmSpillaz on 2008-02-08
It's fixed in the latest git version of freewins. It's a problem with the input shaping and other windows not sending resize notifies properly. You should file a bug with the creators of offending applications.

To enable the fix, just disable 'shape input' and reload the plugin and reload your windows. This, unfortunately however disables the touted 'input shaping' features where input is restricted to the area of where it seems the window is.

---

### Post by lsd_us3r on 2008-04-15
> **reyasuk said:**
> Someone suggested that I turn compiz off and that fixed my problems.  The notification area works and the two programs causing problems also started responding to the mouse.  I turned compiz back on with all plugins disabled and then, switching on those I use one by one, I found that it was Freely Transformable Windows that was the main cause of the problems for me.  The programs affected were amsn and todiscgui.  I still not sure that amsn is working consistently but at least I know where to look now. :)
Hope this might give a clue for others to investigate.
Jen

thanks

---

