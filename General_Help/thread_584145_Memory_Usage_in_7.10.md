---
title: "Memory Usage in 7.10"
date: 2007-10-20
forum: General Help
---

### Post by SupWiz17 on 2007-10-20
I uprgaded to 7.10 yesterday and now ubuntu is using up alot more memory than it did before. The two biggest processes using memory are nautilus and xgl. I never had desktop effects activated before but now I have a few in compiz could that be the reason for so much memory being used all the time.

---

### Post by Gosha-Za on 2007-10-20
> **SupWiz17 said:**
> I uprgaded to 7.10 yesterday and now ubuntu is using up alot more memory than it did before. The two biggest processes using memory are nautilus and xgl. I never had desktop effects activated before but now I have a few in compiz could that be the reason for so much memory being used all the time.

Whoa. I was just going to make a topic about this.

I've been running Feisty for at while and had it as my OS-of-choice. And I looked forward to Gutsy and updated the same day as it came out. However I got really disappointed when I had updated it. My RAM usage is like, a fifth more than I had with feisty. And the RAM-cache is using about  50%.
I tried shutting the indexing-stuff off but it's not helping much.
Oh, also, I don't use xgl or compiz or whatever, just GNOME. It's simple and the special effects of course are cool but I end up getting annoyed by them.

So, now I use about 90% of my RAM just browsing internet, chatting, and having scite  and irssi running.

I mean... I could run Win2000 in Innotek VirtualBox at the same time before.

What are the new processes that waste RAM in Gutsy?
I don't really know which one, and how, I can shut down.

---

### Post by SupWiz17 on 2007-10-20
Yeah same here I am using 70% of my RAM just browsing the internet and using pidgin it is a bit ridicolous.

---

### Post by DoktorSeven on 2007-10-20
Desktop effects enabled will definitely make your RAM usage increase, but if you don't have it enabled, check the process list (**gnome-system-monitor**) in the Processes tab, sort by CPU and see what's hogging the system.  It might be some background process like a file indexer or something that can be disabled.

---

### Post by SupWiz17 on 2007-10-20
> **DoktorSeven said:**
> Desktop effects enabled will definitely make your RAM usage increase, but if you don't have it enabled, check the process list (**gnome-system-monitor**) in the Processes tab, sort by CPU and see what's hogging the system.  It might be some background process like a file indexer or something that can be disabled.
I will look into what I could disable but I just didnt think that desktop effects would take up this much memory.

---

### Post by Gosha-Za on 2007-10-20
> **DoktorSeven said:**
> Desktop effects enabled will definitely make your RAM usage increase, but if you don't have it enabled, check the process list (**gnome-system-monitor**) in the Processes tab, sort by CPU and see what's hogging the system.  It might be some background process like a file indexer or something that can be disabled.

I have looked into it. And I really can't tell what's eating so much. Those are the ones over 1 MB

> nautilus 18.8 MB
gnome-panel 7.5 MB
pidgin 6.5 MB
metacity 3.0
gweather-applet-2
nm-applet
mixer_applet2
multiload-applet2
trashapplet 916.9 KB
Well, trashapplet is not up to 1 MB, but it eats quite alot.

Also, how do I see what is eating the cache?

---

### Post by SupWiz17 on 2007-10-21
As I have let my computer sit it seems that the memory usage has gone down but I still think it is very high at about 50%.

---

### Post by Subban on 2007-10-21
If you can't see in the process list what is eating your RAM up, then as far as I am aware its likely to be just normal behavior,  using the RAM for disk caching etc ?

Linux just fills up the unused RAM with cache stuff to speed up accesses, but if the RAM is needed for a process it gets freed and used, I think the theory is that your RAM is better off doing something like caching when unused rather than sit empty and wasted (kinda like people :)) I would imagine stuff is going to be a little different in Gutsy than Fiesty was, but fundamentally the same.

---

### Post by Gosha-Za on 2007-10-21
> **Subban said:**
> If you can't see in the process list what is eating your RAM up, then as far as I am aware its likely to be just normal behavior,  using the RAM for disk caching etc ?

Linux just fills up the unused RAM with cache stuff to speed up accesses, but if the RAM is needed for a process it gets freed and used, I think the theory is that your RAM is better off doing something like caching when unused rather than sit empty and wasted (kinda like people :)) I would imagine stuff is going to be a little different in Gutsy than Fiesty was, but fundamentally the same.

I guess that's fine. But it apparently doesn't work too good. And I rather have an application taking four seconds to start up than waiting four seconds when I alt-tab.

