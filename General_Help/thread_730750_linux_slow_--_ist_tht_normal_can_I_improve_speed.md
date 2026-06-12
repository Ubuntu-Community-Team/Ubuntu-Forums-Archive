---
title: "linux slow -- ist tht normal? can I improve speed?"
date: 2008-03-21
forum: General Help
---

### Post by wiggie on 2008-03-21
I know I have a rather outdated system, but I didn't think it would slow down linux that much. Here are my specs:

AMD K7 Thunderbird at 1.4 GHz, but only works at 1.05 GHz, because (my guess is) it heats up too much and locks up
512 MB RAM
NVidie Gforce 4 with 128 MB
7200 rmp HDD

Yes, this system is old BUT:
- does flash have to be so troublesome and stutter half the time (dispite the fact that flash sucks, and youtube should actually be running divx or xvid)
- I sometimes have to wait a long time just to switch between tabs in either opera or firefox
- i definitely sense the problem to be on the graphics side, but I thought my video card should take care of that... it somehow does
- it makes little difference if I turn off compiz fusion, since I don't use too crazy effects
- i'm running gnome but use amarok, and had to turn off the OSD so that it won't stall when a song changes, again blaming the graphics; and yes I know that amarok needs kde libs and that takes up memory
- browser issues, again: i think scripting is a huge damper, for example, when I open a flickr page, it slooooows dooooown, like I would be running through water; this most likely is a processor issue
- browsing high resolution photos.... more or less a no go, and trying to open it up and click next in f-spot definitely eats away my time
- ok there might be others I can't think of right now, ask and I shall answer

possible solution not involving extra costs:
- get rid of processor/memory/graphic hungry apps such as compiz fusion
- don't use a gui browser.... yeah right
- boykott flash, I think it's my arch enemy, I can't believe it is so widely accepted, especially on things like youtube, I'm dumbfounded
- does it make sense to use , for example, iceWM vs Gnome? Will I feel the difference?
- compile the kernel on my pc -- does that help? I heard it makes it faster since the kernel adapts to the hardware, I need a confirmation on that

I cannot compare it MS Windows, since I abandoned it over a year ago, and if I remember correctly, it was  faster then linux.

And a final question: Which system would be adequate in order to not get a slow linux? Minimally a dual core 2 gb machine?

Thanks for your upcoming replies!

Wiggie

---

### Post by jespdj on 2008-03-21
So the processor runs only at 1.05 GHz because of an unknown problem? It sounds like the hardware is getting old and is starting to fail, and when that happens you can expect all kinds of strange and unpredictable problems like slowdowns, random lockups and spontaneous reboots.

Linux in general doesn't have hardware requirements that are as high as Windows. You could try running Xubuntu instead of Ubuntu on it.

The first thing I would change on that hardware is add an extra 512 MB of memory to it.
> And a final question: Which system would be adequate in order to not get a slow linux? Minimally a dual core 2 gb machine?
That's impossible to answer because it depends on what you think "slow" means. But you certainly do not need the newest and fastest Core 2 Duo to run Ubuntu.

---

### Post by cmnorton on 2008-03-21
I have a slow Pentium laptop, and I maxed the memory to its limit, 1GB. It might be a 2.x speed non-hyperthreaded Intel CPU. I cannot quite remember. It is slow to log in, but not sluggish, once logged in. 

XUbuntu is often recommend for slower computers, because there is not as much demand for graphics resources. If you can max your memory, that involves spending money, but perhaps is not as much grief as re-installing Ubuntu.

---

### Post by Npl on 2008-03-21
first thing you should do is disable or preferably uninstall that damn tracker-tool. Takes up >100MB and stresses CPU, next Ubuntu version wont install it by default either. Related packages are libtracker-gtk0 tracker tracker-search-tool, uninstall any of em via Synaptic.

And generally, no matter what some zealots say, alot of opensource-apps/libraries simply arent as fast as comparable stuff on Windows. There are good reasons (flexibility) and bad reason(weird 'academic' designs) for that.

Forget compiling kernel, the kernel is fine, its the amount and in some cases the perfomance of packages that are eating away performance. Try disabling services you dont need for starters, look for the Entries Sessions (Sitzungen) and Services (Dienste) in the System-Menu.
Regarding Browsers, you could try Opera9.50-prereleases, they are a good deal faster than the current release: [http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

### Post by wiggie on 2008-03-21
Thanks for the replies folks, greatly appreciated.

what does the tracker-tool do? Tracks stuff I guess. Well, I'll uninstall it, thanks for the tip.

I thought that linux software was slower then windows software. Oh well, that's how it is, I guess I'll have to save up and buy a new pc.

---

### Post by Ender305 on 2008-03-21
I think linux is faster, of course, I had vista, the slowest of the slow

---

### Post by HermanAB on 2008-03-21
Uhmm, I'm writing this on my 650MHz Eee PC running a full KDE desktop.

Sooooo, if your PC is slow, then there is something wrong with your setup and more often than not, it is due to a lame DNS.

Check /etc/resolv.conf and ensure that the nameservers listed are all good.  Compare it with the nameservers used by a Windows machine (c:\> ipconfig /all)

You can test a name server with 'dig'.

Cheers,

Herman

---

