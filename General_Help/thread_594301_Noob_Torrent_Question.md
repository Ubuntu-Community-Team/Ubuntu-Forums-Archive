---
title: "Noob Torrent Question"
date: 2007-10-27
forum: General Help
---

### Post by C00P88 on 2007-10-27
Hello all,

I just installed Azureus, hoping to download linux distros faster. I have it installed, and it stayed open long enough for me to set it up, but now it just closes. I try to re-open it, but it closes immediately. I also noticed that I'm getting connection attempts (I think) on port 27401, the default for Azureus. Is this normal? I deleted the rule in Firestarter so it will now block those connections. It shows it's blocking a connection every second, sometimes 2 connections per second. Is this normal? I have not yet tried to download a file yet, why would anyone try to connect to me? I checked the system menu, it does not show Azureus running in the background. I also tried re-installing Azureus with no change. It closes immediately. Any idea why it would be closing, and are the connection attempts normal?

---

### Post by Steveway on 2007-10-27
Why Azureus?
You should better use Deluge or Ktorrent.

---

### Post by YokohamaGaijin on 2007-10-27
What version are you running?  What Java VM do you have installed?

I had the same problem with 7.10 and Sun Java 5 & 6.  It would start and fail Java according to the log file.  I went with ktorrent and haven't regretted the change.  

:guitar:

---

### Post by ed-koala on 2007-10-27
I can't speak about the connections part, but I had a problem with Azureus opening closing too.  It's a known bug (or so I'm told) but there is a workaround - you need to delete the log files in the .azureus directories.

I just switched to Deluge instead of fooling with Azureus.  Uses less system resources and has all the functionality of Azureus.

Let us know how things go, these torrent questions are always of interest to me :)

---

### Post by C00P88 on 2007-10-27
Thanks for the quick replies!

I completely removed Azureus, yet Firestarter is lit up, I'm getting CONSTANT connection attempts on port 27401. Firestarter also closes after a while. I'm a bit concerned at this point.

As for Java, if I go to Applications, Internet, I have a Sun Java 6 option. Should I remove this?

I'm running Ubuntu 7.10.

Why Azureus? I don't know, a guy at work said it worked ok, it's my first attempt at any bittorrent program. It's no longer on my system now.

---

### Post by ed-koala on 2007-10-27
Hmmm, since you are getting connection attempts on the default Azureus port, I'm wondering if it isn't just leftover attempts to connect from others sharing the torrent.

Have you started any other torrent client yet?  And, how long has it been since you quit Azureus?  If it is leftover attempts due to Azureus, it should die down fairly quickly.

---

### Post by C00P88 on 2007-10-27
I currently am not running any torrents of any kind, and I stopped using Azureus 30-40 minutes ago. I'm still seeing connection attempts in Firestarter. If Firestarter closes, does that mean my firewall is off? It hasn't shut down in several minutes, so I guess that's an improvement.

---

### Post by ed-koala on 2007-10-27
Check Firestarter's event viewer, and see what ISP address(es) are trying for an incoming connection.

Then go to System - Administration - Network tools and use lookup to see who is trying to connect.  If it happens to be one particular ISP, you can see if it is perhaps your own service provider (that happened to me once, thought I had intruders in Windows and turned out to be harmless).

If you see it looks like break-in attempts, you can just block the port and use some other for your torrents.

---

### Post by C00P88 on 2007-10-27
I rebooted my PC, and power-cycled my router and modem. No more connection attempts. :)

It's still odd that Firestarter keeps closing. Is this some sort of bug?

There were several different addresses from what I remember, before the reboot/power cycle.  I don't currently have any to look up. I'm guessing something was left over from Azureus causing the problem? I think I'll try to figure out what's going on with Firestarter before I try another torrent program. Thanks for the help so far. :)

---

### Post by ed-koala on 2007-10-27
Ubuntu is very secure already, so a firewall isn't all that necessary ... I download torrents and I don't bother with one, or anti-virus.  One of the great reasons to use a Linux distro in my opinion.

If you want Firestarter, perhaps try removing and reinstalling, that might clear up things.

---

### Post by C00P88 on 2007-10-27
Ok, this might be a dumb question, but bear with me....

I just installed Deluge, and am trying to configure it (where to put files and stuff). Firestarter is showing attempted connections on a different port, for Deluge (actually says Bittorent). If I haven't yet downloaded any torrents, why would anyone try to connect to me?

---

### Post by ed-koala on 2007-10-28
The Deluge client should say Deluge in the title bar. If it doesn't, you probably have the Ubuntu default bittorrent client running.

The connections you see incoming might have something to do with the client testing your port to see if it's available/working.  Just guessing here tho.  If you actually started Deluge, did the old torrents from Azureus auto load into Deluge?  That also might be why you are getting connection attempts, tho unless the torrent actually tried to start I don't see why that would happen.

As I posted earlier, just trace back the ISP number trying to contact you and that should tell you what is going on.  If you need help doing that, post the isp trying to make contact and I'll see what it is.

---

### Post by C00P88 on 2007-10-28
Actually I just uninstalled Firestarter. It wouldn't stay open anyway.  I did get Deluge working tho. Unfortunately, it wasn't the result I was expecting. I was hoping I could download faster via a torrent, but it's actually faster for me to download regular files. The download started ok for Deluge, but after 15-20min, it went from 200-300 kBit/Byt (whatever it's called) to 1 or .5. If I download the traditional way, I can get 700-800 kiB if I just wait until 4am. (that was for a gutsy iso I was testing with, Free BSD never connected at all). Thanks for all the help tho. I DO appreciate it!

---

### Post by digger95 on 2007-10-28
A straight file download from a good mirror will almost always get you better results than a torrent download.  Torrents are great, I use Ktorrent all the time, but if you're lucky and get a well-seeded torrent it 'might' come close to using your full bandwidth, but not likely.  A good download manager on a straight download will get you your distros much faster.  Opinions may vary of course.

---

