---
title: "Random Freezes, need help debugging"
date: 2006-12-01
forum: General Help
---

### Post by AusIV4 on 2006-12-01
Hi, I wrote a while back about some problems I was having. For a while I thought I had them resolved, but now I'm running into the same problem again.

Before Edgy was released, I had an incredibly stable Dapper system, on which I ran MythTV, and I used it for web browsing and listening to music with Amarok. When Edgy was released, I tried upgrading. Long story short, that failed miserably and I've decided to stick with Dapper.

Now my system functions, but it will randomly freeze, and I have no idea why. The only differences between my current setup and my old setup are: a) I replaced a hard drive (in a RAID 5 array), b) I installed MythTV from superm1's repository rather than from source, c) I installed lirc from Ubuntu's packages instead of from source.

From what I've read, it sounds like this is probably a hardware or driver issue. I don't think it's lirc, because I don't load the modules on boot, and I've had it crash while the modules were not loaded. I doubt it's my new hard drive, because it's in a RAID array, and RAID drivers are pretty solid. MythTV doesn't run at a kernel level, so I doubt that's the issue.

I've tried running a Konsole with the top line of top (the terminal program) visible at all times so that I could see what program was causing the hiccup, but it always seems to crash when I've neglected to keep top visible.

I've also tried running a Memtest. I ran it over night (9+ hours) and it did not find a single problem, so I don't think that's my problem.

When I'm around, the freezes aren't a big deal - I just hit the power button and reboot. The problem is that when I go out of town for more than a day or two, my computer inevitably freezes up and my shows don't get recorded.

My system logs give me nothing to go on. Often, the last log entry in /var/logs/syslog is from as much as 5 minutes before the crash. If anyone could give me a way of forcing top to stay in the foreground without being too obtrusive, or something else I could see after the system crash, I'd really appreciate the help.

---

### Post by Tyltyl on 2006-12-02
I had this issues for months now and I still haven't found a fix. 
It has been discussed in many threads (just search for "freeze") and some people have solved in different ways, by removing graphic card drivers, disabling wifi etc.
Just try, I don't know what else to suggest since I think the same problem has many causes :(

---

### Post by AusIV4 on 2006-12-03
Ok, I finally got Dapper installed on my laptop, so I was running top via an SSH connection during a crash. I've attached a printout of top from the crash. As far as I can tell, there's nothing of any significance there.

> It has been discussed in many threads (just search for "freeze") and some people have solved in different ways, by removing graphic card drivers, disabling wifi etc.

I've removed my wifi card, because I thought for a while that was my problem. I've heard of people having problems with ATI graphics cards, but mine is an old Savage card that is supposed to be fairly well supported.

I've scanned the forums for causes of these problems, and I haven't found much at all that looks like it could be related to my freezes. The most irritating thing is  (aside from the crashing) that I didn't have these problems until I reinstalled, and I'm not aware of any significant changes that have been made between setups.

[EDIT]
I did notice that my last two crashes have had a lengthy error that starts with 
```

Dec  3 20:00:04 AusIVServer kernel: [17359100.292000] Unable to handle kernel paging request at virtual address 4b434854

```

This is followed by a list of loaded modules and a bunch of register addresses and a stack trace. I've not been able to find any information on what the above error message means, but it doesn't sound good. Does anyone know what it means?

[EDIT2]
Looking further into the Call Trace, it looks like the problem may have stemmed from kjournald, which from what I understand is something the Kernel uses for handling journaling file systems.

That's when it hit me. There was relatively big difference between my current setup and my old one. In my old setup, I used JFS as the file system for my RAID volumes, and ReiserFS for the root file system and this time I used ext3 for both. All three are journaled file systems, but I have to wonder if there might be some problem with ext3 that could be causing my crashes.

Any thoughts?

---

### Post by superm1 on 2006-12-03
I can relate very similar issues with ext3.  Particularly, the issues cropped up when deleting recordings while recording at the same time.  I resolved the issue for myself by choosing XFS for the recordings partition instead.

---