What would the consequences be if I installed Feisty again?
Seems troublesome but I think I'll end up doing that actually. What I like with linux is that it is light-weight and that I can do alot of stuff at the same time.
Surfing and chatting at the same time is not even close to enough. Isn't that why there are two workspaces?
At least that's why I have two screens.

Would Feisty be hard to keep up-to-date?
Should I stick to some other distro that is more light-weight?
.... What can I do to speed up Gutsy?

---

### Post by SupWiz17 on 2007-10-21
I can see what is eating up my RAM the top 3 processes using up my RAM are either Firefox, XGL, or Nautilus. I understand that firefox with multiple tabs is going to use up RAM but I dont see why XGL or Nautilus does. I guess I didnt have XGL activated before though so that could be why I never noticed it.

---

### Post by SupWiz17 on 2007-10-21
I am also noticing that Pidgin uses a lot of memory for an instant messenger client. I do not remember gaim ever taking up this much memory is there any way to stop this?

---

### Post by dib_uk on 2007-10-22
I am having similar problem.  Left it(ubuntu 7.10GG) running over night, come back and the system is very very slow.  I mean, the mouse takes about 3 minuites to respond.  With lots of patience I was able to bring up top(took 10 minutes to load), system load was over 30.  memory usage:

MEM: 515836k Total 509620k used, 6216k free
SWAP: 1502036 total  745268k used, 756768k free

I think this is whats hogging all that memory:
PID    USER PR NI VIRT  RES    SHR  S %CPU  %MEM  TIME+        COMMAND
6182  root   16  0  733m 452m 1208 d   0.5       89.9    766:53:93  nautilus

I am not logged in as root, so I guess this is something it does in the background??

Its impossible to get it to shutdown but I am worried about just pulling the plug.

Help!!
Iam still a newb, so be kind

**UPDATE** 
did "shutdown -r now" to reboot it but on reboot there was lots of filesystem errors.  fsck fix them and now it has rebooted ok.

Just wondering now what that nautilus was doing, can I use gnome without nautilus and how can I reboot without fs being jackup next time?

---

### Post by Subban on 2007-10-22
in a terminal or run command (alt+f2) you could try
```

killall nautilus
```

It should kill and reload Nautilus.

---

### Post by SupWiz17 on 2007-10-22
As I have been letting my computer sit the memory usage has gone down quite a bit. I dont know why I have the same programs running but it is down to about 30% from 50%+, maybe gutsy just takes a day or two to get used to the system or something.

---

### Post by Subban on 2007-10-22
> **SupWiz17 said:**
> As I have been letting my computer sit the memory usage has gone down quite a bit. I dont know why I have the same programs running but it is down to about 30% from 50%+, maybe gutsy just takes a day or two to get used to the system or something.

Maybe it was doing some housekeeping in the background, or Tracker was updating or something,  I am only guessing though

---

### Post by Gosha-Za on 2007-10-22
Woah, I just realized there are alot of KDE-related running in the background

> 
kthreadd
ksoftirqd
khelper
kblockd
kacpid
kacpi_notify
kswapd0
khpsbpky
knodemgrd_0
ksuspend_usbd
khubd
kjournald
kpsmoused
kgameportd
konemand/0
...


Actually, they don't seem to take up a lot of RAM each .. but together I guess they consume pretty much.
I'm quite sure these weren't running when I had Feisty.

