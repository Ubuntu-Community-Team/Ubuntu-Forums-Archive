---
title: "Mythtv backend server crashes!"
date: 2007-02-05
forum: General Help
---

### Post by ifross on 2007-02-05
A few weeks ago I installed a mythtv backend on a computer with 2 dvb cards in. It took a hell of a lot of time and finally everything was sorted and I installed the frontend on my desktop. Everything was working nicely as it should. Overnight I turn my desktop off in my room, the next day I tried to start the frontend and it didn't work.

Upon closer inspection, it was not just the mythtv backend that wasn't working, the whole computer had crashed (couldn't ssh to it) I did hard reboot and it loaded up and my fronend worked again.

This kept happening and only happened in the night so i thought that might be the problem, so I made a script to ping to it and output the result to a file (did so every 5 minutes) I left my desktop on overnight and when I came to it the next day the machine had not crashed!

The problem seems to be to do with my desktop connecting or disconnecting with the server, so I thought this may be something to do with nfs so I changed some settings but nothing helps... 

I literally have no idea what can be causing the crashes every time to the system, I tried looking in log files but I couldnt really tell whats going on,

The server crashes, without fail, if I leave it on overnight and turn off my desktop. Having to go up to the loft just to reset the computer everytime I want to use the program isnt very fun.

I created a script that ran overnight with cron that output the time every 5 mins to a file and what was weird was the fact that it didnt crash as soon as I turned off my desktop, it did 3 hours later at 3:45 in the morning.


I'd appreciate any help as Im at my wits end, I think the problem is mythtv based and if I look in the log file, the last line before crashing last night says :

[mpegts @ 0xb73cd500]Parser not found for Codec Id: 94212 !

I can't believe that a codec problem would cause a system crash but I'm not sure...

Any help would be much appreciated and I can provide any more information if you need/want it, I really want to fix this!

This is my first time asking the ubuntu community for help and Ive heard great things :)

---

### Post by majoridiot on 2007-02-05
interesting problem... if that is the last line in the mythbackend log, it could be possible that it
is choking when trying to transcode a recorded program.

two things i would start with, both are settings in mythtv-setup on the backend machine-

```
 sudo killall mythbackend
```

to stop the backend before changes. then-

```
mythtv-setup
```

1. make sure Idle timeout  is set to **0** (under General, then page thru to Sutdown/Wakeup 
Options) in case it is crashing when trying to shut down.  setting to 0 never shuts down on idle

2. **disable** "Allow transcoding jobs" (also in General, two pages after the previous setting)
to prevent it from transcoding your recordings.

once you make the changes-

```
mythbackend &
```

to bring the backend up again.

let it run unattended with the frontend off and no cron jobs like you were trying and see if it
survives the night intact.  if it does, we just need to tweak your transcoding codec settings
if you need to transcode your recordings to save space.

---

### Post by Ptero-4 on 2007-02-05
And if the transcoding is the culprit you may just ssh in to your mythtv PC from time to time and when it`s drive is near full run the transcoding.

---

### Post by ifross on 2007-02-06
Thanks for the reply, I've done what you suggested, but I think it is unlikely that its the cause because my desktop had the backend installed as a slave backend, I disabled all the CPU intensive jobs on the master backend (commflag, transcode) and did them on my desktop... Did'nt seem to help and I thought that the disconnecting and reconnecting of the slave backend may be messing with something so I uninstalled it.

I'll see what happens tonight.

Last night it crashed around twenty past 12. Nothing in the mythtv log at all around then... 

the last logs in the kern.log are:

 Feb  6 00:20:21 mythtv kernel: [17186950.672000] Inbound IN=eth0 OUT= MAC= SRC=192.168.0.101 DST=239.255.255.250 LEN=316 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=1900 DPT=1900 LEN=296 

(The server's IP is 192.168.0.101)
I just have no idea whats going on!!

---

### Post by wiz561 on 2007-02-06
Are you, by any chance, running the SVN version or the stable .20 one?  

If you still have problems and are coming up blank here, you might want to try posting to mythtv-users.  There's a ton of traffic over there and people are pretty knowledgable with things pertaining to myth.


Good Luck!

---

### Post by ifross on 2007-02-06
Im using .20 version...

Reading this:
[http://www.ubuntuforums.org/showthread.php?t=310824&highlight=mythtv](http://www.ubuntuforums.org/showthread.php?t=310824&highlight=mythtv)

seems that a few people are having similar problems but no-one really knows the cause of the freezes. Ill try some of the stuff they mention (I've already tried 3 filesystems with no success...)

---

