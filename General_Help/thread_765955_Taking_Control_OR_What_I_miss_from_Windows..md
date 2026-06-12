---
title: "Taking Control OR What I miss from Windows."
date: 2008-04-24
forum: General Help
---

### Post by TimPy on 2008-04-24
Hello.  I have been a fairly happy ubuntu user for about six months.  After my initial problems with installing ubuntu, I was completely satisfied with ubuntu. Unfortunately, lately (about a month or two ago) ubuntu started running at a very slow pace. It was not related to desktop effects or how much I was running on my computer. It would seem to come at random times, and restarting didn't always fix it. At first this was caused by a poorly configured Xorg file.  I fixed that, and now Xorg hardly ever takes over 20% of my cpu. (I ran top.)  

The odd thing was that my computer would run great at some times, and so slow it was unusable at others. The re-configured Xorg file only worked for about a day.  After I restarted a computer, other proccesses decided to clutter up my cpu.

Although I haven't really looked at what is eating my cpu, I figured I would ask about my windows instinct: Kill and then restart a process that is causing me trouble. Is there a way to do this? Is this the 'ubuntu way'?  If I have to look up, figure out what each proccess is doing and why it is taking up so much cpu, then figure out how to fix the problem, restart, and then tackle my next problem, It may take a long time. Do I need to provide examples of what is eating up my cpu, or is there a 'quick fix' to this.

I suppose I miss the consistency of windows: It was always sluggish and I would generally know what was causing it. Do I just need to become more educated with the ubuntu world to figure this stuff out?

For reference, I am currently running KDE (though I have gnome and xfce), about to upgrade to Hardy,  have a 1.3 gighz proccessor, 512 meg of ram, and an intel graphics card that doesn't seem to show up with problems in a google search.

---

### Post by natrixgli on 2008-04-24
It's a good idea to know what the process is before you kill it, of course... 

When you run top, you can see on the left of each process it's number, and then you can run the kill command:

```
me@mybox~$ kill -9 xxxx
```

Where xxxx = number of process.

-or- 

```
me@mybox~$ killall -9 nameofprocess
```

for more details, run 'man kill'


Another handy command is the 'skill' command. I often find handy:

```
me@mybox~$ sudo skill -KILL -u username
```


to kill all processes for a specified user. Of course it's probably a good idea to make sure that the target user isn't someone on your network typing page 998 of their novel in an unsaved text document.... 


If you prefer a more windows-like approach, you can launch the system monitor. Bear in mind you can only kill processes run by you unless you use 'sudo', but that can be dangerous. Be careful.


-n8

---

### Post by TimPy on 2008-04-24
I believe the ubuntu approach will work for me.  However, what will be the behavior of a proccess after I kill it?  If it is a crucial proccess, will it bounce back up?   For example, if I kill Xorg, will it crash my system?  I am also possibly looking for a more permanent approach: How do I slim down the number of high % eating cpu proccessess? I suppose I should look for each individual one, figure out what it does, and figure out how to stop it.  Is this the best approach?

---

### Post by natrixgli on 2008-04-24
Well, most *really* important stuff will require root privileges to kill, so if you see 'operation not permitted' then you have stumbled on such a case.

using the -HUP signal will kill, then respawn a process (again, see 'man kill' for more info)

```
me@mybox~$ kill -HUP xxxx
```


As for slimming down, there may be some things you don't need under System > Preferences > Sessions, and/or System > Administration > Services

I'm sure I don't gain too much by doing so but I always disable Bluetooth and Evolution Alarm Notifier since I don't use those... 

If you have an older PC you might want to try using Xubuntu instead which uses a lighter weight desktop called XFCE.

The best thing to do would be read up on the forums, search, and google stuff like 'ubuntu performance tweaks' etc. Think about how much time it took to become a Windows Expert... It takes much less time to become an Ubuntu expert because GOOD info is much more readily available.


Cheerio,

-n8

---

### Post by vexorian on 2008-04-24
Don't go around killing processes, if something out there is making your PC slugish then this is a bug , the first step is to recognize what is causing it.

run gnome-system-monitor and go to the proesses tab, there you can find the CPU eating process.

Tell us what it is.

Also, try disabling compiz... And do a memory check.