### Post by AusIV4 on 2006-12-04
I used JFS for my filesystem last time, and it lead to a major data loss when I couldn't reduce my partition when I wanted to change my LVM, so while I've learned some lessons from that experience, I'm still hesitant to use any file system I can't reduce. However if ext3 is in fact the cause of my crashes, it may be worth the risk (plus, now that I'm on RAID, I don't see reducing my partitions any time soon).

If I do decide to switch my array to JFS or XFS, I'll need to figure out how exactly I'm going to juggle 139.6 GB of data around my drives and have it all come out in order once it's rebuilt.

I think it's doable, the question is, am I sure that's my problem?

---

### Post by superm1 on 2006-12-04
Well here is what I say you do.  Rather then juggle the data around right this minute - get another hard drive temporarily.  Pull out all of this raid array for the moment being.  Set up myth to use this other drive to do your recordings, and set it up as XFS or JFS.  Give it a few days (or however frequent your crashes are) and then go from there. 

If you don't have a spare drive sitting around or some buddies that will be willing to lend you one, your local big box retailer will probably have some extended return options.  I know at least by me, Best Buy won't charge a restocking fee if I was to buy a hard drive today, use it for a week or two and then return it.  They see it as I wasn't happy with the product and I get my money back.  You see it as a way to test out a piece of your setup :)

---

### Post by AusIV4 on 2006-12-04
I don't have extra drives, but right now my logical volume is large enough that I could reduce it and run on the remainder for a while.

Thanks for saving me the trouble. (And thanks for the MythTV repositories, they saved me a couple hours of installation).

[EDIT]
I've created a smaller logical volume and I'm running jfs. I'm going out of town this weekend. If my computer makes it until I get back, I'll assume ext3 was the problem and switch to jfs. If I continue to have problems, I'll assume ext3 was not the problem, and put my volumes back to the way they were. Even though the data juggling will be uh... interesting, I'm hoping that was the problem so I can be done with this whole ordeal.

---

### Post by AusIV4 on 2006-12-05
Things just got weird.

I finished watching a TV show and I was about to go to bed, but when I tried to shut down mythfrontend, my system froze. But this time wasn't the same. Ctrl-alt-backspace didn't work, but I could ssh into my box, access the apache server, etc. My old symptom was a complete freeze, none of that would have worked.

