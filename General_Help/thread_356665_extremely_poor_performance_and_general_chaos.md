---
title: "extremely poor performance and general chaos"
date: 2007-02-08
forum: General Help
---

### Post by easterlingman on 2007-02-08
Hello everyone, this is my first cry for help on the ubuntu forums - I've recently switched from windows xp to 64 bit edgy with xfce & beryl.. for the past week I've been trying to get my computing life together with this new software, but certain things are standing in my way - the chief among these is general lagginess.  firefox seems to run slower than it did on XP, and every so often something will eat up all the power of my processor, and I can't seem to find out what it is or how to kill it.  When I try to use the xfce4-taskmanager it shows me that the thing that is using most of my processor is 4 xscreensaver tasks all at 8%, and occasionally Thunar flashes on to indicate that it is using 240% of my processor.

ok, my question is: does xfce suck?  should i be using something else?  what do you usually do when your ubuntu slows down?  also, how do you uninstall things in ubuntu?  i keep apt-getting things but i'd like to know how to find out all the things i've installed and how to get rid of them... i like running a tight ship.  is there any chance that 64 bit things are slowing me down?  i was under the impression that things optimized for 64 bit processors (and i've got one) run faster than their 32 bit counterparts.  

i've got many more problems but i'd like to solve the basic ones first... any help would be appreciated.

---

### Post by cleentrax on 2007-02-08
I don't have a 64-bit computer yet, but from what I've read, you're better off at 32 bit right now, unless you have an absolute need for 64 (like 32gb of RAM, or a 64-bit app).

As for xfce, I'm running it (6.10, was 6.06) on my server, and I haven't had any memory problems to speak of. It seems light and stable.

If it's not too much effort, I would suggest going back to 32bit for a while.

---

### Post by kebes on 2007-02-08
First off, welcome.

Now you brought up a whole bunch of issues... I'll try to deal with as many as I can.


Firefox lagginess can sometimes be caused by IPv6 being enabled. In the firefox address bar, go to the location:
about:config

then search for "ipv6", you'll see an option:
network.dns.disableIPv6
You can set this to "true" so that it doesn't bother with IPv6 lookups. Sometimes this speeds up performance. You can also disable IPv6 system-wide, which might help.


Then again your lagginess seems to be some strange process running out of control. This is not normal. What I typically do is use the commandline for these sorts of things. So open a terminal and run:
top

This will list the programs that are running and how much cup% they are using. If you see something that is using tons of CPU and you want to force it to quit, you can kill it. Just look at its name, and then quit the "top" program (by pressing q) and then type:
pgrep *name* -l

This will show you the process id (PID) and name of any programs running that match your search string. You can then use:
kill ####

(where ### is the PID of the program you want to kill). Of course it's not usually a good idea to kill random programs, so do a bit of searching on the program name, and see if it should or should not be using so much CPU.


Does xfce suck? I don't think so, but I don't use it myself (I prefer KDE). Lots of people use xfce and say it runs great. In fact typically xfce runs faster than Gnome or KDE because it is smaller. However if you have modern hardware, you may prefer KDE or Gnome, and can give those a try. It shouldn't run slow, however, and so it's worth figuring out what process is causing trouble. You can copy and paste the output from top in this thread and maybe someone can spot something amiss....


About uninstalling. Since you seem comfortable with apt-get, you can use it to uninstall:
sudo apt-get remove *programname*

I personally recommend that you use "aptitude" instead of "apt-get", however. It's the exact same thing, except it stores extra info that makes uninstalling more robust (it actually removes libraries that are no longer necessary). So you can similarly go:
sudo aptitude install *programname*
and
sudo aptitude remove *programname*

---

### Post by easterlingman on 2007-02-27
Hello again, thank you so much for the suggestions.. I've been using top to identify erronious process and kill them (though i'm not sure how to find a specific process id with top), but I still seem to be having weird performance issues... maybe it's just the norm for linux systems?  I'm used to processor usage hanging around 0% - 5% while idle, but according to the cpu monitor the norm is closer to 20% to 40% with fluctuations up to 100% every 10 seconds or so....

what process do you go through to identify exactly what is running on your system and which processes are slowing things down?  i've compiled my kernel (it wasn't optimized for my processor) which seemed to speed things up for a while but I'm getting depressed about it again...  amarok is slow but it's my only option because apparantly there are no other linux programs that can handle a large (200+ gigs) music collection...  

