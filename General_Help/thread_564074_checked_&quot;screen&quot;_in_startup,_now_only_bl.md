---
title: "checked &quot;screen&quot; in startup, now only black at startup HELP!!!"
date: 2007-09-30
forum: General Help
---

### Post by roughstart on 2007-09-30
I clicked startup to view what was loading and saw that screen and some other option weren't checked, I checked them both and rebooted because I was trying to configure some sound problems before that and thought maybe a reboot would help. Anyway, I get the black screen of death instead of the login screen. Any way I can revert this from the console?

Thanks,

---

### Post by roughstart on 2007-09-30
Thanks for the help.....not...

---

### Post by xoce on 2007-10-01
I have this trouble too. After install Ati Proprietary drive and reboot, I see black screen. Video-Ati Radeon X1950XT (256mb)

---

### Post by random_user on 2007-10-01
I know this doesn't help at all, but just letting you know you probably aren't alone. I checked something (allowing administrators to log in locally), and then restarted my system after major 74 updates and now my log in screen will not show up...it just loads for infinity.  So I am interested in this thread and to see a solution to this. I mention the "allowing admins" thing because of a post I found which seemed similar to my problem:

[http://ubuntuforums.org/archive/index.php/t-477786.html](http://ubuntuforums.org/archive/index.php/t-477786.html)

So I didn't check "screen", but I am probably getting the same issue. Hopefully a simple fix! I'd hate to have to completely re-install.  Are you using Gutsy by the way?

---

### Post by roughstart on 2007-10-01
Found a quick fix. Easy as pie, long as it aint mincemeat.....
Oh, and I'm runny Feisty.

Just load the live CD and let it load up completely. Then, after it's done, play in it a bit, doesn't matter if you change settings or not, it's the CD, can't modify it. Just look for some info you need or whatever and then restart the system. Take the live CD out and that should take care of the problem.

Looks like whatever damage I'd done to the kernel had been repaired by just running the platform from the CD. It did seem like, after the 2nd boot, that the problem had "reoccurred" , but I rebooted it and it's fine again. Strange....but hey I'm back on lol....


Hope this helps.

---

### Post by random_user on 2007-10-01
Unfortunately that may not help me, since I'm on gutsy I don't have a live CD....if there is one available I guess I can always download it :) 

In the meantime...you wouldn't happen to be aware of where the log-in information is written to in the filesystem? 

I figure I can probably nano into the file that contains a line ..something like (probably far-fetched, but gets idea across):

AllowAdminLocalLogin = true

and then I can change it to false..or something like that.  Anyone have an idea? Glad to hear you got your issue fixed though!

---

