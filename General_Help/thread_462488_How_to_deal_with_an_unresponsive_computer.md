---
title: "How to deal with an unresponsive computer?"
date: 2007-06-02
forum: General Help
---

### Post by Endolith on 2007-06-02
A few times in the past few weeks, my computer has gotten so clogged up I couldn't use it.  I think it's related to Firefox, but I can't reproduce it reliably.  But how do I deal with this situation?  It becomes very sluggish and the "system load average" meter maxes out.  The computer gets noticeably hot, but the CPU meter doesn't seem to correlate.  I don't get that.  Maybe it's the GPU that's locked up?  I try to open Gnome System Monitor to shut down processes, but, like Windows  Task Manager, it usually doesn't actually open until the problem has solved itself.  I try pressing Ctrl+Alt+F2 or whatever but it doesn't respond to anything either.  Eventually even the mouse stops responding.  How do you deal with situations like this besides holding down the power button?

---

### Post by raja on 2007-06-02
It is unusual for a computer to get completey unresponsive in linux like this. I have never had a situation where I had to hold the power button down. While the mouse is still active, just click on the close button of the unresponsive application. That should forcible exit even an unresponsive application. 
If you can open a terminal, you can kill a process from there. You can even do 'top', look at the process clogging the cpu and kill it. 
You should maybe set up the system monitor applet on the panel so that you can monitor cpu and RAM usage. If it begins to go up, look at the processes to see who the offender is. If it is firefox, you have to repeat this with extensions disabled one by one - often it is an extension which maybe causing a memory leak.

---

### Post by Endolith on 2007-06-02
> **raja said:**
> It is unusual for a computer to get completey unresponsive in linux like this.

No it isn't. :-)  Linux has always been worse than XP in this regard for me.  "Linux never crashes" is a myth (or only applicable to servers.)

>  I have never had a situation where I had to hold the power button down. While the mouse is still active, just click on the close button of the unresponsive application. That should forcible exit even an unresponsive application. 

I don't know which application is unresponsive, though.  I don't want to close something and lose my work if I don't have to.

> If you can open a terminal, you can kill a process from there. You can even do 'top', look at the process clogging the cpu and kill it. 

Can't open a terminal or system monitor.  KDE has an "applet" thing that notifies you if an application has gone haywire, and lets you force it closed.  Anything like that for Gnome?

> You should maybe set up the system monitor applet on the panel so that you can monitor cpu and RAM usage.

It shows memory, CPU, network, system load average, and temperature of hard drive and CPU.   The system load average is the one that goes up in this situation.  What does system load average even mean?

---

### Post by Endolith on 2007-06-08
It did it again.  I know what the cause was this time: Firefox trying to load a very very long page with lots of images.

Is there some way I can reduce the processor priority of Firefox or increase the priority of other things like the mouse and the system monitor?  I don't think it has this problem in Windows.  What's wrong with Linux that it does this?

---

### Post by diatribe on 2007-06-08
Ive heard a lot of people say firefox has memory leaks, if you type man uptime it will give a basic explanation of load averages.  you could always try another browser and see if that helps

---

### Post by tagra123 on 2007-06-08
when it does this 

you can kill firefox by typing in a terminal

killall mozilla-firefox

How much memory in your pc?

Have you tweaked firefox settings?

How many browsers or tabs are open?

I tweaked my firefox -- running version 2 on dapper with no problems. 

Here's one tweak page -- there are many more just google for them  

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by handydan918 on 2007-06-08
> **Endolith said:**
> It did it again.  I know what the cause was this time: Firefox trying to load a very very long page with lots of images.

Is there some way I can reduce the processor priority of Firefox or increase the priority of other things like the mouse and the system monitor?  I don't think it has this problem in Windows.  What's wrong with Linux that it does this?

The nice command will do this. See:
man nice

---

### Post by ramjet_1953 on 2007-06-08
If Firefox is causing the problem, how can an OS be to blame?

Shoddy applications, or improper setup can cause havoc on any OS, including Windows or OSX.

Why not try Opera, anyway, I have found it very good and the password wand is a really good function.

Regards,
Roger :cool:

---

### Post by tgalati4 on 2007-06-08
Control-Alt-Backspace will kill the X server and all the programs using it.  Your data in open applications won't be saved (unless autosaved within the past 10 minutes).  It may take a while for the X server to go down so be patient.  At the command prompt:  startx or it should restart automatically in Ubuntu.

There is a Force-Quit applet that I have put on my Gnome Application Bar.  I have used it for balky Firefox pages.  Sometimes to restart Firefox you need to:  sudo killall firefox-bin to kill off the remaining firefox threads before restarting.

Install and run ssh so you can log in remotely if your graphics card freezes.  This sometimes allows you to shutdown when your keyboard and mouse freezes.

---

### Post by Endolith on 2007-06-08
> **diatribe said:**
> Ive heard a lot of people say firefox has memory leaks
Not the problem.

> if you type man uptime it will give a basic explanation of load averages.

Ah.  Thanks.  So it's opening a lot of uninterruptable processes?

> **tagra123 said:**
> when it does this 

you can kill firefox by typing in a terminal

I said I can't open a terminal.

> How much memory in your pc?
1 GB

> Have you tweaked firefox settings?
Not really.

> How many browsers or tabs are open?
One browser with lots of tabs.

> **handydan918 said:**
> The nice command will do this. See:
man nice

Ok, thanks.  I was thinking something to change the process's priority in real time though.  Is that even theoretically possible?  I know windows task manager can do this.  I will read more about this.

> **ramjet_1953 said:**
> If Firefox is causing the problem, how can an OS be to blame?

Because a single application can lock up the entire desktop and make it impossible to do anything?  The "locking up everything" is not a Firefox problem.  It's a GNOME/X Windows/Linux  problem.

> Why not try Opera, anyway

Because I didn't ask for browser recommendations?

> **tgalati4 said:**
> Control-Alt-Backspace will kill the X server and all the programs using it.

Nope.  :-)

> There is a Force-Quit applet that I have put on my Gnome Application Bar.

That might be useful.  Is it more useful than the app's Close button?  GNOME eventually pops up a force quit dialog from that.

