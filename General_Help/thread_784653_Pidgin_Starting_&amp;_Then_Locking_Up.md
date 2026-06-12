---
title: "Pidgin Starting &amp; Then Locking Up"
date: 2008-05-06
forum: General Help
---

### Post by money2themax on 2008-05-06
is anyone else having that problem too?

---

### Post by money2themax on 2008-05-06
bump

---

### Post by Exsecrabilus on 2008-05-06
It happens for me.....and on Firefox too.....

But I just wait a few minutes and it unlocks.

---

### Post by money2themax on 2008-05-06
> **Exsecrabilus said:**
> It happens for me.....and on Firefox too.....

But I just wait a few minutes and it unlocks.
fire fox locked up but i fixed that by hitting my router but pidgin is just being stubborn

---

### Post by dyous87 on 2008-05-06
This has been happening to me a lot in pidgin since upgrading to 8.04. In fact it has been happening to a lot of apps. I like hardy but it really doesn't seem as stable and speedy as it should be. Perhaps it was releases too soon.

---

### Post by money2themax on 2008-05-06
> **dyous87 said:**
> This has been happening to me a lot in pidgin since upgrading to 8.04. In fact it has been happening to a lot of apps. I like hardy but it really doesn't seem as stable and speedy as it should be. Perhaps it was releases too soon.
your probably right cur this didn't start until after i upgraded to hardy

---

### Post by neur0 on 2008-05-06
Confirming the Pidgin freeze (with 50%+ CPU usage) and also Firefox instability (It may or may not unlock after a minute or two)

---

### Post by money2themax on 2008-05-06
> **neur0 said:**
> Confirming the Pidgin freeze (with 50%+ CPU usage) and also Firefox instability (It may or may not unlock after a minute or two)
now all we need is an admin to read this and this thread can be listed as solved

---

### Post by storm99999 on 2008-05-06
I've been experiencing a similar issue, in which most apps will lock up or fail to properly start.  The only thing I can do to temporarily fix it is switch the scheduler to another one and back, for example:
```
sudo -s  
echo deadline > /sys/block/<hard disk with root on it>/queue/scheduler
<Wait a bit, maybe check the load or something for a few seconds>
echo cfq > /sys/block/<hard disk with root on it>/queue/scheduler
exit
```

This seems to break a deadlock the system has, at least on mine.  It's smooth sailing after that commandset gets run.

---

### Post by money2themax on 2008-05-06
> **storm99999 said:**
> I've been experiencing a similar issue, in which most apps will lock up or fail to properly start.  The only thing I can do to temporarily fix it is switch the scheduler to another one and back, for example:
```
sudo -s  
echo deadline > /sys/block/<hard disk with root on it>/queue/scheduler
<Wait a bit, maybe check the load or something for a few seconds>
echo cfq > /sys/block/<hard disk with root on it>/queue/scheduler
exit
```This seems to break a deadlock the system has, at least on mine.  It's smooth sailing after that commandset gets run.
what exactly is this supposta do?

---