When I SSHed in, I tried top, and it showed incredibly low cpu and memory usage. Then I tried 'ls' - my ssh terminal stopped responding. I closed that and tried again. I changed to the / folder. ls worked fine. Thinking it was probably a problem with my /home/ file system, I changed into /home/ and tried ls. It worked too. I changed to my mythtv user's folder. ls worked there too. The only place ls didn't work was my home directory (I didn't think to try subfolders within my home directory). Oddly, I share my home directory via NFS with my laptop, and I could access it fine from there.

I tried sudo /etc/init.d/kdm restart, and that froze my terminal.

Finally, out of other ideas, I did a sudo reboot (a more proper reboot than was possible with my old problmes), and everything booted fine.

Any ideas why this would have happened? It certainly didn't look like it was the same problem I've been having in the past, and it's the first time it's happened, so it may be a one time deal. Even so, it's reset my uptime (by about 4 hours, no biggie), and raises other concerns.

---

### Post by superm1 on 2006-12-05
Well this is quite the odd freeze.  Did /var/log/Xorg.0.log bring any justice in explaining this at all?  Or /var/log/messages?  I've encountered similar things where it was caused by an important network share going down, even if i'm not active in that directory.  Do you have any other network shares mounted right on that box?

---

### Post by AusIV4 on 2006-12-05
I did have my laptop's network share mounted in that directory, but I was using my laptop to SSH in. Does it cause problems to mount a network file system from a box that isn't up all the time? (And I didn't see anything in log files that I thought were worth mentioning).

---

### Post by superm1 on 2006-12-05
It can cause problems if they are actually mounted, and not just ssh:// links in nautilus.  I don't want to say it was necessarily the cause of your problem, because usually the computer will recover from things like that after a minute or two, unless you mounted using a "hard" option.

---

### Post by dgtester on 2006-12-05
My box froze constantly with Edgy (not on Dapper), and I tracked the problem down to powernowd. I just added the Dapper repositories into synaptic and then downgraded to the dapper version of powernowd and everything was fine.

---

### Post by AusIV4 on 2006-12-06
I'm approaching 2 days uptime. That's not quite long enough to jump for joy over, but it's certainly encouraging - usually I'm lucky to get upwards of 30 hours.

I leave town tomorrow and I'll be away from my box until Sunday. Annoying thing is, my campus network has a tendency to kick off boxes and you have to manually log back in. If that happens over the weekend, I won't be able to tell whether my box is still up or not. If it's still up when I get back Sunday, I'll start migrating the rest of my files over to the jfs file system.

[EDIT]
I just started trying to watch a TV show from MythTV, and the quality was just bizarre. There were green and blue splotches all over the screen, particularly where movement was occurring. I tried watching old recordings (ones I've watched before), and they had the same splotches. I reinstalled some mythtv components, and all of my old recordings seem to be fine, but the one I was recording when I noticed the problem is still weird.

I'm guessing this is unrelated to my crash issues, but the timing seems strange.

---

### Post by superm1 on 2006-12-06
30 hours uptime for a myth box being something to jump for joy..... i remember those days when i had a box with some flaky hardware.  

I can proudly post this though now:
```
mythtv@mythdell:~$ uptime
 22:58:21 up 81 days, 48 min,  1 user,  load average: 0.11, 0.12, 0.10

```

Depending on whether these color splotches are happening during regular machine usage too, u have a fun issue on your hand :)

I'll cross my fingers for your box this weekend.

---

### Post by AusIV4 on 2006-12-07
Well crap. Since the mythtv user already existed, reinstalling some of the mythtv components wasn't allowing proper configuration. After that, I started getting segfaults with mythfrontend and backend. By deleting the mythtv user I was able to get mythtv-common to configure, but backend was still segfaulting. Fed up, I decided to reboot my computer, as that usually resolves my segfaults.

```

austin@AusIVServer:~$ uptime
 23:54:37 up 9 min,  1 user,  load average: 0.40, 0.32, 0.19

```

So I'm back to counting the hours again, but I'm still feeling fairly confident that I've found my *main* problem. I may have some other stuff to troubleshoot later, but I'm thinking I'll be able to get sufficient uptime.

[EDIT]
As I expected, my school's network booted off my computer, so at this point I have no idea whether or not my computer is running.

---

### Post by AusIV4 on 2006-12-10
I got back to my computer a few minutes ago, and it was on the login screen, just as I had left it. Just to be sure everything was alright, I tried uptime:
```

austin@AusIVServer:~$ uptime
 13:41:00 up  2:14,  2 users,  load average: 0.65, 0.78, 0.40

```
So apparently it rebooted 2 hours ago.

I have all of my TV shows from mythtv, though, which implies that the computer was still operating prior to the reboot. I think this problem is unrelated, and when I have more time, I'll search through the logs for the cause of the crash. Depending on what I find, I'll probably go ahead and migrate everything else over to jfs.

I can deal with a computer that reboots periodically, so long as it's only down for a couple of minutes during the reboot phase. What I don't want to put up with is a computer that I have to manually restart every couple of days.

---

### Post by superm1 on 2006-12-10
Well glad to hear that these don't seem to be myth related, i guess :)

Good luck debugging your random freezes.  Something to try, is to bump down the agp speed on your graphics card, or try to turn down the memory speed in your bios if its supported.

---

### Post by mysticmarks on 2007-01-15
This is popping up everywhere. I would not change any hardware. It is occuring accross the board. I want to finger nautilus, but there just isnt enough information as most of us cannot preform proper tracing of the issue.(its a freeze!) This shows in threads on all video chipsets, plugins, browsers, etc. I have found the crash can be forced be very fast scrolling in various applications. I myself have tried all fixes and workarounds suggested based on my system hardware and am pretty sure this is related to an underlying issue that encompasses all of this.

---

### Post by ordou on 2007-01-22
Hi. I'm new to Ubuntu/Linux and I'm experiencing similar issues with my server (Dapper 6.06.1). I also could use some help.

My server's is an 
[LIST]
[*]Athlon 1333 MHz
[*]768MB memory
[*]Ati Radeon 9200
[*]Hauppauge PVR-150
[*]CNet Gbit network card
[*]Two SiI 3114 SATA controllers with lots of disks:
[LIST]
[*]/boot using ext2
[*]/root using Reiserfs
[*]/multimedia using XFS
[/LIST]
[/LIST]
The server usually runs mythbackend at boot and doesn't have X installed. Since I installed Dapper I've had random freeze/ hangs, and only a reboot/ shutdown will correct the problem. So recently, I've disabled mythbackend to see if that was the cause of the freeze, however I still get the random hangs.

/var/log/syslog doesn't show anything (I think), here's a snip of the syslog around the time of my lock-up earlier tonight:
```

Jan 22 12:27:32 mordor -- MARK --
[COLOR="Red"]Jan 22 12:47:32 mordor -- MARK --
Jan 22 19:00:18 mordor syslogd 1.4.1#17ubuntu7: restart.
[/COLOR]Jan 22 19:00:19 mordor kernel: Inspecting /boot/System.map-2.6.15-27-386
Jan 22 19:00:19 mordor kernel: Loaded 23031 symbols from /boot/System.map-2.6.15-27-386.
Jan 22 19:00:19 mordor kernel: Symbols match kernel version 2.6.15.
Jan 22 19:00:19 mordor kernel: No module symbols loaded - kernel modules not enabled. 
Jan 22 19:00:19 mordor kernel: [17179569.184000] Linux version 2.6.15-27-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006
```

I could really need some help in hunting this problem down. Thanks!

---

### Post by jondkent on 2007-01-24
I'm the same as a lot of people with 6.10 I also get random freezes.  I think it might be down to my video card, but from reading the comments on this it doesn't look like it.

The freezes are not consistent, but do look like its more a GNOME issue that anything else.  Still digging though so let you guys know if I come up with anything.

Jon

---

### Post by Nikron on 2007-01-24
I get random freezes, only mouse works, but only if I'm doing something graphic related...  IE I've never freezed while typing, but using firefox/nautilus will freeze my computer.

---

### Post by ordou on 2007-01-25
I haven't got Gnome or KDE installed on my server, and I'm only using shell via ssh. So if the issues are related, it's something other than that. (?)

---

### Post by ickyb0d on 2007-02-06
Unfortunately I also get random frontend freezes, but the backend never seems to crash.  I'm relatively new to MythTV (about 2-3 days in now) so I followed the [Backend/Frontend/Desktop howto in the wiki]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop") which seemed to go relatively smoothly.

I'm currently running
[LIST]
[*]MythTV 0.20
[*]Ubuntu 6.10
[*]PVR-500 Capture Card with IVTV Drivers
[/LIST]

Anyways, i'm going to try messing with stuff tonight and see what i can get.  Mine seems to only freeze on live TV and shortly after accessing the guide; although i guess i haven't really had a chance to play with too much else.  I just had one quick question though...

since only the frontend is crashing, where are some good places to look for errors? I've done "frontend -v all" in a terminal and i always seem to get something along the lines of "audio buffering" or something to that effect and then it freezes.  I could give the exact error message later (when i'm at the computer) but thanks for all the suggestions in this thread so far!

---

### Post by superm1 on 2007-02-06
> **ickyb0d said:**
> Unfortunately I also get random frontend freezes, but the backend never seems to crash.  I'm relatively new to MythTV (about 2-3 days in now) so I followed the [Backend/Frontend/Desktop howto in the wiki]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop") which seemed to go relatively smoothly.

I'm currently running[LIST]
[*]MythTV 0.20
[*]Ubuntu 6.10
[*]PVR-500 Capture Card with IVTV Drivers[/LIST]
Anyways, i'm going to try messing with stuff tonight and see what i can get.  Mine seems to only freeze on live TV and shortly after accessing the guide; although i guess i haven't really had a chance to play with too much else.  I just had one quick question though...

since only the frontend is crashing, where are some good places to look for errors? I've done "frontend -v all" in a terminal and i always seem to get something along the lines of "audio buffering" or something to that effect and then it freezes.  I could give the exact error message later (when i'm at the computer) but thanks for all the suggestions in this thread so far!