Any tips for what I should do?
Remove the kubuntu-desktop? ( Oh, actually I don't even have it installed. I have some other KDE-applications installed though. But I seldom use them since they run slow. )
( Amarok, The K-scanner program .. And probably some others I can't remember )

---

### Post by digitalbenji on 2007-10-22
Those are not KDE jobs, but rather kernel jobs.  I would leave them be.

---

### Post by Gosha-Za on 2007-10-23
> **digitalbenji said:**
> Those are not KDE jobs, but rather kernel jobs.  I would leave them be.

Oh!

So that's why there's a k before them.

Hmm, I guess I'll just forge my own system then.

---

### Post by SupWiz17 on 2007-10-25
Anyone having problems with XGL using up alot of memory. Earlier today XGL alone was using up half of my memory it was a bit outrageous.

---

### Post by chrisccoulson on 2007-10-25
> **dib_uk said:**
> I am having similar problem.  Left it(ubuntu 7.10GG) running over night, come back and the system is very very slow.  I mean, the mouse takes about 3 minuites to respond.  With lots of patience I was able to bring up top(took 10 minutes to load), system load was over 30.  memory usage:

MEM: 515836k Total 509620k used, 6216k free
SWAP: 1502036 total  745268k used, 756768k free

I think this is whats hogging all that memory:
PID    USER PR NI VIRT  RES    SHR  S %CPU  %MEM  TIME+        COMMAND
6182  root   16  0  733m 452m 1208 d   0.5       89.9    766:53:93  nautilus

I am not logged in as root, so I guess this is something it does in the background??

Its impossible to get it to shutdown but I am worried about just pulling the plug.

Help!!
Iam still a newb, so be kind

**UPDATE** 
did "shutdown -r now" to reboot it but on reboot there was lots of filesystem errors.  fsck fix them and now it has rebooted ok.

Just wondering now what that nautilus was doing, can I use gnome without nautilus and how can I reboot without fs being jackup next time?

If it keeps doing it, file a bug. Looks like Nautilus has a memory leak on your machine. You could also try doing:
```
mv ~/.nautilus ~/.nautilus.old
```

This will reset your Nautilus profile whilst keeping a backup of your old profile. I had a memory leak with Nautilus once, and this is what fixed it.

---

### Post by robrmd9 on 2007-10-25
> **SupWiz17 said:**
> I am also noticing that Pidgin uses a lot of memory for an instant messenger client. I do not remember gaim ever taking up this much memory is there any way to stop this?

Pidgin has a lot of memory issues, I don't remember gaim being this bad.  If you leave Pidgin running, it will eat up more RAM until you restart it.  It does this even if no plugins are enabled.

Version 2.2.2 (just released) should fix some of these leaks.

---

### Post by chrisccoulson on 2007-10-25
> **SupWiz17 said:**
> Anyone having problems with XGL using up alot of memory. Earlier today XGL alone was using up half of my memory it was a bit outrageous.

I've seen at least one other user on the forum commenting about memory usage, and in their case - Xgl was also using a lot of RAM. Not sure where the thread is though.

---

### Post by John Harrington on 2007-10-27
I've also been having the problem of very sluggish peformance occurring unpredictably and related to very high memory use.  It started with upgrade to Gutsy.  I have 512 MB RAM.  Graphic effects turned off.  Beagled appears to be the main culprit, taking more than 100 MB memory during sluggish episodes.  I selected "minimize memory usage" in tracker preferences, but still had the problem.  Today the system almost stopped working completely for several minutes, and then the memory usage suddenly dropped and speed immediately came back to normal.  I then checked and beagled wasn't working, so I assume the system shut it down.  Any suggestions other than to turn off beagle entirely?

---

### Post by chrisccoulson on 2007-10-27
> **John Harrington said:**
> I've also been having the problem of very sluggish peformance occurring unpredictably and related to very high memory use.  It started with upgrade to Gutsy.  I have 512 MB RAM.  Graphic effects turned off.  Beagled appears to be the main culprit, taking more than 100 MB memory during sluggish episodes.  I selected "minimize memory usage" in tracker preferences, but still had the problem.  Today the system almost stopped working completely for several minutes, and then the memory usage suddenly dropped and speed immediately came back to normal.  I then checked and beagled wasn't working, so I assume the system shut it down.  Any suggestions other than to turn off beagle entirely?

Are you suggesting that you're running both Tracker and Beagle?

---

### Post by John Harrington on 2007-10-27
Yes, that was stupid of me.  I thought Tracker was just the new name for Beagle, and therefore I was assuming that changing the Tracker settings would affect Beagle.  Comes from not reading up on Gutsy before installing it.  I guess I'll just uninstall Beagle.  Thanks.

---

### Post by th3gh05t on 2007-11-12
> **SupWiz17 said:**
> Yeah same here I am using 70% of my RAM just browsing the internet and using pidgin it is a bit ridicolous.


Ya, I totally agree. Look how much memory pidgin is taking up.

---

### Post by Jouke74 on 2007-11-12
- Pidgin obviously has a memory leak.

- Another big offender as mentioned is XGL (at my computer it was taking ususally about 200 MB). 
XGL won't show in the Gnome-system montitor unless you change the view to show all processes not just your processes. 

- Compiz also takes a lot (50-100 mb).

So if you are surfing the internet in firefox, using pidgin and have all desktop effects enabled you need about 512 Mb when you start. Memory leaks in Compiz and XGL also have been reported so this will probably increase with time you are using the programs. 

The computer slowness will start as soon as the computer starts to swap the full  memory to the swap partition.

---

### Post by th3gh05t on 2007-11-12
> - Pidgin obviously has a memory leak.

Does upgrading to 2.2.2 fix this problem? Has anyone tried?

---

### Post by Eestlane on 2007-11-26
So Pidgin is the weird thing causing such overhaul in my system. Thanks!
Also xgl is kind of a bit too much for me using ~50 MB of RAM. I only have 512 MB anyway.
I'll try some other IM from now on.

Thank you for this thread!

---