btw, if you want to kill a process by name you can use

```

pkill processname

```

If you want to use kill's funny extra options options:

```

kill options $(pgrep processname)

```

If you like taking control, this OS is for you, this is the reason I moved from windows, although it requires some effort to learn the tricks.

---

### Post by ZeroZ400 on 2008-04-25
Read up on this: [Rute User's Guide]("http://rute.2038bug.com/node12.html.gz")

Also, do NOT use "kill -9"  A normal kill should do, killing a process in windows is like using kill -term (if i remember right).  Kill -9 is like nuking the process and can crash your system.

---

### Post by xaenyx on 2008-04-25
Run

```
ps ux > ~/proclog.txt
```

Then post the contents of the 'proclog.txt' file in your home directory.

Also, what kind of hardware do you have?

---

### Post by TimPy on 2008-04-25
vexorian: Right now my desktop is running quite smoothly.  Whenever it starts flipping out, I'll run top. (I'll have to write them down paper and pen style though, whenever it flips I'll be lucky to be able to run top)

xaenyx: What does that code do to benifit me? But when I get to it, I will run that code.

ZeroZ400: I'll make sure and read that guide and tell you what I get out of it, thanks.

---

### Post by TimPy on 2008-04-25
vexorian: Right now my desktop is running quite smoothly.  Whenever it starts flipping out, I'll run top. (I'll have to write them down paper and pen style though, whenever it flips I'll be lucky to be able to run top)

xaenyx: What does that code do to benifit me? But when I get to it, I will run that code.

ZeroZ400: I'll make sure and read that guide and tell you what I get out of it, thanks.

---

### Post by straxus on 2008-04-26
In case you were wondering, this link explains why you shouldn't use "kill -9" willy-nilly:
[http://speculation.org/garrick/kill-9.html]("http://speculation.org/garrick/kill-9.html")

As Zero said, a simple kill command will suffice most of the time.  I just wanted to reiterate that point, as it's a very important one.

---

### Post by TimPy on 2008-04-29
First aof all, thanks for the previous help: I've learned some new things about proccessess. Unforutnately, my problem has not changed.

I just recently installed ubuntustudio - and I still have the same problem.  Although I still can't find hardly any ryhme or reason, I think that random programs take up lots and lots of cpu right before and after my Xorg server decides to reset itself.

For example, when I logged into gnome with ubuntustudio today, it took about 7 minutes to bring up (compared to the normal 30 seconds.) I switched to another xserver with Ctrl F6 about halfway through the load, and nautilus, gnomepanel, and one other program were taking 30% cpu each. As I'm typing this in epiphany, my cpu is going of the wall and my computer is slow.

Basically- I've come to this conclusion: With no ryhme or reason that I can figure out, ubuntu, no matter what flavor, decides to let cetrain programs, generally graphical in nature, but I can't tell for sure- large portions of my cpu for no reason. I am in desperate need of help. If this isn't fixed, I can't work with Ubuntu in any sort of productive enviroment. I'm willing to try anthing at this point, although quickest fix is best right now. 

So, please help with ideas and possible solutions, I will appreciate it- I might make a new thread sometime if I get no replies.
--------------------------------
I noticed something new: currently, Xorg is causing my problem, not epiphany: I had recently fixed a problem with xorg- was it just a fluke fix? I'm so confused right now.

---

### Post by vexorian on 2008-04-30
Well, I see 'graphics' and xorg everywhere in your post, so, guesses:

* Bugged graphic card driver, try googling for your graphic card and similar reports in *n*x

* Compiz-fusion, try disabling it for a while (disable desktop effects) and see if it helps.

* Post details about your hardware.

---

### Post by KeyserSoze93 on 2008-04-30
You've got KDE, GNOME and XFCE? That could slow things down if they all have their own sets of daemons (background tasks, like auto mounting stuff, that kind of thing) running at once... 

Check the process list when KDE is running for any GNOME related processes.

---

### Post by wirelessmonkey on 2008-04-30
I find that htop works better for diagnostics than top.  sudo apt-get install htop
then you can watch/sort items in the htop display.  Just leave it running in a terminal window, rather than starting it after your problems show up.


Best of Luck

---