woe is me!

---

### Post by easterlingman on 2007-03-01
I've solved a bit of my problem by removing gdm from init.d - I'd switched to xfce and gdm wasn't unloaded from the boot list (and i had no need for it anymore), so taking it out recovered a ton of memory and made everything snappier... what's the deal with gnome bulk!

---

### Post by easterlingman on 2007-03-02
I've found ANOTHER reason behind my poor performance... klogd was taking up a massive amount of cpu time for some reason, so I killed it....  I'll just have to go without kernel messages for a while

---

### Post by RedSquirrel on 2007-03-03
Just reading through this, it seems to me that someting is very wrong with your system.

Could you provide your system specs? CPU, RAM, etc.

Did you try the default kernel? Any chance something is wrong with your compiled version?

I've never used the 64-bit version of Ubuntu/Xubuntu, but I'm really surprised that you'd have to jump through that many hoops to get things working properly.

I'm using the 32-bit Xubuntu (i.e., XFCE) on fairly old hardware (this linux box is over six years old!) and runs as smooth as silk. 
I've used GNOME and it runs fairly well, but it is a little sluggish on this box.

You can use Synaptic to have a look at the programs installed on your machine (it should be in one of the menus; Applications -> System, I think). It's a graphical program, so you can do pointing & clicking if you prefer that. Synaptic is just a graphical frontend for apt-get and it's a nice way to look at what's installed. Once you know what you want to add/remove, using aptitude to install and remove has some advantages. See this page for more details:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by easterlingman on 2007-03-03
Yeah it seems that way.. I'm not sure though.  I haven't had any problems in the past day or so, but I do know that there is some problem with my motherboard since for some reason I can't get more than 512 mb of ram to work (I've got 2 512 modules but if I try using the second one and running memtest I get tons of errors - but no errors with just the one 512)

Athlon XP 3000+
512 mb DDR 3200
generic mobo K8M800
Nvidia Geforce 7800 GS
a 40 gig main (wd) drive and a 500 gig sata secondary drive (also wd)

anything else you want to know?

---

### Post by easterlingman on 2007-03-04
I seem to have phantom CPU cycles being consumed... sometimes cpu usage will go up to max for a while (a few minutes and then drop down) - top doesn't show any process using that much CPU time, but there's a large amount of cpu time being used by "wa" - i'm not sure what that stands for, but it doesn't seem to be associated with anything i'm running...  i can't find any info about it by searching.

---

### Post by RedSquirrel on 2007-03-04
Thanks for posting your specs.

I thought the Athlon XP was 32-bit. I guess they released a 64-bit version at some point. Interesting.

In any case, I personally wouldn't run the 64-bit Ubuntu on anything other than the latest AMD64 processors, not the Athlon XP. And even at that, I would probably go for the 32-bit Ubuntu even if I had one of the newer CPUs. I don't think you'll see a huge difference in performance when comparing 32-bit to 64-bit Ubuntu. The latter might be a bit quicker, but I just don't see it making that much difference. (Someone who has experienced a big difference might correct me on this.)

So, I would agree with cleentrax (above) that the 32-bit is a better option for you. With your specs, Ubuntu should be running very well, not bogged down as you have described. You shouldn't have to disable gdm or klogd for a system like yours. Even on my old box, these things cause no trouble at all.