> Install and run ssh so you can log in remotely if your graphics card freezes.  This sometimes allows you to shutdown when your keyboard and mouse freezes.
Heh.  I didn't think of that.  I SSH to the other computer all the time.  Why not go the other way?

---

### Post by 444 on 2007-06-08
Well you said the system was getting hot, so it might be something else but...

The only time Linux gets unresponsive for me is during heavy swapping. Usually because of Firefox. On a page with a ton of images (seeing the parallels?). Basically when Firefox eats all the ram *and* almost all the swap, everything slows to a crawl. After about five minutes or so of swap grinding X gets restarted. I avoid it by keeping an eye on memory usage and restarting Firefox when it gets too high.

Another way to deal with it would be ctrl-alt-f6, which would take you to a command prompt that would load faster than any gnome stuff. Then you could 'killall firefox-bin'.

I've never had a problem with excessive cpu usage. I guess you could lower the priority of firefox but it's never been a problem, even at 100% cpu other programs work fine for me.

---

### Post by Endolith on 2007-06-09
> **444 said:**
> Well you said the system was getting hot, so it might be something else but...

Well, it's a laptop...   It's always getting hot.  As I said, the CPU usage meter doesn't go up during this.

> The only time Linux gets unresponsive for me is during heavy swapping. Usually because of Firefox. On a page with a ton of images (seeing the parallels?). Basically when Firefox eats all the ram *and* almost all the swap, everything slows to a crawl. After about five minutes or so of swap grinding X gets restarted. I avoid it by keeping an eye on memory usage and restarting Firefox when it gets too high.

That sounds *very* familiar.

---

### Post by ramjet_1953 on 2007-06-09
Quote:Why not try Opera, anyway 

Because I didn't ask for browser recommendations?


Endolith, a little less attitude would be appreciated on this forum.

Lots of people are here trying to help each other and advice is given freely, just becuase we want to help.

If you have a look at the "Code of Conduct" riles, you will see what I mean.

Regards,
Roger :cool:

---

### Post by Endolith on 2007-06-09
> **ramjet_1953 said:**
> If you have a look at the "Code of Conduct" riles, you will see what I mean.

Ok.

> 16. Replies to questions that ask for help running legitimate software ... that do not answer the question, but instead instruct the user that they should not be using that software ... serve only to frustrate and confuse the user and will be removed to make room for answers to the question the user asked

(abridged version) ;-)

---

### Post by korna on 2007-06-11
I have exactly the same problem with firefox. When firefox has been online for some time and i have seen some pages with lots of images, ubuntu will start swapping like mad .. endlessly. I can't forcequit firefox or start anything else and after a minute I can't even move the mouse anymore. The only way to get everything back is to hard reboot the computer!

In opera I don't have this problem. Still it is odd that the browser that comes installed with Ubuntu functions like this :P

I have 3 extension and I'm going see if disabling them helps.

---

### Post by Endolith on 2007-06-11
This happened again, but I believe Totem was the cause this time.  I had Firefox open for a while with no problems, started Totem and the computer started slowing down, closed Firefox and the problem persisted.  When I forced Totem closed, the problem went away.

KDE has a little applet that warns you if a program is taking over, and lets you force close it.  What I think I want is:

Something to watch if programs suddenly start using an inordinate number of uninterruptible processes and asks me if i want this to continue.

This "something" and the mouse used to activate it should have high enough priority that it is always available.

---

### Post by hikaricore on 2007-06-11
Didn't see this posted here yet, so I thought I'd throw it in:

[How to reboot if all else fails.]("http://ubuntuforums.org/showthread.php?t=315404&highlight=elephants")

If I overlooked it and am being redundant, sorry. :P

---

### Post by Endolith on 2007-06-12
> **hikaricore said:**
> Didn't see this posted here yet, so I thought I'd throw it in:

[How to reboot if all else fails.]("http://ubuntuforums.org/showthread.php?t=315404&highlight=elephants")

If I overlooked it and am being redundant, sorry. :P

Wow.  :-)

---

### Post by Yfrwlf on 2007-06-30
Endolith, I don't know a whole lot about how Linux and OSes in general function, but it sounds like it's a memory problem and not a process priority problem.

I've heard several users say that even if an app takes all the attention of the CPU, other things still work OK for them.  I've had problems with this myself, and maybe things need to have their priorities adjusted so that X has higher priority than any other running application, I don't know, but I don't feel that is the issue here.

The issue definitely sounds like a memory consumption issue.  Perhaps the issue is when a running application keeps asking for more and more memory, no matter how "nice" the kernel adjusts different running processes, that application is still there and asking for more memory, so how does the Linux kernel currently handle such a situation?  Maybe the answer is poorly.  I would guess that the problem is not at all with X, but with the kernel.  X is just of course one of many different running processes, and it sounds like a process memory issue.

If my assumptions that are very limited in knowledge actually are correct, perhaps something on the kernel level needs to be implemented to cut off an application's request for additional memory once the system reaches a critically low level?  Doing this I assume would cause the program to crash, but I'd think a crash would be much preferable to a system lock-up.

Last but not at all least, your attitude is preventing others from wanting to talk to you or help you.  It is very possible to politely disagree with someone without making rude responses like "Wow.".  Please be polite and informative in order to work to find the solution to problems, instead of being a problem yourself.

---

### Post by Endolith on 2007-06-30
> **Yfrwlf said:**
> I've heard several users say that even if an app takes all the attention of the CPU, other things still work OK for them.  I've had problems with this myself, and maybe things need to have their priorities adjusted so that X has higher priority than any other running application, I don't know, but I don't feel that is the issue here.

I think the priorities for certain things should be higher by default, like the mouse and the window manager.  There's no way the mouse should stop responding, or the "Close" button when acting as a "force quit".  If Gnome System Monitor is the recommended way to end an unruly process, for instance, there needs to be a quick, responsive way to open it.  (Why doesn't GNOME allow custom keyboard shortcuts natively?  This is the kind of thing that should have one, like Ctrl+Alt+Del in Windows.)