A few good places to start look for errors:
> /var/log/Xorg.*
/var/log/messages
dmesg


You can try bumping down the AGP speed if your AGP graphics card, and also try bumping down memory speed.

---

### Post by ^rooker on 2007-02-06
I've also experienced such random lockups as you're describing. In my case it was the ATI graphics card of a ThinkPad notebook.

2 things you could try to rule out graphic-card problems:

1) Use vesa driver instead of savage (change in /etc/X11/xorg.conf).
2) Turn the color depth down to 16bit (instead of 32 or 24).

Try using your system with these changes and see if the lockups appear again. If they don't you might look for better solutions than vesa/16bit for your graphics device.

---

### Post by ickyb0d on 2007-02-07
for starters...  thanks for the quick response superm1!

> **superm1 said:**
> You can try bumping down the AGP speed if your AGP graphics card, and also try bumping down memory speed.

I guess... first off, i'm just using the onboard video which looks to be...

```
ickyb0d@mediab0x ~$ lspci -v |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04) (prog-if 00 [VGA])

```

I'm not sure, but i also recently changed my tuner inputs (as i have the PVR-500) in mythtv-setup from tuner1/tuner2 to tuner1/svideo2.  I don't know if that would start forcing the guide to crash on me... but it seems to crash every time i load up the guide now during live tv.  I also changed my Xorg.conf to output in the 60Hz range, as the TV i have it hooked up to doesn't support anything else.  You can see an the error and my debugging attempts below... but i did notice that a 0.20a came out recently with some pointer fix.  But i thought that was only for mythweb.  Anyways the output from mythfrontend made me think of that... as it mentions a pointer.  in the first line you can see the "waiting for audio" i was talking about.  

