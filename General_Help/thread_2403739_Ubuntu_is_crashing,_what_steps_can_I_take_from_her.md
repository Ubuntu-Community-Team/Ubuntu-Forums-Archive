---
title: "Ubuntu is crashing, what steps can I take from here? (detailed overview)"
date: 2018-10-15
forum: General Help
---

### Post by mikeubu2 on 2018-10-15
My Ubuntu install freezes about three times a day, sometimes requiring that I go through the process of checking the system partition with fsck to correct errors created by the improper shutdown.  I don't notice a pattern yet, I thought it might only be happening under high CPU loads but last night Ubuntu froze while it was in sleep mode so I'm not sure what the cause is.

Some additional information...


[LIST]
[*]I'm running the latest version of Ubuntu (18.04.1 LTS) 
[*]The System partition is encrypted 
[*]The System partition is on an external HD (USB 3.0, 80GB) and should have a healthy amount of free space. 
[/LIST]


To the best of my memory, here's some of what I've done since installing Ubuntu....

I did not install updates from the install disc because I had no internet when installing Ubuntu, I downloaded some afterwards though.  Initially I had trouble installing packages and dependencies, I tried **"sudo apt-get update && sudo apt-get upgrade" **because I was instructed to by customer service in order to get the dependencies needed for one of the programs I installed. If I remember right, this may have froze my computer but I'm not positive if this was the cause of the freezing problem, things seemed to get worse with time.  That command line didn't work to install the program I wanted and I had trouble installing other packages and programs as well.  This remained the case up until I typed the following line into the terminal... 

[B]"sudo rm /var/lib/apt/lists/*; sudo apt update"
[/B]
 I was told through the Ubuntu IRC channel that the line above would help.  In his own words he said I had the following problem...

                        > your "appstream" errors are due to corruption of the package lists - possibly related to on-disk corruption or possibly whilst over the network.



I'm able to install things easily now that I followed his instructions but I'm still not sure why I'm getting system crashes periodically or if the package list corruption had anything to do with it.

Since then, only a handful of programs have been installed because it's a new install of Ubuntu, here are some of those programs that I can think of offhand...

                          
[LIST]
[*][SIZE=3]**Synaptic **(package installer)

[/SIZE] 
[*][SIZE=3]**Private Internet Access, **(a VPN)

[/SIZE] 
[*][SIZE=3][B]VLC Media Player

[/B][/SIZE] 
[*][SIZE=3][B]Google Chrome

[/B][/SIZE] 
[*][SIZE=3]**Blade of Agony **(A 1st person shooter game)
[/SIZE] 
[/LIST]
  
I couldn't say which one of these, if any, is causing the system crash because they were all installed within a few hours of each other.

Lastly, here are some of the other dependencies I've installed (the ones that I can think of)...  

                            
[LIST]
[*]**"[SIZE=3]libavcodec-extra[/SIZE]"** and **"[SIZE=3]libavcodec-extra57[/SIZE] "** were installed for Youtube video support. 
[*]**&#8220;**[SIZE=3]**gconf2&#8221;** and **&#8220;libappindicator1**[/SIZE][SIZE=3]**"** [SIZE=2]were installed because Private Internet Access required them.[/SIZE][/SIZE] 
[/LIST]


Perhaps Ubuntu is still lacking something that would help it become more stable, I'm not sure.  That's all I can think of at the moment, if anyone has questions let me know and if there's a way to do an error report after a system crash I could provide that information as well, I'm still rather new to Linux.

[U]
[SIZE=4]**Questions...**[/SIZE][/U]



[LIST=1]
[*]Based on the layout of my system above is there anything specific I mentioned that could be causing a problem? 
[*]Is there an easy way to check for system problems or conflicts which could be causing the crashes? 
[*]If not, what are some general steps I can take to help make my OS less likely to crash, is there a program that I can install or something I can do in the terminal that would help increase the chances that my operating system is stable?  (The last question is important if we cant figure out the cause.) 
[/LIST]

I'm open to any suggestions or tips on this topic, thanks in advance for any help!

---

### Post by sp40140 on 2018-10-15
The hardware specs usually add clarity.
The starting point  is logs. You can find them in /var/log directory. Mark the time of crash and look for errors at the time in logs. Start with system log.
Now a guess: external (USB) drives usually have sleep mode to save energy and preserve the drive. If you install the os there, I'm not sure how that will work.
But that is just the first thing that popped in my head. 
Too many potential issues. So, check the logs. And post the relevant time logs here if you need clarification.

---

### Post by mikeubu2 on 2018-10-17
Thanks for the info, I see syslog and syslog 1, are these the files  you're talking about when you say system log?  It appears nothing has  been logged past October 8th in those files, with the last line  reading....

Oct  8 20:56:53 Linux colord[983]: failed to get session [pid 1942]: No data available

I'm  not sure if it's the right file though, I went to the right folder but don't see a system log file,  only one that's abbreviated sys, which I'm only guessing is the right one.  As  for the proper log files, whether it's this one or another file, when do  they record information, only when there's a problem to log, when a  boot occurs, or regularly throughout use of the OS?

[B]For some specs on my laptop....
[/B]

[LIST]
[*]AMD® A8-6410 apu (64-bit)
[*]amd radeon r5 graphics × 4
[*]6 to 8 Gigs of Ram if I remember right but the OS is only suggesting I have 4.8GB which is nonsense.
[*]An internal 750GB HD that I'm going to keep for my Windows OS
[/LIST]

As for having the OS on an external HD, I'm reading a lot about people who are doing it.  If the HD is going to sleep, I wonder if there'd be a way to turn that off.  A system crash hasn't happened today, knock on wood so I'm waiting for it at the moment to help diagnose the problem.

---