> The issue definitely sounds like a memory consumption issue.  Perhaps the issue is when a running application keeps asking for more and more memory, no matter how "nice" the kernel adjusts different running processes, that application is still there and asking for more memory, so how does the Linux kernel currently handle such a situation?  Maybe the answer is poorly.  I would guess that the problem is not at all with X, but with the kernel.  X is just of course one of many different running processes, and it sounds like a process memory issue.

I've added the swap space meter to the system monitor applet.  I didn't realize I hadn't selected it.  I'll see if there's a correlation next time the problem happens.  The last time it happened, the CPU usage was very low, but the system load went up and redlined, and the temperature of the hard drive went up.

I think I've seen the same effect caused by Evince and Sweep, so I don't think it's Firefox-specific.  It's hard to tell, though, because Firefox is almost *always* running...  :-)

Thanks to everyone for their help.

> Last but not at all least, your attitude is preventing others from wanting to talk to you or help you.  It is very possible to politely disagree with someone without making rude responses like "Wow.".  Please be polite and informative in order to work to find the solution to problems, instead of being a problem yourself.

I know this is the Internet and it's hard to read emotions from text and all, but... how in the world is it rude to say "Wow" with a smiley face?

---

### Post by TutoWRM on 2007-06-30
> **Endolith said:**
>  (Why doesn't GNOME allow custom keyboard shortcuts natively?  This is the kind of thing that should have one, like Ctrl+Alt+Del in Windows.)


Actually it can be done, just install automatix2 if you don't have it, and check under Miscellaneous, although read the following warning:that only works with gnome and metacity, it won't work under compiz or bery turned on.

regards. :)

---

### Post by Yfrwlf on 2007-06-30
> **Endolith said:**
> I think the priorities for certain things should be higher by default, like the mouse and the window manager.  There's no way the mouse should stop responding, or the "Close" button when acting as a "force quit".  If Gnome System Monitor is the recommended way to end an unruly process, for instance, there needs to be a quick, responsive way to open it.  (Why doesn't GNOME allow custom keyboard shortcuts natively?  This is the kind of thing that should have one, like Ctrl+Alt+Del in Windows.)

I started a thread on just this subject here [http://ubuntuforums.org/showthread.php?t=488762]("http://ubuntuforums.org/showthread.php?t=488762") because I couldn't find one specifically addressing the issue of making it easier for users to force close applications that have locked up or become unresponsive.  While some of the methods listed in this thread are good, there are many problems with the current system I feel, especially for new users.

> **Endolith said:**
> I've added the swap space meter to the system monitor applet.  I didn't realize I hadn't selected it.  I'll see if there's a correlation next time the problem happens.  The last time it happened, the CPU usage was very low, but the system load went up and redlined, and the temperature of the hard drive went up.

I think I've seen the same effect caused by Evince and Sweep, so I don't think it's Firefox-specific.  It's hard to tell, though, because Firefox is almost *always* running...  :-)

Thanks to everyone for their help.

All I know is that what is happening to you is bad, and needs to be prevented.  Sure, perhaps users should probably be the ones to decide to close certain programs of their choosing in order to free up memory if their computer starts slowing down, but if memory space becomes critical enough so that things become completely unresponsive or freeze up entirely, that sounds like a problem perhaps the kernel should be the one to deal with properly.  I don't know all the implications of all of this, I'd have to talk to a friend who's a Linux kernel dev to find out more information.

Let us know what you find out. :)

---

### Post by Yfrwlf on 2007-06-30
> **TutoWRM said:**
> Actually it can be done, just install automatix2 if you don't have it, and check under Miscellaneous, although read the following warning:that only works with gnome and metacity, it won't work under compiz or bery turned on.

regards. :)

Why Gnome doesn't have a place for custom shortcuts is a bit silly to me as well, but the reason is actually pretty simple.  I guess you can open the gconfig tool thing and do it in that, but you have to run that from the command line.  The entire point of all this is that the Gnome developers want to keep everything "simple".  KDE takes the opposite approach, and loads you with lots and lots of options to browse through.  In my opinion, the best desktop configuration would be a happy medium between these two ideologies.  Keep the default settings sane, and stow all the more "advanced", or simply less-used options away into "advanced" sections, but don't get rid of the power tools completely.  I believe both can co-exist on the same desktop.

I think the much bigger issue though is not trying to create custom hot keys, it's why hasn't something already been made default in X or the desktop environments?  Closing dysfunctional applications IS something that the all users are going to have to do, so I feel a system needs to be implemented in order to address this issue.

