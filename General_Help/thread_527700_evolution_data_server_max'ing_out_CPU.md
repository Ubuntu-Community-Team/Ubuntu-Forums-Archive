---
title: "evolution data server max'ing out CPU"
date: 2007-08-16
forum: General Help
---

### Post by maddentim on 2007-08-16
I have ubuntu 7.04 and use Evolution for email and calendar.  For the last day, the process "evolution-data-server-1.10" has been max'ing out the CPU and I have not been able to get it under control.  I have, from the terminal, tried to restart the program by 
```
$ evolution --shutdown-force
```

to no avail.  When I restart evolution, the data server just goes back to consuming all the CPU.

I am thinking that something must be corrupt, but do not know how to recover.

Any suggestions??

Thanks!

---

### Post by maddentim on 2007-08-17
I have resolved this issue on my own.  I had some webcals set up.  I deleted them and the evolution-data-server returned to normal.  weird.

---

### Post by Ginger The Cat on 2008-04-24
I've added this here as it looks like it might be related

I have been having problems with my laptop overheating. Because of this I have had gkrellm running and displaying the temperature and other data.

While using my laptop today I heard the fan kick in and when I checked the temperature it was at 51C with processor usage at 100%
I just had Firefox and Thunderbird open. I closed them both and processing remained at 100%.
I opened System Monitor and it showed Evolution-data-server in the high 90s% for processor with Status sleeping.

I did "Stop process" on it and processing dropped immediately to almost nothing and temperature to a normal 31C.

I realise that 51C isn't particularly hot and that I shouldn't go round ending processes when I don't know what I'm doing but...

Can anyone tell me what evolution-data-server is and why it would be using so much of my processor when I don't use Evolution.
Also why was processing at near 100% when its status was "Sleeping"

I'm using Hardy Heron. 

Cheers

Mike

---

### Post by elucidblue on 2008-04-25
I'm having the same problem, both on my home and work machines, each running Hardy.  Killing the process takes care of the problem, but obviously that's only a temporary fix.

---

### Post by CarloMagno on 2008-04-26
I had the same problem just after upgrading to Hardy. I launched Evolution and followed the configuration process and voilà the CPU usage dropped instantaneously. But that didn't solve my problems of poor scrolling in firefox and nautilus..

---

### Post by justmenodupes on 2008-04-26
same problem here...

never used evolution, but was going to try it and see how does it's calendar was :(