### Post by dragonfly41 on 2018-10-17
On occasions I have found these tools to be useful for 
analysing confusing logs ... in Ubuntu 16.04 ...

**petit**
[https://www.tecmint.com/petiti-log-analysis-tool-for-linux-sysadmins/](https://www.tecmint.com/petiti-log-analysis-tool-for-linux-sysadmins/)

and
[B]glogg
[/B][http://glogg.bonnefon.org/index.html](http://glogg.bonnefon.org/index.html)

---

### Post by mastablasta on 2018-10-17
> **mikeubu2 said:**
> 
[LIST]
[*]6 to 8 Gigs of Ram if I remember right but the OS is only suggesting I have 4.8GB which is nonsense.
[/LIST]

not if the ram stick is not working. you can verify and test the RAM with memtest or check available RAM with command

```
free -m
```

more here: [https://serverfault.com/questions/85470/meaning-of-the-buffers-cache-line-in-the-output-of-free?rq=1](https://serverfault.com/questions/85470/meaning-of-the-buffers-cache-line-in-the-output-of-free?rq=1)



> 
As for having the OS on an external HD, I'm reading a lot about people who are doing it.  If the HD is going to sleep, I wonder if there'd be a way to turn that off.

lot's of people take drugs too... doesn't mean we should as well. :p

in any case this was just a guess.

you can use the default logviewer to check the logs.

also what does crash mean? frozen picture? sound working? y/n? can you switch to console (cartl+alt+f1 though f7)? can you issue the [REISUB]("https://ubuntuforums.org/showthread.php?t=617349") ([https://ubuntuforums.org/showthread.php?t=617349](https://ubuntuforums.org/showthread.php?t=617349) ) command?

---

### Post by mikeubu2 on 2018-10-18
> **mastablasta said:**
> not if the ram stick is not working. you can verify and test the RAM with memtest or check available RAM with command

```
free -m
```

more here: [https://serverfault.com/questions/85470/meaning-of-the-buffers-cache-line-in-the-output-of-free?rq=1](https://serverfault.com/questions/85470/meaning-of-the-buffers-cache-line-in-the-output-of-free?rq=1)



Sorry for the delay, I'm traveling at the moment so my replies will be  spread out some.  Let me check what you're mentioning as I write this...

The free -m command is reading that I have a total of 4889 MB of RAM, then 975 for Swap.  I'm only guessing that the Swap adds to the total for a complete readout of recognized RAM, either that or the 975MB of Swap is part of the total, I'm not sure given it's listed separately.  Even if it is to be added to the total, that would only bring me to a total of 5864 MB which would still be under the amount that I have.  Not sure how I'd go about fixing that or confirming the true amount, I'm certain it's 6GB worth or more though.  I could boot into Windows later to see what it reads if there's no other way from Ubuntu.

> N
lot's of people take drugs too... doesn't mean we should as well. :p

in any case this was just a guess.

you can use the default logviewer to check the logs.

also what does crash mean? frozen picture? sound working? y/n? can you switch to console (cartl+alt+f1 though f7)? can you issue the [REISUB]("https://ubuntuforums.org/showthread.php?t=617349") ([https://ubuntuforums.org/showthread.php?t=617349](https://ubuntuforums.org/showthread.php?t=617349) ) command?

...

Crash means a complete crash, as in no activity or response to any mouse movements or  keyboard commands and strokes.  It slows down excessively first but I only have about a 20 second warning at the most to do anything, barely enough time to pull up the system monitor to check for a troublesome process if I'm lucky.   I'm not sure about the commands you're mentioning, I think I went to the console once just to test it out when the system wasn't crashing but I had no idea how to get out of the console so I ended up having to restart my computer, (I'm still new to Linux :-k).  

Let me check your link...

[SIZE=3]_Alt+SysRq_+R+S+E+I+U+B [SIZE=2]seems like a good option for an OS freeze, although I don't have a SysRq button on my keyboard.  I've read that the Print Screen button has replaced SysRq so I suppose it should work by using Print Screen instead, I'll test that out when I'm ready to restart my laptop again.

I opened the log viewer program and it seems more organized than the raw log documents, I'll remember to check that the next time the system crashes.  It's been a few days since it's  crashed so I'm not sure exactly what I'd be looking for.  I'm hoping the issue resolved itself but I'm not getting my hopes up too much on that, I have no idea what I'm doing different, if anything.

[/SIZE][/SIZE]

[SIZE=3][B]dragonfly41

[/B][SIZE=2]I'll have to take a look at those programs. Right now I'm just waiting for the OS to crash again so that I can pinpoint what lines in the log are associated with the crash.  Thankfully, it's been days now since it's occurred,

___________________

[SIZE=3]In the m[/SIZE][/SIZE][SIZE=3]****[/SIZE]eantime, does anyone have any general tips for stabilizing Ubuntu?  Are there any utilities I can use or command lines I can enter which would fix problems in the OS or look for software that's causing problems?[B] 
[/B][SIZE=2][/SIZE][SIZE=2][/SIZE][/SIZE]

---

### Post by mastablasta on 2018-10-19
you can also check the RAM size in BIOS or UEFI. 

are you maybe using a 32 bit version of the OS?

SysRQ is PrtScr key, though on laptop you may need to also press Fn to actually get the SysRq to register. it all depends on the keyboard setup.

slowdown and then freezing could be RAM or overheating of sorts. for exmaple when CPU or GPU get under load they heat up but don't cool of fast enough. when this happens on CPU the the system would usually shut off, but when it happens on GPU the system usually freezes. i would suggest that when you have time you install psensor and monitor the system temperatures: [https://wpitchoune.net/psensor/](https://wpitchoune.net/psensor/)

the app is using lm-sensors command line utility, and then displays it all in a much nicer way, so that us non-techies can actually read it. :)

---

