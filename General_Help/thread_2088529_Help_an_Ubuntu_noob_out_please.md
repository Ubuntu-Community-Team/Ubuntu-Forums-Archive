---
title: "Help an Ubuntu noob out please"
date: 2012-11-26
forum: General Help
---

### Post by Suisami on 2012-11-26
Alright. I've been a windows user for about a decade. I tried Ubuntu once about 3 years ago, but ended up going back because I didn't like using emulates for my games. Now I have a laptop that I'm not using for gaming, and it needed an OP. So I used Ubuntu because its free. And unfortunately, Ubuntu's UI has changed dramatically. 

My laptop is ridiculously slow. By slow I mean unnecessarily, averaging about 3 to 7 secs to open most windows of any sort. Now I'm trying to tweak it to be less hard on my computer,  and have spent 4 hours trying to change it to LXDE because I couldn't figure out the newer interface. 

Now, LXDE has made a noticeable improvement. But I want to go as far as possible. Please help me by telling me the most effective ways I can maximize my computers performance. I'm not computer illiterate, but I have limited experience with the computer jargon, so please take this into account.

My computer specs are:

Dell Inspiron 1300 
Intel Celeron(R) M processor 1.40GHz
60 gig hardrive 
502.0 MiB of RAM

Current Memory usage
133.2 MiB (27.2%) of 488.3 MiB

Swap
24.1 MiB (4.8%) of 502.0 MiB

Obviously this is a low end laptop. Upgrading is not an option at this time. I'm looking for a supercomputer, just one that's functional for browsing the internet and basic takes like storing videos and pictures and occasionally writing. Please and thank you.

---

### Post by blackbird34 on 2012-11-26
(a little more hassle) Maybe you could do a fresh install of Lubuntu - it is Ubuntu with LXDE, and all the programs associated with it. It sounds like you installed plain Ubuntu and tacked on LXDE after, so there might be some extra stuff running. 

For much less hassle, if you want it to run quite a lot (I believe) faster, you could choose to run the computer with only a Window manager at the login screen - LXDE is based on a WM called Openbox and you can choose it: you'll only get a blank desktop as baseline, with everything accessed through the right-click menu.

Welcome back and don't hesitate to post back for more info :D

---

### Post by ibjsb4 on 2012-11-26
You seem to be using swap even though you have free ram.  This can slow things down.  To see if this is a problem, [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo sysctl vm.swappiness=0

This will temporary force your system to use ram first and will work until you reboot.  Then it will reset to default.  To make the change permanent:

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

Edit: Also like blackbird34 said, pure lubuntu is better.

---