Again, that topic though is here [http://ubuntuforums.org/showthread.php?t=488762](http://ubuntuforums.org/showthread.php?t=488762), since I don't want to hijack this thread's current topic.

---

### Post by Endolith on 2007-06-30
> **TutoWRM said:**
> Actually it can be done, just install automatix2 if you don't have it

I don't have it.  I tried it once and it hosed my system.  Never again.

> **Yfrwlf said:**
> Why Gnome doesn't have a place for custom shortcuts is a bit silly to me as well, but the reason is actually pretty simple.  I guess you can open the gconfig tool thing and do it in that, but you have to run that from the command line.  The entire point of all this is that the Gnome developers want to keep everything "simple".  KDE takes the opposite approach, and loads you with lots and lots of options to browse through.

Yep.  I preferred KDE because GNOME was too limited, but I've given GNOME a shot and decided I like it better.  A lot of times you can figure out how to do something with a third-party program or hidden option, even if the developers don't want you to. The fundamental concept behind GNOME is good, but some of the developers don't fully understand it, and limit the functionality in bad ways.

> In my opinion, the best desktop configuration would be a happy medium between these two ideologies.  Keep the default settings sane, and stow all the more "advanced", or simply less-used options away into "advanced" sections, but don't get rid of the power tools completely.  I believe both can co-exist on the same desktop.

Agreed.  "Advanced" sections or command line tools are often crutches for things that haven't been developed or implemented properly yet, but that doesn't mean they should just be left out altogether.

> I think the much bigger issue though is not trying to create custom hot keys, it's why hasn't something already been made default in X or the desktop environments?  Closing dysfunctional applications IS something that the all users are going to have to do, so I feel a system needs to be implemented in order to address this issue.

Agreed.

---

### Post by Yfrwlf on 2007-07-01
This was pretty interesting, the link in the other thread to this page [here]("http://developer.osdl.org/dev/robustmutexes/REPOS/fusyn.hg/?cmd=file;filenode=32d0a5eb8f92fa9221a6311440ffafbc042e510b;file=Documentation/sysrq.txt") tells you that you can use a LAlt-Sysrq-F in order to "call oom_kill to kill a memory hog process".  Perhaps that's one command you should keep close by Endolith, for now, until/if this gets resolved somehow.

---

### Post by Endolith on 2007-08-03
As I said, I've added the swap space meter to the system monitor applet.  And it shows nothing!  Just a black box at all times.

Tonight the problem happened again.  It's a pretty regular occurrence.  This time I believe it was Evince that caused it.  I opened a large PDF and the system started to behave strangely.  I watched the system load meter jump up in steps, and tried to close Evince, but by the time I got the mouse moving towards the close button the mouse had stopped responding, except in bursts every 15 seconds or so, then not at all.  This is how it happens every time.  

This time I noticed that the green part of the memory meter was taking up the entire box, and the CPU was hardly working at all.  I was also running update manager at the same time, and Firefox (of course).  And some other things.

I tried Ctrl+Alt+F1 but it took several minutes just to turn the screen black, then another minute to display the login, then another minute to ask for my password,...  I'm trying to log in over SSH from my other computer and it's unresponsive.  I'd force a computer restart, but that just destroys GNOME and you have to go in and delete session files and so on.  BSODs were so much easier to deal with...

---

### Post by Endolith on 2007-08-03
Ahhh.  It started working again.  The Evince window that I opened is no longer there.  Maybe because I tried to click the close button, maybe because it choked itself to death, I don't know.  The system load bar was still maxed out, so I terminated the other Evince running, and the system load dropped slowly back down to nothing.  My other computer says 5% swap space in use, by the way, and this one always says 0%.

---

### Post by Endolith on 2007-08-03
I just went back into the Ctrl+Alt+F1 terminal (what's the correct name for this?) and saw an error message saying that soffice had quit after taking up too much memory.   So I guess OpenOffice was the culprit this time?

---

### Post by xzero1 on 2007-08-03
> It did it again. I know what the cause was this time: Firefox trying to load a very very long page with lots of images.

Decoding images is a fairly cpu intensive process. Even a low priority process can have a critical section(s) that can "lock" the cpu and prevent interrupts from being serviced (your mouse is locked out for a period of time).More likely it contains calls to the os that would do the same. The design of the program makes a difference and as suggested Opera may do a better job though I would check the firefox forums for a possible tweak that may help.

---

### Post by Endolith on 2007-08-03
> **xzero1 said:**
> Even a low priority process can have a critical section(s) that can "lock" the cpu and prevent interrupts from being serviced

That seems to me like something more fundamental than Firefox itself (or Evince or OpenOffice) is broken...

---

### Post by perspectoff on 2007-08-03
Your problem happened to me all the time with graphics intensive programs.

What I finally figured out was that the Ubuntu Installer did not autodetect my graphics card properly.

I use an intel 865G chipset with Extreme Graphics 2, which requires the i810 video driver. But Ubuntu installed the VESA driver.

Until I corrected my /etc/X11/xorg.conf file so that the correct video driver was named, everything hung with graphics intensive loads.

I figured it out only after months, when my really graphics intensive programs (Stellarium and Google Earth) completely froze.

I made these switches in /etc/X11/xorg.conf:

Changed:

Section "Device"
Identifier "Generic Video Card"
Driver "vesa"
BusID "PCI:0:2:0"
EndSection

to:

Section "Device"
Identifier "Intel Corporation 82945G/GZ Integrated Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

and changed the section:

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
...

to

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82945G/GZ Integrated Graphics
...

Now both Stellarium and Google Earth and all my other graphics intensive programs work fast and without problems.

The problem seems to be that the auto-detection of my graphics card by the Ubuntu Feisty installation did not accurately identify the graphics card driver needed. This was not a problem in Dapper; I don't know what changed.

Try looking to see if your graphics card is properly recognized. I know this is a big problem with Nvidia cards, as well.

---

### Post by HermanAB on 2007-08-03
Hmm, my favourite (though usually financially impractical) solution to an unresponsive computer is the swift application of a big hammer.  That really is a very efficient and satisfying mechanism to make a computing problem go away permanently.

---

### Post by xzero1 on 2007-08-04
> hat seems to me like something more fundamental than Firefox itself (or Evince or OpenOffice) is broken...

I agree with you, if the os can be "taken over" in the way you describe it, I consider that an os bug.

---

### Post by Endolith on 2007-08-05
I'm wondering if it's from running out of memory.  I notice the memory bar is filled with dark green the last few times it happens.  And the swap space meter is perpetually on 0%, which indicates to me that something is wrong with that.  I have 1 GB of memory.

Edit:

Aha.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          1011        928         82          0          4        144
-/+ buffers/cache:        779        231
Swap:            0          0          0

```

---

### Post by Endolith on 2007-08-06
Ok.  Swap space is fixed.  Let's see if it continues happening.

---

### Post by Endolith on 2007-08-22
I have not seen this problem since I enabled swap space.

---

### Post by misfitpierce on 2007-08-22
Good to hear your running fine now. It's always a good idea to have atleast 750MB swap space. Makes for good clearing.

---

### Post by mateuszbaranski on 2007-10-09
> **ramjet_1953 said:**
> 
Why not try Opera, anyway, I have found it very good and the password wand is a really good function.


Opera was good when it was in 8th version - I tried to use 9th 
version several times on Win and linux without success - it takes whole CPU time from time to time - anyone had similar problems?

About the overloaded system - I had also similar problems as Endotlith. The system was so slow that I even couldn't open terminal to kill the damn process.  There were different processes that caused it - Firefox, KPDF, Kadu communicator, vmplayer.

After investigating swap space as sugested by the end of this topic I found that I have wrong UUID for swap partition in /etc/fsta, so the system couldn't successfully mount the swap ppartition.
I have switched from 40GB to 120GB hard drive using CloneZilla (for hard disk cloning) - so UUID were the same on the new HD but - swap partition I have created by myself so it had a new UUID.  That is the efect of Ubuntu Installer which  uses UUID instead of traditionaly /dev/hdx descriptions (ofcourse UUID are preffered but in my case it caused problems).

Thx to Endolith who solved his own problem :)

---

### Post by Endolith on 2007-11-29
This has happened a few times since, by the way.  It simply locks up any time I use up all the memory and swap space.  Yes, 1 GB of memory and 1/2 GB of swap space all used up.

It really shouldn't do that.  I would file a bug, but I wouldn't know where to file it.  This seems like a fundamental problem.

I got another GB of memory and haven't had any problems since.  But still.  It shouldn't be possible to lock up the computer like that.

---

### Post by HermanAB on 2007-11-29
The swap should be about 2x the RAM size.

---

### Post by Endolith on 2007-11-29
> **HermanAB said:**
> The swap should be about 2x the RAM size.

Someone told me half a long time ago.  :-)

---

### Post by 444 on 2007-11-29
> **Endolith said:**
> This has happened a few times since, by the way.  It simply locks up any time I use up all the memory and swap space.  Yes, 1 GB of memory and 1/2 GB of swap space all used up.

It really shouldn't do that.  I would file a bug, but I wouldn't know where to file it.  This seems like a fundamental problem.

I got another GB of memory and haven't had any problems since.  But still.  It shouldn't be possible to lock up the computer like that.

Ah, automatically adding more swap (as a swapfile) when running low. Sounds like a nice feature (half-done already if you search for it). Of course that doesn't really eliminate the problem, when the XX-bit address space (often only around 4gb), or your whole drive (whichever first) gets used, you're back at square one.

I assuming something is bloating up unintentionally. Intentionally would be opening a huge file (image or something), which you'd know beforehand whether to add more swap yourself or not.

So the target is a bloaty program. Like [Firefox](http://kb.mozillazine.org/Memory_Leak), most likely.

Not to mention that you not having enough swap is part of the problem as well. This becomes a lot less of an issue if you use the default swap settings, on my machine it's 2-3gb depending on the drive size. Yes, I experienced your problem with a dinky 128mb swap partition I used to have a while ago. I've never seen the problem (ever) since.

But really, swap is not a replacement for memory. You should not be using swap, it's just there for unusual circumstances (and hibernating). The moment I hear my swap going active, even by just a few megs, I realize it's time to restart Firefox. And this is way before the system freezes up.

---

### Post by Yfrwlf on 2007-11-29
> **444 said:**
> So the target is a bloaty program. Like [Firefox](http://kb.mozillazine.org/Memory_Leak), most likely.

Not to mention that you not having enough swap is part of the problem as well.

The problem may be a bloated program, but for an OS to lock up instead of doing whatever necessary to prevent this isn't good, like it could kill an extremely bloated program that is the main cause of the memory running out of space, and it should be terminated with an error that it has run out of memory so the user knows why.

Lock-ups should never be a "feature" of any OS.

Ever.

At the very very least, after coming under whatever kinds of heavy attack or encountering whatever kinds of bugs, a kernel should try to restart itself instead of locking up.  I'm not saying I know how to make that happen or how possible certain things are, but the fact remains.

"Some men see things as they are and say why, I dream things that never were and say why not." - Robert Kennedy

---

### Post by mateuszbaranski on 2007-12-01
> **Endolith said:**
> Ok.  Swap space is fixed.  Let's see if it continues happening.

Just to make an update. I observed this this again (system couldn't mount swap partition) - it happened probably after hibernating a system or after upgrade from kubuntu 7.04 do 7.10. After this my laptop began to be really sluggish. Again I had no swap space. And the partition with swap was damaged (?!) - I had to fotmat it again in order to be operative.

Is it a bug?
 

Mateusz

---

### Post by asabjorn on 2007-12-13
Another feature in Gutsy that may cause excessive hard drive usage is tracker. This was part of my problem and got better by uninstalling Tracker.

Andreas

---

### Post by Endolith on 2007-12-13
> **asabjorn said:**
> Another feature in Gutsy that may cause excessive hard drive usage is tracker. This was part of my problem and got better by uninstalling Tracker.

But Tracker is so useful!

---

### Post by Endolith on 2007-12-13
> **Yfrwlf said:**
> The problem may be a bloated program, but for an OS to lock up instead of doing whatever necessary to prevent this isn't good, like it could kill an extremely bloated program that is the main cause of the memory running out of space, and it should be terminated with an error that it has run out of memory so the user knows why.

Lock-ups should never be a "feature" of any OS.

Ever.

At the very very least, after coming under whatever kinds of heavy attack or encountering whatever kinds of bugs, a kernel should try to restart itself instead of locking up.  I'm not saying I know how to make that happen or how possible certain things are, but the fact remains.

Exactly.  Should we report this as a general Ubuntu bug?

---

### Post by HermanAB on 2007-12-13
The system should not lock up.  Firefox may take a long time to load, but that should not lock the whole system up.  If it does, then something else is wrong.

I have only experienced severe slow-downs when the system has very little memory and/or /swap is too small or disabled.

---

### Post by Endolith on 2007-12-13
> **HermanAB said:**
> The system should not lock up.  Firefox may take a long time to load, but that should not lock the whole system up.  If it does, then something else is wrong.

I have only experienced severe slow-downs when the system has very little memory and/or /swap is too small or disabled.

Yes.  It becomes so slow that it stops responding to anything and can only be used after a Alt+SysRq+F.

---

### Post by Yfrwlf on 2007-12-14
> **Endolith said:**
> Exactly.  Should we report this as a general Ubuntu bug?

I think you should always file any and all bugs, and they can be directed to the appropriate areas from there.  At the very least, you'll hopefully be able to talk to someone who can help you track down the issue to correctly define what the problem is so that it can be addressed somehow.  I really don't know where this problem is, I mean, if a program has a memory leak, *can* the kernel do anything to stop it?  Because how is the kernel supposed to know that you didn't want that memory allocated by that program?  (We're talking about memory leaks before it gets critical for the moment.)  All the kernel knows is that the program wants more, so it thinks it's normal, when the program shouldn't have done it and it is the program's fault to a degree.  So now lets say you started bumping up against your max RAM and maybe even max swap space.  What I want to know is how would the kernel begin to decide which program to close?  Should it stop whichever process is taking up the most memory?  Maybe the one that is the most active?  It has to close something, so I wonder which it should choose, because I think this difficult decision would have to be made in this case, since there is no way for the kernel to really know which program is having the problem is there?  Except, perhaps it can monitor the mem size of a process, and if it sees that a process has been slowly taking up more and more and more space and seems to be leaking, perhaps it should target the process that seemed to follow a trend like that, and close it as the suspected problem program/process (sorry, kept using those two interchangeably).

Regardless I definitely still agree that it should do *something* instead of locking up or becoming nearly completely unresponsive, or should at that time put user input on maximum priority since the system is clearly (or it should be clear) in trouble.  Perhaps as it nears the edge of the memory filling up, it still thinks "well maybe it's only a little more, then the process will be finished....OK...perhaps a little more.....maybe just needs a liiiitle bit more time, I'll let it keep trying to run...".  For a kernel to give up on a process is kind of serious, you know?  So perhaps the solution is something that is a serious solution and lots of concern needs to be involved with making it.  It may be a great problem for any kernel developers out there.  But yeah, a solution would be nice, no matter the difficulties.  I'm not trying to belittle your problem but at least for me this is something that really doesn't happen anymore though I have experienced it, but of course throwing more performance and RAM at a bug to fix it isn't fixing the bug at all.

Actually, one way to duplicate what may be the same thing or something similar is to install "Stress" from the Ubuntu repository.  There are lots of other benchmark programs, but with stress you do```
stress -c numberofhogs
```for CPU testing,```
stress -i numberofhogs
```for I/O testing, and```
stress -m numberofhogs
```for memory hog testing, or of course you can combine them all into something like```
stress -c 2 -i 2 -m 2
```to hog everything with 2 "hogs" each.  Pull out your system monitor before doing this.  You can watch as things get very sluggish and your resources fill up.  The more hogs, the more intensive the test will be on your system.  Putting a terminal or the system monitor or something on max priority may be a good idea too in order to allow the process to be ended because like I said, UI response will become somewhat slow.

---

### Post by Endolith on 2007-12-14
> **Yfrwlf said:**
> I think you should always file any and all bugs, and they can be directed to the appropriate areas from there.

Of course, but this is a bug with the entire operating system.  I'm not sure where to file it or who could fix it.  I suppose there are already solutions that can be installed, and reporting the bug would have the developers add these solutions to be installed by default?

> I really don't know where this problem is, I mean, if a program has a memory leak, *can* the kernel do anything to stop it?  Because how is the kernel supposed to know that you didn't want that memory allocated by that program?  (We're talking about memory leaks before it gets critical for the moment.)  All the kernel knows is that the program wants more, so it thinks it's normal, when the program shouldn't have done it and it is the program's fault to a degree.  So now lets say you started bumping up against your max RAM and maybe even max swap space.  What I want to know is how would the kernel begin to decide which program to close?

Why does it have to close a program?  Can't it just refuse to allocate more memory to the program?  And then the program will handle what happens from there?  (Crash with out of memory error, or, if the program is well-designed, throw away some cached data, shut down cleanly and save recovery files to disk, or, if not time-sensitive, just pause execution and keep asking for more memory?)  Why can't it just pop up an "out of memory, please close something" notification and start using free disk space (/tmp/?) as surrogate memory until you close something manually?

> Should it stop whichever process is taking up the most memory?  Maybe the one that is the most active?

[oom_kill]("http://fxr.watson.org/fxr/source/mm/oom_kill.c?v=linux-2.4.22") already keeps track of this, and makes that decision for you, but I don't think it should just be configured to [kill processes randomly]("https://lists.sdsc.edu/pipermail/npaci-rocks-discussion/2006-June/019111.html").  The OS should present a user-friendly way of killing something intentionally, if it comes to that.  The interface should remain responsive no matter what.  If System Monitor is the GNOME way to manipulate processes, it should have high enough priority that it still pops up in some form or other regardless of the state of the system.

> Regardless I definitely still agree that it should do *something* instead of locking up or becoming nearly completely unresponsive, or should at that time put user input on maximum priority since the system is clearly (or it should be clear) in trouble.

Yes.

> It may be a great problem for any kernel developers out there.  But yeah, a solution would be nice, no matter the difficulties.  I'm not trying to belittle your problem but at least for me this is something that really doesn't happen anymore though I have experienced it, but of course throwing more performance and RAM at a bug to fix it isn't fixing the bug at all.

I bought another GB of RAM, actually, because of this problem.  It still locks up occasionally.  I just use a lot of memory, I guess.  ;-)

> Actually, one way to duplicate what may be the same thing or something similar is to install "Stress" from the Ubuntu repository.

Good to know.

---

### Post by Endolith on 2007-12-21
> **444 said:**
> Ah, automatically adding more swap (as a swapfile) when running low. Sounds like a nice feature (half-done already if you search for it). Of course that doesn't really eliminate the problem, when the XX-bit address space (often only around 4gb), or your whole drive (whichever first) gets used, you're back at square one.

But it would hopefully warn you long before this happened and let you close programs intentionally instead of letting the system shoot them at random.

> I assuming something is bloating up unintentionally. Intentionally would be opening a huge file (image or something), which you'd know beforehand whether to add more swap yourself or not.

So the target is a bloaty program. Like [Firefox](http://kb.mozillazine.org/Memory_Leak), most likely.

Yes, but it shouldn't lock up the entire system anyway.

> Not to mention that you not having enough swap is part of the problem as well. This becomes a lot less of an issue if you use the default swap settings, on my machine it's 2-3gb depending on the drive size. Yes, I experienced your problem with a dinky 128mb swap partition I used to have a while ago. I've never seen the problem (ever) since.

Our computing practices must differ.  I've got 2 GB of RAM now, and 512 MB of swap, and it just locked up again.

> But really, swap is not a replacement for memory. You should not be using swap, it's just there for unusual circumstances (and hibernating). The moment I hear my swap going active, even by just a few megs, I realize it's time to restart Firefox. And this is way before the system freezes up.

Instead of "hearing" the swap space being used, you should at least be notified by a balloon tooltip or something.  But there are better solutions.

---

### Post by Yfrwlf on 2007-12-21
I had X start going really really slow the other day.  No clue what it was doing, just went really slow.  When I logged in remotely since local actions were taking 100 years, nothing was maxing out the processes.  X was just screwed up or something.  I don't know how much swap space was being used, but I closed Firefox, and it was gone, but it didn't help, X was still slow, I had to restart X to fix the problem.  Not sure how to log these types of slowdowns really...

You may have said this already Endolith but are they complete lockups for you, because I thought you said they were slow downs, and have you tried SSHing in when this happens?

---

### Post by Endolith on 2007-12-21
> **Yfrwlf said:**
> You may have said this already Endolith but are they complete lockups for you, because I thought you said they were slow downs, and have you tried SSHing in when this happens?

They are slow downs, but they become so slow that not even the mouse or Ctrl+Alt+F1 responds, and it persists like this for hours.  So it's effectively a lockup.

If I SSH from another computer, there's a chance it will let me log in after a few minutes of waiting, but usually that is unresponsive, too.

---

### Post by DrMilo on 2007-12-21
I've got the same thing. I'm using i386 dapper on a new system with my old video card and an AMD dual core motherboard. The lockups are complete, no keyboard or mouse at all. seems to do with playing video but whenever I try to reproduce the condition it doesn't lock up. I can go several days without locking up and then it will happen again. I've got some new drivers for my motherboard and tomorrow hopefully I'll get motivated enough to do them. But as previously said there's something unprotected in Ubuntu or this wouldn't happen. I had system hangs before in Ubuntu but untill I used this motherboard I never had it where no keys would respond.

---

### Post by Yfrwlf on 2007-12-22
> **Endolith said:**
> They are slow downs, but they become so slow that not even the mouse or Ctrl+Alt+F1 responds, and it persists like this for hours.  So it's effectively a lockup.

If I SSH from another computer, there's a chance it will let me log in after a few minutes of waiting, but usually that is unresponsive, too.

What is getting the most CPU attention in your case, is it Firefox or X or anything in particular, when you are able to SSH in?  I notice a time on my computer when both Xorg and Firefox were taking up a substantial amount of CPU power.  After all, displaying Flash or Java apps could bog both down, perhaps it's a bug in one of them.  In one case I even had two Xorg processes running that were both taking up a bunch of CPU, and when I got rid of one of them it didn't effect my X session.  Very strange.

Does anyone know of a proper way of supplying this information to bug collectors?  Not sure what you would provide with these problems.  Xorg logs?  Guess I'll check out the Xorg pages and try to find out..

> **DrMilo said:**
> I've got the same thing. I'm using i386 dapper on a new system with my old video card and an AMD dual core motherboard. The lockups are complete, no keyboard or mouse at all. seems to do with playing video but whenever I try to reproduce the condition it doesn't lock up. I can go several days without locking up and then it will happen again. I've got some new drivers for my motherboard and tomorrow hopefully I'll get motivated enough to do them. But as previously said there's something unprotected in Ubuntu or this wouldn't happen. I had system hangs before in Ubuntu but untill I used this motherboard I never had it where no keys would respond.

Have you tried SSHing in, and is it sudden or do things start to slow down in general before the lockup?

---

### Post by DrMilo on 2007-12-22
> **Yfrwlf said:**
> What is getting the most CPU attention in your case, is it Firefox or X or anything in particular, when you are able to SSH in?  I notice a time on my computer when both Xorg and Firefox were taking up a substantial amount of CPU power.  After all, displaying Flash or Java apps could bog both down, perhaps it's a bug in one of them.  In one case I even had two Xorg processes running that were both taking up a bunch of CPU, and when I got rid of one of them it didn't effect my X session.  Very strange.

Does anyone know of a proper way of supplying this information to bug collectors?  Not sure what you would provide with these problems.  Xorg logs?  Guess I'll check out the Xorg pages and try to find out..



Have you tried SSHing in, and is it sudden or do things start to slow down in general before the lockup?

I have never SSHed and don't know how. There's no perceptible slowdown. Today it happened that I was playing a video and went over to my browser and when I moved the mouse to where it became a hand over a graphic it locked instantly. This while I had the video on pause in VLC.

I've tried something. I had the files from a previous install of Ubuntu on another partition and have now deleted them and rebooted. Perhaps something was loading improperly? I have tried to recreate the fault since and so far can't. Unfortunately this lockup doesn't seem to be recreatable anyway!

Also I plan to do these motherboard upgrades today. 

Only thing I've got so far is a video on pause in VLC with Firefox open seems to do it... but then it doesn't!

---

### Post by DrMilo on 2007-12-23
This might be something or nothing but I was running my mouse through a dongle to a PS2 port. I've taken out the dongle and am running the mouse through USB. I haven't been able to cause the lockup since, which doesn't mean a thing of course. But the mouse is much more responsive and fast since I did that. There are some old bugs in Ubuntu to do with running a mouse on a PS2 port and sometimes these bugs are never entirely resolved. I'll report back...

---

### Post by Yfrwlf on 2007-12-23
> **DrMilo said:**
> This might be something or nothing but I was running my mouse through a dongle to a PS2 port. I've taken out the dongle and am running the mouse through USB. I haven't been able to cause the lockup since, which doesn't mean a thing of course. But the mouse is much more responsive and fast since I did that. There are some old bugs in Ubuntu to do with running a mouse on a PS2 port and sometimes these bugs are never entirely resolved. I'll report back...

Are you sure the lockup was a full lockup?  Could you use keyboard inputs, or was it just the mouse that stopped responding?  One way to test is to hit Ctrl-Alt-F1 twice to get to a terminal, or just hit one of the Gnome hotkeys for something.  I'm assuming it was a complete lock-up of course.  Perhaps it is an input issue with X with your mouse.

Any way, if you ever have it happen and X is completely locked and not allowing you out of it, try SSHing in by installing the "ssh" package on your computer which will install both the server and client packages.  You can then SSH in from other computers by typing "ssh yourusernameonremotecomputer@remotecomputer'sIPaddress".  Or, you can use a GUI program like Putty, which is available for most all platforms I believe.  Test it so that if you ever have a problem again, you can try SSH.  Once you're in, you can do things like restarting X if X has crashed or the computer is slow (due to X, which it usually is the culprit, or things running within your X session like Firefox, which will be restarted by restarting X).  Just so you know, to restart X from the command line do "sudo /etc/init.d/gdm restart".

---

### Post by Yfrwlf on 2007-12-23
Endolith:

During a slow down, try to SSH in and get your X logs, maybe a text save of the output of top if you can put that in a file?  I'm not sure what other things you could gather exactly, and if the problem was happening and you could SSH into it that would be the best time to ask about it.  I'd gather anything you can and talk to the Firefox, Xorg, and kernel communities in that order and see if you can find out what the problem is, make suggestions to try to find out if there's some way the kernel could be improved, etc etc.  Try to track someone down who can help, and provide any information they ask for while the problem is happening if it keeps up.  Let us know if you're successful in finding *something* out!  I'd do IRC as it's often the fastest.

---

### Post by Yfrwlf on 2008-01-26
Wanted to note an experience I had, while loading up an OGG file in Audacious the computer became less responsive as my memory neared being completely full, since it was focusing on Audicious mostly, but once it was too much for it and it realized or hit the point at which there was no more space left for it, Audicious was terminated.  I know because I watched my system monitor.  RAM and swap space filled up until they peaked, then Audicious was automatically closed and they both dropped back to normal.  This is a good thing, and what an OS should do.  Now, maybe Audacious just crashed, and it wasn't the OS that ended it, but regardless it was good since what else could be done with a program that wants more memory than exists?  I found out there is a processing que though, so if programs need stuff done and the CPU is too busy, they will be placed in a que which is visiable I think through the command line program Top.  But wanting more memory than exists?  Can't be done.

However, there could be some improvements to the desktop.  While the mouse never froze completely but did bog down a bit a few times, other programs that were "in focus" on the desktop greatly slowed as memory storage approached being full.  In other words, I don't think Linux has been made to play nice with the desktop yet.  It still functions like a server, and divides tasks equally.  The new scheduler perhaps may improve on that, but I don't know if there is any "focusing" based on window desktop focus like other OSes may have.  I believe that if Linux is to succeed on the desktop, implementing a priority-switching mechanism based on window focus may be a good, and it would be really easy, and you could make it configurable and disableable.

---

### Post by Endolith on 2008-01-26
> **Yfrwlf said:**
> Audicious was terminated.  I know because I watched my system monitor.  RAM and swap space filled up until they peaked, then Audicious was automatically closed and they both dropped back to normal.  This is a good thing, and what an OS should do.

Maybe oom_kill?  That's not really the best way, but it's better than locking up.

---

### Post by runemaste644 on 2008-01-26
maybe try ctrl+alt+backspace?
that kills the xserver (in Linspire, it is called a 'quick reboot') and all apps connected to it, therefore freeing up some space. Save your stuff before you do it, though.

---

### Post by philipm on 2008-03-18
> **hikaricore said:**
> Didn't see this posted here yet, so I thought I'd throw it in:

[How to reboot if all else fails.]("http://ubuntuforums.org/showthread.php?t=315404&highlight=elephants")

If I overlooked it and am being redundant, sorry. :P

My machine became totally unresponsive to the point of no mouse movement and not being able to ssh in. Your hint (other than yanking the power cord) appeared to be the only way out.

In my case, I had been trying to view a YouTube on FireFox 2.0.0.11, and it complained that I lacked a plugin depsite the fact that the required Flash plugin (flashplugin-nonfree) was actually there, so I told it to install the offered free alternative which it did (gnash), then my next attempt at viewing a YouTube (after restarting FireFox) totally locked up the system.

After updating the system (FireFox to 2.0.0.12) and removing gnash and asking it to reinstall flashplugin-nonfree YouTube is finally working.

That some combo like this could totally lock up the system is not very good.

I'm not sure if I want to repeat the entire experiment but this may be enough of a paper trail for someone keen enough to file a bug report to try to pin it down more exactly (but otherwise, this may help someone with the same symptoms).

---

### Post by Yfrwlf on 2008-03-21
> **philipm said:**
> My machine became totally unresponsive to the point of no mouse movement and not being able to ssh in. Your hint (other than yanking the power cord) appeared to be the only way out.

In my case, I had been trying to view a YouTube on FireFox 2.0.0.11, and it complained that I lacked a plugin depsite the fact that the required Flash plugin (flashplugin-nonfree) was actually there, so I told it to install the offered free alternative which it did (gnash), then my next attempt at viewing a YouTube (after restarting FireFox) totally locked up the system.

After updating the system (FireFox to 2.0.0.12) and removing gnash and asking it to reinstall flashplugin-nonfree YouTube is finally working.

That some combo like this could totally lock up the system is not very good.

I'm not sure if I want to repeat the entire experiment but this may be enough of a paper trail for someone keen enough to file a bug report to try to pin it down more exactly (but otherwise, this may help someone with the same symptoms).

As long as it's not some kind of kernel lock, you should *always* be able to switch to another screen, log in, and terminate the process that has either locked up or is eating 99.9% of the CPU because it has become borked.  SSHing in may be sluggish, but that should also remain possible.  I would say that if you can't SSH in, either your timeout is set too low on your SSH, or the kernel has locked.

Perhaps there should be an X-server monitor that makes sure the server process doesn't seem hosed and if it is, to restart it for the user.  That way those who don't know the command line will have a chance at getting it restarted.  Not sure how possible this is, it'd have to be intelligent enough to determine the difference between a bogged-down X-server and a borked X-server.  That might be a quick patch until X becomes more failsafe or can encapsulate errors better or whatnot.

---