You mentioned that you installed a bunch of stuff. It's possible that something you installed has issues, but I'm not really convinced that that's the real source of the problems. Again, I would suspect that custom kernel. Maybe it's something to do with Beryl, but I've never used it so I can't say much about it.

You mentioned your motherboard was having trouble. If you are having hardware issues, then that certainly can contribute to strange OS behavior. If you try the 32-bit version and that has trouble then it could be something to do with your hardware: bad motherboard, an unusual network card, etc. If your problems persist, you could try removing any "extra" hardware and see if that helps, then add things back in one at a time. That would help you trackdown what device is causing trouble.

Just to let you know, having a massive amount of resources being used all the time (CPU at 20% - 40% most of the time) is not the norm for a linux system. On a properly configured system, you would never see that, so something isn't right with your system.

By the way, the "wa" you mentioned is "Amount of time the CPU has been waiting for I/O to complete." (see the man page for "top": 'man top' in a terminal). On my system, it's usually zero. There might be a good reason for your "wa" to be high, but it sounds strange to me.

You could try having a look at some of the logs in the directory /var/log and see if there's anything strange going on in there. /var/log/messages or /var/log/debug are good ones to start with, but there are a few more in that /var/log directory.

---

### Post by easterlingman on 2007-03-05
Whoops, I miswrote my processor type - there is no 64 bit athlon xp, the proper specification is athlon 64.  

my only remaining problem is the 'waiting for io operation to complete'.  is this because of the kernel?  i've looked in the kernel log (dmesg, right?) and i don't see any flagrant errors... there are many different kinds of logs in /var/log - which one would i look at to see a log of all the I/O operations to find out what it is that my processor is using all its time waiting for?

---

### Post by easterlingman on 2007-03-05
hm.. gconfd (gnome config server?) seems to be starting up and shutting down all the time.. maybe that's a problem?  i can't seem to remove it.. i'm using xfce.. how would i get rid of gconfd?

also a lot of the messages in my /var/log/messages are just -- MARK -- 
what does this mean?

---

### Post by RedSquirrel on 2007-03-06
The -- MARK -- is just a timestamp. It occurs every 20 minutes by default.

I'm not sure what else to suggest at this point. I haven't had these issues myself....... I still think I would try the default kernel unless you found that didn't work well either...... kind of out of ideas at the moment.....

---

### Post by easterlingman on 2007-03-07
Edgy 6.10 comes with kernel version 2.6.17-generic.  is there any reason i shouldnt've compiled 2.6.20?  is it just that 2.6.17 was the current version when 6.10 was released?

---

### Post by RedSquirrel on 2007-03-08
There's nothing wrong with using a newer kernel. The nice thing about using the default one though is that is has been tested and should basically work without too much fuss.

You're having some pretty strange things going on. IMO, I would use the most vanilla system setup to see if that works and then go from there. Doing it that way means one can attack the root cause(s) of the problems they are experiencing rather than tracking down and treating a bunch of symptoms.

If I had your system and your issues, I would:

1. backup any important files (e.g., files you created in your home directory), 
2. wipe the hard disk with "killdisk" [[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)], 
3. install the 64-bit version without any modifications, and see how that works. 
4. If that still has major problems, I would try the 32-bit version. 

If neither version works, then there could be a hardware issue with your machine. 

All of that may sound like overkill to you, but that's what *I* would do. I would want to get things up and running quickly so that I can at least use the system without having to go and disable a bunch of programs (gdm, klogd, etc.). Just my opinion, though. It is *your* system and you must do what you feel is right, of course.

BTW, I noticed there is x86 64-bit Users forum:

[http://ubuntuforums.org/forumdisplay.php?f=134](http://ubuntuforums.org/forumdisplay.php?f=134)

From limited scanning of posts there, it seems that the jury is still out on the 64-bit Ubuntu. :(

---

### Post by easterlingman on 2007-03-08
I think I'll try this once Feisty comes out... thanks for the advice.

---