all in all..  I did a tail -f on /var/log/Xorg.log as well as var/log/messages and looked at dmesg.  Nothing changed in the time i went into mythtv and loaded up the guide (which crashed the frontend).   below is the last output from mythfrontend -v all.  The line before this was just an SQL statement.. i assume querying the guide table.

again... any help would be appreciated, but if i figure this out, i'll let you guys know.  thanks again!

```

2007-02-06 23:34:19.472 AO: audio waiting for space on soundcard: have 3296 need 4096
2007-02-06 23:34:19.473 NVP: A/V Divergence: -0.798477, Rate: 0.246209, Warpfactor: 0.981025, warpfactor_avg: 0.999909
*** glibc detected *** mythfrontend: free(): invalid pointer: 0xa9422680 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb5bbd8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb5bbda44]
/usr/lib/libmythavutil-0.20.so.0(av_free+0x16)[0xb72e9162]
/usr/lib/libmythavcodec-0.20.so.0(img_resample_close+0x15)[0xb708ecf0]
/usr/lib/libmythtv-0.20.so.0(_ZN13VideoOutputXv15PrepareFrameMemEP11VideoFrame_13FrameScanType+0x84e)[0xb7ac9ebe]
/usr/lib/libmythtv-0.20.so.0(_ZN13VideoOutputXv12PrepareFrameEP11VideoFrame_13FrameScanType+0x270)[0xb7aca376]
/usr/lib/libmythtv-0.20.so.0(_ZN17NuppelVideoPlayer6AVSyncEv+0xc7f)[0xb79e2281]
/usr/lib/libmythtv-0.20.so.0(_ZN17NuppelVideoPlayer18DisplayNormalFrameEv+0x787)[0xb79e5379]
/usr/lib/libmythtv-0.20.so.0(_ZN17NuppelVideoPlayer15OutputVideoLoopEv+0x878)[0xb79e7db0]
/usr/lib/libmythtv-0.20.so.0(_ZN17NuppelVideoPlayer22kickoffOutputVideoLoopEPv+0x42)[0xb79e7ee2]
/lib/tls/i686/cmov/libpthread.so.0[0xb5da0504]
/lib/tls/i686/cmov/libc.so.6(__clone+0x5e)[0xb5c2451e]
======= Memory map: ========
08048000-08186000 r-xp 00000000 08:02 732787     /usr/bin/mythfrontend
08186000-08188000 rw-p 0013e000 08:02 732787     /usr/bin/mythfrontend
08188000-0844c000 rw-p 08188000 00:00 0          [heap]
a88de000-a88df000 ---p a88de000 00:00 0 
a88df000-a90df000 rwxp a88df000 00:00 0 
a9200000-a928e000 rw-p a9200000 00:00 0 
a928e000-a9300000 ---p a928e000 00:00 0 
a9400000-a9429000 rw-p a9400000 00:00 0 
a9429000-a9500000 ---p a9429000 00:00 0 
a9587000-a9588000 ---p a9587000 00:00 0 
a9588000-a9d88000 rwxp a9588000 00:00 0 
a9d88000-a9e00000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
a9e00000-a9f00000 rw-p a9e00000 00:00 0 
a9f40000-a9fb8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
a9fb8000-aa030000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa030000-aa0a8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa0a8000-aa120000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa120000-aa198000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa198000-aa210000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa210000-aa288000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa288000-aa300000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa300000-aa400000 rw-p aa300000 00:00 0 
aa430000-aa4a8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa4a8000-aa520000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa520000-aa598000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa598000-aa610000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa610000-aa688000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa688000-aa700000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa700000-aa800000 rw-p aa700000 00:00 0 
aa840000-aa8b8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa8b8000-aa930000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa930000-aa9a8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa9a8000-aaa20000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aaa20000-aaa98000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aaa98000-aab10000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aab10000-aab88000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aab88000-aac00000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSAborted (core dumped)
ickyb0d@mediab0x ~$ 

```