### Post by storm99999 on 2008-05-06
The first line switches the user to root (because sudo doesn't seem to work on the commands later).

The next command tells the computer to change how processes are given time to do their job to the "deadline" scheduler.  The switch (apparently) causes all incomplete tasks to finish, including what appears to be a task that never got around to finishing and is locking up the system (of which I do not know what).

There's the wait, to make sure it works.

Then the next command switches the scheduler back to what is normally used in Ubuntu, the CFQ scheduler, or the Completely Fair Queuing scheduler.  This is to make sure the system works as intended.

The last command escapes from root user mode just in case, as it's never good to stay as root.

Additionally, if one needs to, I sourced the command off of this article: [http://www.wlug.org.nz/LinuxIoScheduler](http://www.wlug.org.nz/LinuxIoScheduler) , specifically the part about "Changing Schedulers".

---

### Post by dyous87 on 2008-05-06
So are you saying that running those commands just one time will fix this lock up problem with applications in Hardy?

---

### Post by storm99999 on 2008-05-06
Unfortunately, it's only temporary.  I've been messing with my kernel trying to find a fix, but nothing's appearing.

---

### Post by dyous87 on 2008-05-06
> **storm99999 said:**
> Unfortunately, it's only temporary.  I've been messing with my kernel trying to find a fix, but nothing's appearing.

So those commands need to be run whenever an application locks up huh?

This seems quite annoying, I was having none of these problems with 7.10, and it isn't as if I have a low spec computer. I have 2 gigs of ram and an Intel Core 2 Duo. I really hope it is patched sometime soon.

---

### Post by storm99999 on 2008-05-06
Hmm, it may not need be for every program, nothing bad has happened for over 40 minutes since I tested the command.  It probably only lasts until a reboot at best though.

I remember from some place that it might have something to do with the "Tickless System" setting in the kernel.

Searching for a boot command that was supposed to fix it, I came across [http://fedoraproject.org/wiki/KernelCommonProblems](http://fedoraproject.org/wiki/KernelCommonProblems)

Which has a part labeled "Crashes/Hangs" with this list of boot options:

[LIST][*]acpi=off is a big hammer, and if that works, narrowing down by trying pci=noacpi instead may yield clues
[*]nolapic and noapic are sometimes useful
[*]nolapic_timer can be useful on i386; on x86_64 this option is called noapictimer
[*]Given it's new and still seeing quite a few changes, nohz=off and/or highres=off may be worth testing. (Though this is kernel 2.6.21 and above only) 
[/LIST]

I'll try some of these and report back.

---

### Post by dyous87 on 2008-05-06
Alternatively, since you said that those commands should last until reboot, wouldn't it be possible to add them to /etc/rc.local so that they run every time on boot up?

If these commands are really a solution then this should work?

What do you think?

---

### Post by storm99999 on 2008-05-06
Hmm, it might work. However, I tried the boot commands, all the acpi and apic commands failed to work (I don't quite know why yet, the system just restarted before mounting disks) but nohz=off worked.  I'll stress the system out until it quits working soon, so I hope it holds up.

Edit: Nope, it quickly locked up.  I retryed the trick I've been using, but the processor was loaded a full 30 seconds before the load went to 0 again.  However, this stuff is heavily cpu reliant.  Next command then...

---

### Post by dyous87 on 2008-05-06
> **storm99999 said:**
> Hmm, it might work. However, I tried the boot commands, all the acpi and apic commands failed to work (I don't quite know why yet, the system just restarted before mounting disks) but nohz=off worked.  I'll stress the system out until it quits working soon, so I hope it holds up.

I tried them as well and got the same results. I think I may try adding those commands to my rc.local and seeing how it goes. If the system stops hanging or at least hangs less then its a good thing.

Do you have any details on why this is though? What is causing it?

---

### Post by storm99999 on 2008-05-06
Nope, I just tried switching schedulers based off a note in the kernel documentation that the deadline scheduler was more useful for systems with high performance disk drives.

---

### Post by dyous87 on 2008-05-06
> **storm99999 said:**
> Nope, I just tried switching schedulers based off a note in the kernel documentation that the deadline scheduler was more useful for systems with high performance disk drives.

Hmm I see, and by high performance disk drives I am guessing they mean anything more then a 7200 RPM HDD?

---

### Post by money2themax on 2008-05-06
> **dyous87 said:**
> Hmm I see, and by high performance disk drives I am guessing they mean anything more then a 7200 RPM HDD?
how do you find that out without opening the case?

---

### Post by storm99999 on 2008-05-06
The documentation was labeled "Copyright 2002", so probably.

I tried highres=off for a boot option.  It seems to have significantly lowered the load.  It crunches numbers for a minute after boot and when Firefox loads, it hasn't locked up more than a second, and that was once.  top states that the load is 0.16 0.64 0.40.  It doesn't quite zero it out, it hovers at 0.2~, but it helps.

---

### Post by dyous87 on 2008-05-06
> **money2themax said:**
> how do you find that out without opening the case?

What type of computer do you have?

> **storm99999 said:**
> The documentation was labeled "Copyright 2002", so probably.

I tried highres=off for a boot option.  It seems to have significantly lowered the load.  It crunches numbers for a minute after boot and when Firefox loads, it hasn't locked up more than a second, and that was once.  top states that the load is 0.16 0.64 0.40.  It doesn't quite zero it out, it hovers at 0.2~, but it helps.

Hmm that is interesting. I tried those commands you gave as well and so far I have not had one lock up. This is with Windows XP running in virtualbox so that is a big plus!! 

I will continue posting the test results here.

---

### Post by storm99999 on 2008-05-06
Well, my last test was the two in combination.  It started at 0.22 average over the last 5 minutes.  Upon entering the commands, it loaded up to 0.34 for 20 seconds and dropped to, at the moment, 0.04.  I still have no idea what causes this, but a common theme seems to be a late make Intel chip.  I'll keep track of it, and I hope this helps others that see it.

---

### Post by dyous87 on 2008-05-06
> **storm99999 said:**
> Well, my last test was the two in combination.  It started at 0.22 average over the last 5 minutes.  Upon entering the commands, it loaded up to 0.34 for 20 seconds and dropped to, at the moment, 0.04.  I still have no idea what causes this, but a common theme seems to be a late make Intel chip.  I'll keep track of it, and I hope this helps others that see it.

What CPU are you using btw?

---

### Post by storm99999 on 2008-05-06
> **dyous87 said:**
> What CPU are you using btw?

Core2Duo E6550 @ 2.8Ghz.

---

### Post by dyous87 on 2008-05-06
Ok I have an  Intel(R) Core(TM)2 Duo CPU T7100  @ 1.80GHz so this may be an issue that effects new Intel Dual Core CPU's, ironically as that may be.

---

### Post by money2themax on 2008-05-06
> **dyous87 said:**
> What type of computer do you have?

HP a1510n


> **dyous87 said:**
> 
Hmm that is interesting. I tried those commands you gave as well and so far I have not had one lock up. This is with Windows XP running in virtualbox so that is a big plus!! 

I will continue posting the test results here.

funny cuz my processor is 2.4GHz AMD Athlon 64 3800+

---

### Post by dyous87 on 2008-05-06
Well I looked up your computer and you definately do have a 7200 RPM Hard Drive.

Strangely however you are not using a recent model dual core Intel Chip. You aren't even using a dual core chip so I guess this problem is not related to our processor.

---

### Post by storm99999 on 2008-05-06
> **money2themax said:**
> 
funny cuz my processor is 2.4GHz AMD Athlon 64 3800+
Hmm... are you using the default build of Ubuntu (x86) or any special builds (x86_64)?  Other than that, I have no guess as to what's going on.  Maybe it's just late build computers, maybe it's SATA disks (which might be why changing the scheduler for a disk helps).  I do not yet know.

When I get time, I'll test kernel 2.6.25.2, as in 2.6.25.1 there were a few scheduler tweaks, and 2.6.25.2 is a bugfix of some error that the changelog does not make clear.

---

### Post by money2themax on 2008-05-07
> **storm99999 said:**
> Hmm... are you using the default build of Ubuntu (x86) or any special builds (x86_64)?  Other than that, I have no guess as to what's going on.  Maybe it's just late build computers, maybe it's SATA disks (which might be why changing the scheduler for a disk helps).  I do not yet know.

When I get time, I'll test kernel 2.6.25.2, as in 2.6.25.1 there were a few scheduler tweaks, and 2.6.25.2 is a bugfix of some error that the changelog does not make clear.
i'm using the X86 ver but i'm thinking about switching to x86_64 when my disks come in the mail
also i have another HDD that my OS is on and its a 30GB [speed unknown] it was purchased in 2000 in a HP running ME

---

### Post by money2themax on 2008-05-08
> **storm99999 said:**
> I've been experiencing a similar issue, in which most apps will lock up or fail to properly start.  The only thing I can do to temporarily fix it is switch the scheduler to another one and back, for example:
```
sudo -s  
echo deadline > /sys/block/<hard disk with root on it>/queue/scheduler
<Wait a bit, maybe check the load or something for a few seconds>
echo cfq > /sys/block/<hard disk with root on it>/queue/scheduler
exit
```This seems to break a deadlock the system has, at least on mine.  It's smooth sailing after that commandset gets run.
this isn't working cuz i don't know what HDD has root on it

---

### Post by money2themax on 2008-05-08
Bump

---

### Post by dyous87 on 2008-05-08
> **money2themax said:**
> Bump

Hmm you have two Hard Disk drives right?

If you open a terminal and install gparted:

```
sudo apt-get install gparted
```

and then run it from System>Administration>Partition Editor, you should be able to see your hard disks listed and the configuration and partitions on them including root.

Hope this helps,
David

---

### Post by money2themax on 2008-05-09
> **dyous87 said:**
> Hmm you have two Hard Disk drives right?

If you open a terminal and install gparted:

```
sudo apt-get install gparted
```and then run it from System>Administration>Partition Editor, you should be able to see your hard disks listed and the configuration and partitions on them including root.

Hope this helps,
David
yeah an gparted takes literally 1 hour to start

---

### Post by dyous87 on 2008-05-09
hmm that's very odd indeed.

What happens when you try to run

```
sudo gparted
```

from the terminal?

---

### Post by money2themax on 2008-05-09
> **dyous87 said:**
> hmm that's very odd indeed.

What happens when you try to run

```
sudo gparted
```from the terminal?
it starts but it hast read 3 HDDs 30GB, 200GB, & 120GB

---

### Post by kprateek88 on 2008-05-09
I'm having trouble with Pidgin after upgrading to 8.04 too. Every now and then it stops responding, and the exact symptoms vary. Sometimes other apps work. Sometimes the screen freezes completely, except that I can move the mouse, but clicking has no effect. In such cases I have to switch to tty1 and kill -KILL the pidgin process.

I'm using Compiz.

---

### Post by dyous87 on 2008-05-09
> **money2themax said:**
> it starts but it hast read 3 HDDs 30GB, 200GB, & 120GB

When you start gparted it should show the current configuration and paritions of your master hard drive. In the upper right hand corner there should be a drop down menu with the different hard drives.

For example: '/dev/sda', '/dev/sdb', '/dev/sdc', etc. or something similar to this. If not are you certain that those other hard drives are working/ installed correctly. Make sure the sata cables and power cables are securely in place. Also if you have jumpers on the hard drive you may want to make sure they are set for the right configuration. 

You master drive should be set for master and the others should be slave. 

> **kprateek88 said:**
> I'm having trouble with Pidgin after upgrading to 8.04 too. Every now and then it stops responding, and the exact symptoms vary. Sometimes other apps work. Sometimes the screen freezes completely, except that I can move the mouse, but clicking has no effect. In such cases I have to switch to tty1 and kill -KILL the pidgin process.

I'm using Compiz.

This is the exact same problem I have been having from time to time. With recent ubuntu updates however it has seemed to get a little better so make sure your system is fully up to date.

Also you may want to try this code posted by storm99999 which seems to help a bit:

```

sudo -s  
echo deadline > /sys/block/<hard disk with root on it>/queue/scheduler
<Wait a bit, maybe check the load or something for a few seconds>
echo cfq > /sys/block/<hard disk with root on it>/queue/scheduler
exit

```

Good luck,
David

---

### Post by MusicMastaMike on 2008-05-09
I was having this issue after I first installed Hardy.  I ended up completely purging my installation of pidgin, removed all but essential items from my ~/.purple directory, and then reinstalled.  Haven't had a single issue since.

> sudo apt-get purge pidgin* libpurple0 && sudo apt-get autoclean

Then, if you don't need anything in your ~/.purple directory:

> sudo rm -r ~/.purple

Then do:

> sudo apt-get install pidgin pidgin-data libpurple0

Hope this helps!

---

### Post by dyous87 on 2008-05-09
Just to add to what MusicMastaMike said above. Did any of you having these problems actually perform a clean install of Hardy or did you do an upgrade from a previous version of Ubuntu. 

The reason I ask is, and i believe this may be in relation to what he said about removing all of pidgin and then reinstalling, I first was using hardy after upgrading and I was having major problems but once I backed it all up and did a fresh install everything started running a lot smoother. 

It seems that a lot of these problems may be incompatibilities with software and their previous versions. 

David

---

### Post by MusicMastaMike on 2008-05-09
> **dyous87 said:**
> Just to add to what MusicMastaMike said above. Did any of you having these problems actually perform a clean install of Hardy or did you do an upgrade from a previous version of Ubuntu. 

The reason I ask is, and i believe this may be in relation to what he said about removing all of pidgin and then reinstalling, I first was using hardy after upgrading and I was having major problems but once I backed it all up and did a fresh install everything started running a lot smoother. 

It seems that a lot of these problems may be incompatibilities with software and their previous versions. 

David

I personally did a fresh install, BUT I had kept my .purple folder (backed up my whole home folder).  There were probably some settings and such in there that were messing it up.  I ended up deleting everything out of .purple except for my logs, smileys, and buddy list files.  Then I did what I said above, copied the files I kept back into the .purple folder, and all worked great!

---

### Post by storm99999 on 2008-05-09
> **dyous87 said:**
> Just to add to what MusicMastaMike said above. Did any of you having these problems actually perform a clean install of Hardy or did you do an upgrade from a previous version of Ubuntu. 


I personally destroyed everything as I wanted to have an encrypted root drive.  I just backed up home elsewhere and redid Pidgin, Firefox, and Evolution as it would take longer to restore than to actually do the job again.

However, my problems *were* a lot worse than what most describe, and that was that every single application was slowing down massively, but those two did the worst.  I know Firefox's was the SQLite database problem, but I do not know what Pidgin's problem was.  It seems though that I may have just been more affected by whatever bug is causing slowdowns all around as that tweak works both on mine and others problem so far.

I'll be keeping track of whatever I do in the kernel and if anything helps (highres=off is good, but mildly annoying as I prefer to use the default settings and the scheduler trick is annoying) I'll list it off.

---

### Post by money2themax on 2008-05-09
also i want to go back to firefox 2.x

---

### Post by dyous87 on 2008-05-09
> **money2themax said:**
> also i want to go back to firefox 2.x

you can install firefox-2 through synaptic if you like. Is there any reason you want to however?

---

### Post by money2themax on 2008-05-09
> **dyous87 said:**
> you can install firefox-2 through synaptic if you like. Is there any reason you want to however?
the new one is buggy as hell [actually i had a major system crash with 8.04 x86 so i'm switching to 7.10 x86_64 and i'll need the x86 libs]

---

### Post by storm99999 on 2008-05-09
I finally got around to trying out 2.6.25.2, and either the problem has subsided, or the kernel fixed it.  Dunno.  Without the hack for the scheduler or highres=off, I am getting 0.18 0.49 0.25 after a few minutes of testing (and firefox didn't flinch when I hit it with around 30 or so tabs... Pidgin up in seconds, instead of minutes.).  I'll push it to the limit as soon as I can to see if I can't get the schedulers to deadlock again.

---

### Post by bdcheung on 2008-05-13
> **MusicMastaMike said:**
> I was having this issue after I first installed Hardy.  I ended up completely purging my installation of pidgin, removed all but essential items from my ~/.purple directory, and then reinstalled.  Haven't had a single issue since.

Worked great!  Thanks Mike!

---

### Post by MusicMastaMike on 2008-05-15
Just an update... I started having some serious lock-ups again.  It seems that there is an issue with the pidgin-musictracker plugin.  I purged my installation of this plugin (sudo apt-get purge pidgin-musictracker) and everything went back to normal!

---

### Post by money2themax on 2008-05-15
> **MusicMastaMike said:**
> Just an update... I started having some serious lock-ups again.  It seems that there is an issue with the pidgin-musictracker plugin.  I purged my installation of this plugin (sudo apt-get purge pidgin-musictracker) and everything went back to normal!
thats the funniest thing is i had that installed too

---

### Post by dyous87 on 2008-05-15
speaking of lockups mine has been worse again actually. Virtualbox locks up a lot as well as gftp, pidgin and firefox. Nothing is worse then fspot however. I try importing my photos and the entire system all but crashes like less then a quarter way in and gives me an "out of memory" error message. How can importing photoes eat up two gigs of ram?

:confused:

---

### Post by money2themax on 2008-05-15
> **dyous87 said:**
> speaking of lockups mine has been worse again actually. Virtualbox locks up a lot as well as gftp, pidgin and firefox. Nothing is worse then fspot however. I try importing my photos and the entire system all but crashes like less then a quarter way in and gives me an "out of memory" error message. How can importing photoes eat up two gigs of ram?

:confused:
are your pictures are the size of the earth?:lolflag:

---

### Post by dyous87 on 2008-05-15
noo haha they are not. I really don't understand it.:((

---

### Post by money2themax on 2008-05-16
too bad cuz that would have explained your problem:lolflag:

---

### Post by dyous87 on 2008-05-16
> **money2themax said:**
> too bad cuz that would have explained your problem:lolflag:

haha yes it would, sigh i wish this would all be fixed

---

### Post by storm99999 on 2008-05-17
> **dyous87 said:**
> speaking of lockups mine has been worse again...

Do you have any more info on that?  I've run 1700 pictures through F-Spot, and it will choke for a few minutes, but it eventually breaks out of it.  Does the system seem to just drift to sleep when you're trying to work, slowing down input?  Any QT (KDE) based apps slowing down?

On another note, I haven't had any problems with the 2.6.25.2 kernel (although I should keep it updated if I went this far, .4's out...) in the last few days of use without grub hacks or hacking the scheduler. I think whatever was acting up got fixed at the core.

---

### Post by Xiong Chiamiov on 2008-05-17
On the original topic, I've been having pidgin lock up recently, due I think to the GTK updates (there were GTK updates, weren't there?)  I use KDE, so most of my apps are QT instead of GTK, so pidgin is really the only one that does that.

---

### Post by caue.rego on 2008-11-04
I'm with hardy 64, currently trying to upgrade ubuntu for first time to 8.10, and also with similar issues with Pidgin from a completly fresh install, and always updated system. Luckly, I have the Upgrade running right now which prevented me from trying that first suggestion of purging pidgin.

I did took a day or two tweaking few things, mostly with compiz, and I did checked few plugins in pidgin, but although the music one is in my mind it was not marked when I've checked. I don't even have such "musictracker" on my list of available plugins (which is weird, I could swear I've seem something like that and marked it eventually). The apt-cache pkgnames do show it, but I haven't purged it yet due to my Upgrade running and locking /var/lib/dpkg

So I've just tried disabling few plugins from pidgin (can't recall which ones), same place where I marked them, and so far it seems to be working fine with my current set of plugins (gtkbuddynote.so, cap.so, history.so, joinpart.so, markerline.so, notify.so and timestamp_format.so).

Although I'm still waiting for pidgin to actually connect to any network (oddly it is just hanging there for about 10 minutes now), **thanks** (so far) for your advices _MusicMastaMike_! At least it isn't hanging on my processor anymore. :)

And I'm running Rhythmbox!

edit: btw, how can I thank in a post if I can find no link for it?

---

### Post by iguanamind on 2008-11-05
All right I am having the same issue and I just installed fresh 8.10.  Locks up.  I have purged it and re installed per this thread.  Didn't do anything.  Not happening to any other applications.

---

### Post by ltkermit on 2008-11-10
> **MusicMastaMike said:**
> Just an update... I started having some serious lock-ups again.  It seems that there is an issue with the pidgin-musictracker plugin.  I purged my installation of this plugin (sudo apt-get purge pidgin-musictracker) and everything went back to normal!

I started having this issue after a recent Intrepid update, purging the musictracker plugin fixed my issue as well.

Thanks!!!

---

### Post by wintrmute on 2008-11-11
> **iguanamind said:**
> All right I am having the same issue and I just installed fresh 8.10.  Locks up.  I have purged it and re installed per this thread.  Didn't do anything.  Not happening to any other applications.

I recently upgraded from 8.04 to 8.10, and now Pidgin is freezing very frequently.

I've tried creating a whole new user on the box, and even on that account, it freezes up quickly!

Once pidgin dies, it needs to be kill -9 to get rid of it.. normal SIGTERM doesn't do anything.
I don't see anything in my dmesg or /var/log/messages that look relevant.

Any ideas?

---

### Post by wintrmute on 2008-11-11
I ran gdb (a debugger) over pidgon a bit.. It seems like the freezes were ocurring in the pulseaudio libraries.. I think it's a pthreads deadlock.

I tried disabling sounds in Pidgon (Preferences -> Sounds -> No Sound) and it seems to have improved things markedly.. No crashes so far!

It's worth noting that I don't have a soundcard in this machine..

---

### Post by iguanamind on 2008-11-11
That's interesting because the locking up has gone away.  I didn't notice that I had done anything to fix it.  But now that you mention it, my sound card wasn't working at all.  I had to compile the alsa driver manually and install it.  The sound card worked fine and I didn't notice this at the time, but that's also when Pidgin stopped locking up.  I also noticed yesterday when I had some problems with my soundcard driver failing for some reason that a few minutes later, my Pidgin instance locked up.  I thought, "Well it's time for a reboot."  Of course, the sound card came up and Pidgin didn't lock again all day.

This would all support the idea of a pthread deadlock in pulse audio.

---

### Post by wintrmute on 2008-11-11
Looks like it is this bug:

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/290914](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/290914)

Feel free to go over there and confirm you have the problem, report details, etc that might help. (And click the 'This problem affects me' box)

---

