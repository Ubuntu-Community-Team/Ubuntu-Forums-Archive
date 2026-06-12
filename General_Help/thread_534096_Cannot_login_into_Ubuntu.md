---
title: "Cannot login into Ubuntu"
date: 2007-08-24
forum: General Help
---

### Post by hirotani on 2007-08-24
hi wonder if someone can help?  I tried to log into my ubuntu machine at the login screen - I enter id & pword - the screen goes blank and after a few minutes I am back at the login screen and it will not let me on.

Oddly - I can log onto the Ubuntu box from my mac using ssh - using the same id & pword that the Ubuntu login screen refuses to accept.  

My data looks fine and I will back it up now - so if worse comes to the worse I will just scrub the machine and install a clean version of Feisty.  But that seems a bit defeatist if you know what I mean.   

The last thing I remember doing directly on the Ubuntu box was about 4 days ago.  I backed up files from an external disk connected to my mac onto the Ubuntu box  using scp.  It worked fine - no issues.  When I logged into Ubuntu on that day it worked fine and the system pulled some updates - some of which did not work.  Maybe the problem??

Any help would be appreciated.  I did read through a raft of "problem with login screen" posts but could see no solutions to those posts. So here's hoping.  

I am running Ubuntu 6. 

Thanks,

---

### Post by Tatty on 2007-08-24
How much space do you have left on your hard disk?  I had exactly the same problem with my first ubuntu installation when i ran out of space...

---

### Post by mssever on 2007-08-24
Do you get an error message? If so, what?

Also, errors that come up when logging in via GDM are logged in ~/.xsession-errors. There might be something useful there. Your problem isn't your ability to log in, else SSH wouldn't work. Your problem is probably related to Xorg and/or Gnome.

---

### Post by zach12 on 2007-08-24
Try loging in on fallsafe gnome and see if you can get in. If you can then log in and it may work
have fun!!!

ps this worked on my dapper(6.06) lappy

---

### Post by hirotani on 2007-08-26
Many thanks to you three for coming back to me - very much appreciate it.  

Tatty - you hit the spot,  I got in got in via ssh, did a df -h and found the drive to be 99%++ full!  In an effort to be better over backing up my mac.  I had backup my iTunes library (abt 52G) - twice by accident!!  Once I deleted one of the copies - the machine logged on as usual.

Thanks again.

John.

---

### Post by glotz on 2007-08-26
Why does the login need diskspace? I think this is a serious (if rather uncommon) bug.

---

### Post by mssever on 2007-08-26
> **glotz said:**
> Why does the login need diskspace? I think this is a serious (if rather uncommon) bug.

Certain session-related data is stored on disk instead of in memory. Some examples are ~/.ICEauthority and ~/.Xauthority.

---

### Post by glotz on 2007-08-27
I see. Couldn't some diskspace be reserved for this purpose? I mean we're talking about very small things here in terms of space and very large issues in terms of usability. Here we have two guys who've actually been "burned" by this. To me this could be one of those things that "make lunix so very hard to use". ;)

---

### Post by mssever on 2007-08-27
> **glotz said:**
> I see. Couldn't some diskspace be reserved for this purpose? I mean we're talking about very small things here in terms of space and very large issues in terms of usability. Here we have two guys who've actually been "burned" by this. To me this could be one of those things that "make lunix so very hard to use". ;)
That's a good idea in theory, but I wonder how it would work in practice. The question is, how would you reserve the space? My first thought was to implement it in the kernel, which is what it would take to enforce such a restriction. However, the problem with that is that this issue can only affect those who use X; taking disk space from those who don't use X would be the Wrong Thing.

If you try to implement this in X--or in Gnome or KDE--how do you know if the disk fills up when X isn't able to regulate it? That was the OP's problem.

Perhaps the best way to handle this is to do what Ubuntu already does: Notify the user when the disk usage reaches a certain threshold. It can't account for every situation, but I don't think that a perfect solution is possible.

---

### Post by glotz on 2007-08-27
How about something creates a 200k file at login and deletes it at logout?

---

### Post by mssever on 2007-08-27
> **glotz said:**
> How about something creates a 200k file at login and deletes it at logout?

Or perhaps the other way around; create the file at logout and delete it at login. Perhaps someone should file a bug about this. A discussion here won't get it implemented.

I'm not sure where to file such a bug, though. Launchpad.net?

---

### Post by jamvegan on 2007-08-27
In other versions of linux (Red Hat, for instance) there is a mechanism in place to prevent root from completely running out of space and being unable to login and perform necessary functions.  I do not know what that mechanism is, but perhaps Ubuntu should apply it to regular users, since we do not, as a general rule, ever log in as root.

---

### Post by forestpixie on 2007-08-27
maybe suggest it at the gutsy [idea]("http://ubuntuforums.org/forumdisplay.php?f=253") pool

---