---

### Post by superm1 on 2007-02-08
> **ickyb0d said:**
> for starters...  thanks for the quick response superm1!



I guess... first off, i'm just using the onboard video which looks to be...

```
ickyb0d@mediab0x ~$ lspci -v |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04) (prog-if 00 [VGA])

```I'm not sure, but i also recently changed my tuner inputs (as i have the PVR-500) in mythtv-setup from tuner1/tuner2 to tuner1/svideo2.  I don't know if that would start forcing the guide to crash on me... but it seems to crash every time i load up the guide now during live tv.  I also changed my Xorg.conf to output in the 60Hz range, as the TV i have it hooked up to doesn't support anything else.  You can see an the error and my debugging attempts below... but i did notice that a 0.20a came out recently with some pointer fix.  But i thought that was only for mythweb.  Anyways the output from mythfrontend made me think of that... as it mentions a pointer.  in the first line you can see the "waiting for audio" i was talking about.  

all in all..  I did a tail -f on /var/log/Xorg.log as well as var/log/messages and looked at dmesg.  Nothing changed in the time i went into mythtv and loaded up the guide (which crashed the frontend).   below is the last output from mythfrontend -v all.  The line before this was just an SQL statement.. i assume querying the guide table.

again... any help would be appreciated, but if i figure this out, i'll let you guys know.  thanks again!

