---
title: "slow computer - ubuntu 21.04"
date: 2021-06-26
forum: General Help
---

### Post by jgw on 2021-06-26
I have two computers on a kvm.   Both are running with 21.04   One is slow and keeps on crashing (kinda - wait long enough and it seems to uncrash).   I suspect that I have something, in the slow machine that is hogging stuff.  Oh, I am also using firefox 9.0.1  When I say crash I mean to say that my mouse stops working and firefox is no longer accessable (except for current window).  When I am in the Terminal and am doing a sudo command (like; "sudo apt update" it takes the slow machine up to 20 seconds to give me the name quiery, on the other machine its instantaneous.  OH, when firefox freezes it eventually puts a box on the screen telling me it screwed up and wants to send the info to them and I have a choice to have it force a quit or wait.    Neither works.  it even gets better!  If I goto the monitor and try to end it doesn't.  if I try and kill - it doesn't.  However, in the fullness of time, it will eventually either quit or give me the box telling me it has a problem.  When I choose to Anyway, I also suspect there is some way I can tell what the bad thing causing this is.  I have written several messages on the firefox forum - no replies.

Hopefully there is some solution to my problem?

Thank you...................

---

### Post by ajgreeny on 2021-06-26
>  Oh, I am also using firefox 9.0.1
Really Firefox 9.0.1; did you mean 90.1, ie, running the daily or a development version?

The normal repos version of FF is 89.0.1 so if you are using 9, or 90, where did it come from?

---

### Post by jgw on 2021-06-26
You are right!  It IS 89.0.1!  (dumb mistake - sorry)  In the time I took me to get over here and send this my firefox told me it was sorry - it was frozen when I left to come here and send this!   That means, that it was frozen for about 3 to 4 minutes all told.  (sometimes its forever)

---

### Post by tea for one on 2021-06-26
> **jgw said:**
> I have two computers on a kvm. 

Are these Virtual Machines (KVM/QEMU)?

Or a hardware switch with [COLOR="#0000FF"]K[/COLOR]eyboard [COLOR="#0000FF"]V[/COLOR]ideo [COLOR="#0000FF"]M[/COLOR]ouse?

---

### Post by jgw on 2021-06-26
Always wondereed what KVM really meant - thank you!

Mine is a hardware switch between two physical computers.

---

### Post by dragonfly41 on 2021-06-26
[COLOR=#000000][INDENT]> That means, that it was frozen for about 3 to 4 minutes all told. (sometimes its forever)

Do you have this experience when you  disable all Firefox extensions and close tabs?

I would create a second firefox profile just for testing.

Does another browser such s Brave show these symptoms?[/INDENT]
[/COLOR]

---

### Post by tea for one on 2021-06-26
> **jgw said:**
> One is slow and keeps on crashing (kinda - wait long enough and it seems to uncrash)

Have you tried to reverse the switches on your KVM hardware?

Switch A to Machine A
Switch A to Machine B

Worth a few minutes to experiment?

---

### Post by jgw on 2021-06-26
It behaves this way even when the other machine isn't even turned on.  My kvm is for 4 systems (I use the others when I am messing with other computers)  I doubt it would make any difference as switching them is just a matter of changing plugs and this started before I had even plugged in the other system.  I figure if the other one is not even on and this is happening then where they are plugged in shouldn't make any difference.  It happens, for instance, when I am not even using the kvm which I tested before I installed the current one.  Oh, I just reconnected directly which was easier than switching the kvm connections as I have the three cables and just hooked them up directly.
Same problems.  

I am convinced something is running and hogging.  Just can't figure out what it might be.

---

### Post by TheFu on 2021-06-26
log files have anything?

---

### Post by jgw on 2021-06-27
Lordy!  Forgot about Logs!  I now have it on my dock so I won't forget it.  It hasn't blown up today, yet.  I have faith, however...........

---

### Post by TheFu on 2021-06-27
I have to say, my first gut feeling was some DNS issue.  That can make a fast system become really slow as the queries need to time out before failing, so checking the DNS differences between the systems couldn't hurt. Plus, somehow lots of 20.04 and later systems seem to run into DNS config problems much more often.

---

### Post by jgw on 2021-06-28
thanks for all the replies.  Here is a link to logs program.  This is what happens in less than 5 minutes.  I also mentions wireguard a lot.  I don't have wireguard on my system and I don't think it runs under 21.04 anyway.  Some pretty strange stuff in here.
[https://pastebin.com/JbyVxtdR](https://pastebin.com/JbyVxtdR)

---

### Post by QIII on 2021-06-28
Do you have your OS set to connect to a VPN on startup?  It is possible, if unlikely, that that could be where the Wireshark reference is coming from.

Do you have Geoclue installed?

Check your startup apps.  Eliminate everything that is not default and try then.  Some of those apps can suck up resources and bog you down.

---

### Post by jgw on 2021-06-29
Thanks for the reply!
Its "wireguard".   I checked my vpn (PIA)   Since they are my vpn I don't need wireguard as i think that too is a vpn which is, I think, free!

Here is what starts up:
backups (backs up every 7 days)
firefox (browser)
im-launch (mystery)
private internet access (vpn)
ssh key agent (not sure why or what)
thunderbird (mail)
zapp-sn-watcher (have no idea)

No geoclue

The problem is actually pretty simple.  There is something running and, when it runs, nothing else can happen and my mouse freezes.  Even when it isn't it won't work.  When this happens it takes from 2 to 8 minutes before my system will work again.  If I had a clue as to what it was I would deal with it but when everything is frozen I am stuck.  What I was hoping for was a program that would simply keep track of what was running and how many resources were being used.   I guess there is nothing like that.   If I was younger I would just write it but, I fear, those days are over.  Since my mchines have nothing of real value, my other option is to save everything I can, on another drive, and then just start over from scratch.  its a pain but its also, I suspect, a solution.  I didn't have, incidentally, all these problems before I moved to 21.04 from 20.04.2   I still have two machines that have not moved and they work just fine.

---

### Post by corradoventu on 2021-06-30
Open 'system monitor' and keep it open on 'resources' so when your system hangs you may have an idea of the problem.

---

### Post by TheFu on 2021-06-30
There are 20+ system monitoring tools.  These can write to local and remote systems, provide graphs for most things, and feed into alarming systems. Those alarm system can notify someone or attempt to fix known problems without bothering any humans.  Something like Zabbix or opennms or nagios .... there are at least 20 of these tools.  SysUsage is one of the simpler tools. I ran that for a few years.  Then moved to Munin.  Of course, you can create your own using sar, but that's really old-school.

---

### Post by ActionParsnip on 2021-06-30
if you run:
```

top

```
and watch the terminal as you use the system does anything hog the CPU or RAM?

---

### Post by jgw on 2021-07-06
Here are some links to my logs.  These are from the logs program itself.  Its broken down into: 
important
all
applications
system
security
hardware

When I read these things there always seems to be something missing, not whatever, can't find, or doesn't have something.  Security lists a lot of things that can't be found, not there, or the wrong thing.  Security failed to discover or is skipping and it all has to do with a 'uri' file.  Applications is similar to security.  it just goes on and on.  My main problem is that I really have no idea what is really something that needs attention or not.  I tried leaving the monitor on but when things freeze I can't move the mouse so I am doomed, same with all the other stuff.  I can't see it unless everything is dandy.  Once I have a freeze I usually have to re-boot.  Even when I re-start strange things happen.  I automatically start firefox.  then I decided to close that and just deal with my email.  I tried to stop it and failed,  then I went to the system monitor and tried to stop it- and failed.  then I tried to kill it - and that didn't work either.  It just sat there.  the wonder was that firefox was frozen but my mouse was working everywhere else.  

Here are some links to the logs program results.  I don't know what else to do.  Perhaps some kind person can give me thoughts on this stuff.  I also suspect that I am probably going to far and expecting too much.   

all_log.txt                  [https://pastebin.com/j7MxcXZK](https://pastebin.com/j7MxcXZK)
hardware_log.txt        [https://pastebin.com/TvqZQQxL](https://pastebin.com/TvqZQQxL)
security_log.txt          [https://pastebin.com/bFJyM1v8](https://pastebin.com/bFJyM1v8)
system_log.txt           [https://pastebin.com/gcP8fAX6](https://pastebin.com/gcP8fAX6)
important.log.txt        [https://pastebin.com/jdJVkfcq](https://pastebin.com/jdJVkfcq)
applications_log.txt     [https://pastebin.com/Mn64x9wc](https://pastebin.com/Mn64x9wc)

---

### Post by TheFu on 2021-07-06
System monitoring: [https://www.howtoforge.com/tutorial/server-monitoring-with-munin-and-monit-on-ubuntu-16-04-lts/](https://www.howtoforge.com/tutorial/server-monitoring-with-munin-and-monit-on-ubuntu-16-04-lts/)
I expect the setup for newer releases is the same or extremely similar.
Monitoring helps determine why a system is slow and narrows down why.

---

### Post by jgw on 2021-07-07
"https://www.howtoforge.com/tutorial/server-monitoring-with-munin-and-monit-on-ubuntu-16-04-lts/" says its good up to ubuntu 16.04.  Before I follow those instructions I need to know if it will also work on 21.04   (I have tried older stuff before and sometimes it didn't quite work)  This also assumes its dealing with a server.  I have no idea if I have a server!  This is a question I have been thinking of asking about - are all versions of ubuntu servers or do I have to add something to become a server?

Any help is appreciated and thank you for the reply!

---

### Post by TheFu on 2021-07-07
There is a separate ISO to install "Ubuntu Server."
If you have a GUI, then you didn't install Ubuntu Server.  That's the easiest way to know.
Server management is all through text config files, since there isn't any GUI.  It matters because some people are server-only and others are GUI/DE only.

---

### Post by TheFu on 2021-07-07
It is possible to run desktop programs with GUIs after some dependencies are added onto a server, but it isn't the integrated GUI that most Ubuntu Desktop users would prefer.  OTOH, if you dislike the GUI limitations, usually GUIs offer about 20% of the config options and only the most trivial configs, then you'll prefer the server configurations.

If you have a "desktop", you can install any server programs, but with the understanding that there won't be any GUI to configure them and you'll need to use the CLI to start/stop/enable/disable each part.   OTOH, almost always, server instructions are close enough between releases since there aren't any GUI programmers (often noobs), screwing things up.

So ... when it comes to system monitoring, please understand that all the GUI options are toys compared to real monitoring tools.

If you want to know what you get for these things spend 20 minutes on youtube.  They will almost always have a web interface to access the detailed monitoring statistics for 20-50 things about any Unix platform.  It provides a complete picture, unlike **top**.  Nothing against top, I use it a few times a week, but when I need to see what happened yesterday, last week, last month, and perhaps 9 months ago related to performance, top doesn't cut it.  

For example, all my servers have spikes overnight at slightly different times. I'm used to seeing those. They are expected, required. The overnight spike should relate to the time when backups are pulled.  If a system spikes at a different time too, then I know to look at some other aspects of the data to figure out which application caused it, then I can look at just that program's logs to understand why.  Then I can look for patterns - perhaps it happens every 7 days at the same time?  Why?

---

### Post by jgw on 2021-07-07
thanks for the replies.

Seems I am not a server.  How do I make sure?  Then, if not, how do I turn this machine into a server.  (when I updated I just went out, copied Ubuntu file and then put it on a cd and installed it)

I know little about gui.  My understanding is a gui is a program that presents stuff instead of dealing with the terminal.   I suspect my understanding is just wrong.  

(ignorance is not always bliss)

---

### Post by TheFu on 2021-07-07
Do you ever use a mouse with your setup in anyway?  That's a desktop.
Your signature says "gnome" - that's a GUI program.

---

### Post by jgw on 2021-07-17
Thank you for the replies! 
ill 
After messing with what I have I have decided to install ubuntu server which, I suspect, is going to solve a lot of my problems.  That being the case I will mark this as solved.  (I wish there was a setting for just quitting a topic instead of saying its solved when it really isn't)

---

