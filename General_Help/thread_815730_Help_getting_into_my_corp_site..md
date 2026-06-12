---
title: "Help getting into my corp site."
date: 2008-06-01
forum: General Help
---

### Post by Chlorine Tablet on 2008-06-01
I work for Darden restaurants, ie Red Lobster, Olive Garden, etc. At any rate, I'm having problems logging into the corp. site. Using Vista I wasn't able to log on because of a loopback error it caused with the ports that were being used. XP I had to patch via [;884020"]KB884020]("http://support.microsoft.com/default.aspx?scid=kb;[LN) patch for loopback address range error.
The company doesn't support Vista or IE7. I've changed over to Hardy this week and I've installed IEs4Linux. I followed [these]("http://ubuntuforums.org/showthread.php?p=3447377#post3447377") to install JVM. It's kinda working, but I get the flashing error...still don't know how to solve that....anyways that isn't the problem.

The issue is that when I log into the site it loads up their modules for scheduling and other such things. When opening these modules it goes through the normal IE security screens, accept all the" way through....but no luck. It's saying the same thing when I use Vista. You do not have the permissions to change the host file." Which is the same error you get for the loopback error in vista or IE7.

The company refuses to support anything new. I hate Vista and won't be going back EVER. So, I would like to fix this problem from within Hardy if I could.

---

### Post by SirPerigrin on 2008-06-01
You say they don't support IE7 (Who can blame them?) but you didn't mention what they DO support. Could you simply use Firefox? Probably a dumb question but you didn't leave much information.

---

### Post by Chlorine Tablet on 2008-06-03
After I went to bed last night I thought I should have added much more to my post. Sorry about that.

They support all IE other than 7. Firefox doesn't work unless you use IE tab. Actually tab works assuming you use XP. The loopback error with Vista makes it impossible to use correctly. 

Each of the modules listens into a address and port on my computer. The loopback error makes it block the information in and out through those addresses and ports. 

Using the patch on XP solves the errors you recieve.

When I log into the site it tries to load the modules, as I said before. It then fails and continues the log in process without the modules. If I was simply checking on the emails or something simple then it would allow me fully. However because the whole point of the using the remote log in is to do schedules or to do my truck orders from home, checking email really isn't on the top of my priorities.

I can't seem to get any help from them with even Vista or any other newer windows product. Honestly that doesn't surprise me, but I just want to be at home at some point to finsh up work. Rather than drive 30 mins each time I have to do one tiny thing.

---

### Post by SirPerigrin on 2008-06-03
Well, their stuff seems so jerry rigged i dont have a clue how to fix it, but i do have a solution to getting into their site from linux in a kinda roundabout way.

Rather than try to make this work from linux, i keep a VirtualBox Virtual Machine of W2K or XP around to run those apps that just wont run in Linux. VirtualBox is Free and in the repository's, however i recommend the version on the VBox website. This would allow you to run IE6 right on your Linux desktop via Seamless Mode. 

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by AngryBash on 2008-06-03
Could you not install Wine? Then install an older version of IE onto that?

---

### Post by SirPerigrin on 2008-06-03
Thats what IEs4Linux is, he is saying it didn't work

---

### Post by Chlorine Tablet on 2008-06-03
I'll try out the virtual box you were talking about tonight and let you know how it goes.

---