```

2007-02-06 23:34:19.472 AO: audio waiting for space on soundcard: have 3296 need 4096
2007-02-06 23:34:19.473 NVP: A/V Divergence: -0.798477, Rate: 0.246209, Warpfactor: 0.981025, warpfactor_avg: 0.999909
*** glibc detected *** mythfrontend: free(): invalid pointer: 0xa9422680 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb5bbd8bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb5bbda44]
/usr/lib/libmythavutil-0.20.so.0(av_free+0x16)[0xb72e9162]
/usr/lib/libmythavcodec-0.20.so.0(img_resample_close+0x15)[0xb708ecf0]
/usr/lib/libmythtv-0.20.so.0(_ZN13VideoOutputXv15PrepareFrameMemEP11VideoFrame_13FrameScanType+0x84e)[0xb7ac9ebe]
/usr/lib/libmythtv-0.20.so.0(_ZN13VideoOutputXv12PrepareFrameEP11VideoFrame_13FrameScanType+0x270)[0xb7aca376]
/usr/lib/libmythtv-0.20.so.0(_ZN17NuppelVideoPlayer6AVSyncEv+0xc7f)[0xb79e2281]
/usr/lib/libmythtv-0.20.so.0(_ZN17NuppelVideoPlayer18DisplayNormalFrameEv+0x787)[0xb79e5379]
/usr/lib/libmythtv-0.20.so.0(_ZN17NuppelVideoPlayer15OutputVideoLoopEv+0x878)[0xb79e7db0]
/usr/lib/libmythtv-0.20.so.0(_ZN17NuppelVideoPlayer22kickoffOutputVideoLoopEPv+0x42)[0xb79e7ee2]
/lib/tls/i686/cmov/libpthread.so.0[0xb5da0504]
/lib/tls/i686/cmov/libc.so.6(__clone+0x5e)[0xb5c2451e]
======= Memory map: ========
08048000-08186000 r-xp 00000000 08:02 732787     /usr/bin/mythfrontend
08186000-08188000 rw-p 0013e000 08:02 732787     /usr/bin/mythfrontend
08188000-0844c000 rw-p 08188000 00:00 0          [heap]
a88de000-a88df000 ---p a88de000 00:00 0 
a88df000-a90df000 rwxp a88df000 00:00 0 
a9200000-a928e000 rw-p a9200000 00:00 0 
a928e000-a9300000 ---p a928e000 00:00 0 
a9400000-a9429000 rw-p a9400000 00:00 0 
a9429000-a9500000 ---p a9429000 00:00 0 
a9587000-a9588000 ---p a9587000 00:00 0 
a9588000-a9d88000 rwxp a9588000 00:00 0 
a9d88000-a9e00000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
a9e00000-a9f00000 rw-p a9e00000 00:00 0 
a9f40000-a9fb8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
a9fb8000-aa030000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa030000-aa0a8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa0a8000-aa120000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa120000-aa198000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa198000-aa210000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa210000-aa288000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa288000-aa300000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa300000-aa400000 rw-p aa300000 00:00 0 
aa430000-aa4a8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa4a8000-aa520000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa520000-aa598000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa598000-aa610000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa610000-aa688000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa688000-aa700000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa700000-aa800000 rw-p aa700000 00:00 0 
aa840000-aa8b8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa8b8000-aa930000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa930000-aa9a8000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aa9a8000-aaa20000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aaa20000-aaa98000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aaa98000-aab10000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aab10000-aab88000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSans.ttf
aab88000-aac00000 r--p 00000000 08:02 926751     /usr/share/fonts/truetype/freefont/FreeSAborted (core dumped)
ickyb0d@mediab0x ~$ 

```
I don't use the live tv option on the frontend myself, but I have been able to reproduce this bug when trying to.  I will need to experiment with the latest 0.20-fixes to see if it still occurs, or has been fixed.  If it's not fixed, then it will need to be filed upstream with mythtv's bug tracker.
In the interim, don't use live tv :)  The whole idea behind myth is to ditch live tv anyhow...

---

### Post by ickyb0d on 2007-02-13
well as of now, i reinstalled everything and followed the howto pretty closely.  I've done it enough now i know what to fix (i.e. the /etc/mythtv/mysql.txt or whatever) before running mythtv-setup.  I was mainly planning on taking Superm1 up on his suggestion and just record what i want to watch, and don't worry about livetv.  Anyways...

Everything seems to be running fairly well for the past week or so.  I almost think it was a problem with the themes maybe?  Because right now i've left the theme setting and have no problems watching recorded or live tv.  That's the only thing that i can think of that i consistently changed whenever i reinstalled mythtv.  I've even messed around with a handful of options as far as TV Playback as well - and that still hasn't broken anything.  At any rate, thanks for the suggestion and help Superm1, you seem to be all over the place on this mythtv stuff!

---