I just configured my gmail account (IMAP)... nothing more :(

---

### Post by CarloMagno on 2008-04-27
> I had the same problem just after upgrading to Hardy. I launched Evolution and followed the configuration process and voilà the CPU usage dropped instantaneously. But that didn't solve my problems of poor scrolling in firefox and nautilus..

My mistake, after a couple of reboots in the server the problem is back, so the posted procedure doesn't work. I have to manually stop the process in the system monitor to avoid it consuming 100 % of one of the CPUs. (AMD 64 X2BE-2400 on Gigabyte 690g). The scrolling and lagging problems I suffer are caused by the graphic card (Ati Radeon HD3870) and the proprietary ati driver that was not properly configured when I upgraded from Gutsy to Hardy (Mesa glx instead of ati). Now I am temporary working with "ati" driver and it works OK (no 3D accel, some video playback problems and not full 1080p but good scrolling and performance).

I am using 64bit version of Ubuntu, I will try the 32bit version in a fresh install (on a spare-test partition I have set) to see if those problems are reproduced.

---

### Post by skelemen on 2008-04-27
This is a known bug, unfortunately not fixed yet:

[https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/151536]("https://bugs.launchpad.net/ubuntu/+source/evolution-data-server/+bug/151536")

---

### Post by _Stevie_ on 2008-04-27
hmm configuring it did resolve my problem thought.

---

### Post by blackest_knight on 2008-04-27
> **_Stevie_ said:**
> hmm configuring it did resolve my problem thought.

Interesting I found my EEE was being unresponsive and locking up and evolution-data was eating all the cpu. I tried killing the process which at least made it responsive. 
I deleted .evolution in my home directory and i still got high cpu usage on reboot. so i started configuring evolution only pressed forward once in the dialog before accidently closing it. 

however it isnt an issue now both from cold and a warm boot evolution-data is not running anymore.

---

### Post by nynoah on 2008-04-27
I am having problems with mine too.  Only solution so far was to kill it in my system tray.  Anyone have a clue why evolution is doing this?

---

### Post by _Stevie_ on 2008-04-27
interessting:

The data server, called "Evolution Data Server" is responsible for managing
mail, calendar, addressbook, tasks and memo information.

---

### Post by octopuskevin on 2008-04-28
same problems here. I thought my computer was indexing [the fan was at full] but system-monitor showed evolution eating a whole core's cpu. temp spiked up to almost 80*.

the bug has it listed as high, but there doesn't seem to be a 'solution' yet. I guess till than just keep killing the process if it goes out of hand

---

### Post by LoSt180 on 2008-04-28
same problem here. every start up I have to open System Monitor and stop the process evolution-data-server-2.22 My laptop is a turd and can't handle 100% CPU for very long. The fan is full blast and it will shut itself down after a few minutes. I don't use evolution and don't intend to either.. 

I'm using an Acer laptop, with an AMD Sempron 3000 CPU if that helps anything.

This only started after I did a fresh install of Hardy Heron, I didn't have this problem in Gutsy, or Feisty before that.

---

### Post by justmenodupes on 2008-04-29
trying to remove "evolution-data-server" want to remove also ekiga (I switched to Sunbird :D ) :(

---

### Post by parkland on 2008-04-30
Same problem here, only it maxes out 1 of the cpu's. 


I never use it either.

---

### Post by likwid on 2008-05-01
Do any of you have kubuntu-desktop installed? 

I found that immediately after installing kubuntu desktop this problem occurred, having removed kubuntu desktop it went away.

---

### Post by TokyoYank on 2008-05-03
same problem, but only on the last reboot.  Happened immediately upon logging in.  Evolution was open when I logged out previously, so maybe it was trying to reset something.  (However, it is not in my saved session info.)

Instead of killing evolution-data-server, I found different & very easy work around:  simply start Evolution and then close it.  The job, CPU, and fan noise went away... even after you open it again.

---

### Post by TokyoYank on 2008-05-05
> **maddentim said:**
>   I have, from the terminal, tried to restart the program by 
```
$ evolution --shutdown-force
```

to no avail.  When I restart evolution, the data server just goes back to consuming all the CPU.

OK, it happened again, but not at login.  Just started happening while I was working.  starting the mail Evolution GUI and shutting it down didn't change anything.  However, the --shutdown-force option *did* work.  Running Hardy from a fresh install, fully updated.

---

### Post by Jonathan Métillon on 2008-05-06
> **LoSt180 said:**
> same problem here. every start up I have to open System Monitor and stop the process evolution-data-server-2.22 My laptop is a turd and can't handle 100% CPU for very long. The fan is full blast and it will shut itself down after a few minutes. I don't use evolution and don't intend to either.. 

I'm using an Acer laptop, with an AMD Sempron 3000 CPU if that helps anything.

This only started after I did a fresh install of Hardy Heron, I didn't have this problem in Gutsy, or Feisty before that.

 Hi, same issue here. I just upgraded to Ubuntu 8.04 Hardy Heron. I have the *evolution-data-server-2.22* process that is eating max CPU. I don't use evolution, never started it, and don't plan to (I use GMail webmail).  > **justmenodupes said:**
> trying to remove &quot;evolution-data-server&quot; want to remove also ekiga (I switched to Sunbird :D ) :(

 So, is this safe to remove Evolution? Doesn't Ubuntu heavily rely on the Evolution package?  Thank you.

---

### Post by TokyoYank on 2008-05-07
> **Jonathan Métillon said:**
> So, is this safe to remove Evolution? Doesn't Ubuntu heavily rely on the Evolution package?  Thank you.

Looks like you can remove it easily in Synaptic, if you want to try it temporarily:

[http://ubuntuforums.org/showthread.php?t=733041](http://ubuntuforums.org/showthread.php?t=733041)

But it's not clear to me if programs will stop working.  Since ubuntu-desktop is a meta-package that can be ignored (except when upgrading), applications that share Evolution's database should still work--but, of course, not have the features related to sharing data.  (For example GAIM would work but rely solely on the external server for  contact info; or the GNOME clock applet would show a pop-down calendar, but nothing would happen when you click on a specific date.)

I'm currently giving Evolution a try as my mail reader.  (Though, I think I prefer Thunderbird)  If I remove it, will I loose my external account settings?  ..  If anyone reading removes Evolution, I'm interested to hear how it affects other GNOME applications.



On a related note, in searching the above link I found a plugin that might be useful for connecting GNOME clock with Google Calendar:
[http://altinkaya.org/wp/linux/google-calendar-gnome/](http://altinkaya.org/wp/linux/google-calendar-gnome/)

That kind of plugin functionality is useful, though I'm confused as to why it requires all packages of Evolution.  Does anyone know a stand-alone, non-Evolution (or at least, partial-Evolution) way to give the same effect?  Can anyone out there on the Evolution development team shed light on why these kinds of functionalities haven't been modularized?

---

### Post by Marky-Mark47 on 2008-05-07
> **CarloMagno said:**
> My mistake, after a couple of reboots in the server the problem is back, so the posted procedure doesn't work. I have to manually stop the process in the system monitor to avoid it consuming 100 % of one of the CPUs. (AMD 64 X2BE-2400 on Gigabyte 690g). The scrolling and lagging problems I suffer are caused by the graphic card (Ati Radeon HD3870) and the proprietary ati driver that was not properly configured when I upgraded from Gutsy to Hardy (Mesa glx instead of ati). Now I am temporary working with "ati" driver and it works OK (no 3D accel, some video playback problems and not full 1080p but good scrolling and performance).

I am using 64bit version of Ubuntu, I will try the 32bit version in a fresh install (on a spare-test partition I have set) to see if those problems are reproduced.

To resolve this problem, end the Evolution data server 2.22 process using System Monitor, then go to System -> Preferences -> Sessions, click the Session Options button, then click the Remember Currently-Running Applications button, and this will prevent Evolution data server 2.22 starting up at boot.  If you want to start each session with a clean desktop, it might be a good idea to close your other apps before hitting the Remember Currently-Running Applications button.

---

