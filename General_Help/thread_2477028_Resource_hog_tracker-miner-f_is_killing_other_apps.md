---
title: "Resource hog tracker-miner-f is killing other apps through oom-kill."
date: 2022-07-12
forum: General Help
---

### Post by DuckHook on 2022-07-12
NOTE: TLDR version; skip to post #15 & 16 for solution.

[HR][/HR]

I'm getting hit by the systemd-oomd bug.

I have 64GB of RAM on my main box which ought to be plenty, but am experiencing spontaneous app deaths with no opportunity to save. I do not keep massive numbers of apps running. In fact, typical memory load looks like this:```
duckhook@Zeus:~$ free -hw
               total        used        free      shared     buffers       cache   available
Mem:            62Gi       5.6Gi        55Gi        65Mi       124Mi       1.0Gi        56Gi
Swap:           63Gi       770Mi        63Gi
```
Apps that OOM kills are not only RAM hogs like browsers, but even minor apps like gedit. The logs show systemd-oomd to be the culprit (I've filtered for significance):```
19:51:01 systemd: tracker-miner-fs-3.service: Failed with result 'oom-kill'.
19:51:01 kernel: oom_reaper: reaped process 6439 (tracker-miner-f), now anon-rss:0kB, file-rss:0kB, shmem-rss:4kB
19:50:59 systemd: user@1000.service: A process of this unit has been killed by the OOM killer.
19:50:59 systemd: user@1000.service: A process of this unit has been killed by the OOM killer.
19:50:59 systemd: tracker-miner-fs-3.service: A process of this unit has been killed by the OOM killer.
19:50:59 kernel: Out of memory: Killed process 6439 (tracker-miner-f) total-vm:127921280kB, anon-rss:60906104kB, file-rss:0kB, shmem-rss:4kB, UID:1000 pgtables:249416kB oom_score_adj:0
19:50:59 kernel: oom-kill:constraint=CONSTRAINT_NONE,nodemask=(null),cpuset=/,mems_allowed=0,global_oom,task_memcg=/user.slice/user-1000.slice/user@1000.service/background.slice/tracker-miner-fs-3.service,task=tracker-miner-f,pid=6439,uid=1000
19:50:58 kernel: [   1239]   130  1239     3706      300    69632       10          -900 systemd-oomd
19:50:58 kernel:  oom_kill_process.cold+0xb/0x10
19:50:58 kernel: dnsmasq invoked oom-killer: gfp_mask=0x1100cca(GFP_HIGHUSER_MOVABLE), order=0, oom_score_adj=0
17:57:25 systemd: Started Userspace Out-Of-Memory (OOM) Killer.
```…the times match my app expirations, so I'm confident this is the problem.

My questions are:

[LIST=1]
[*]Am I safe disabling systemd-oomd?
[*]If not, are there workarounds?
[*]Does an app killed by oom leave loose ends that need cleaning up?
[/LIST]
Thanks in advance for all expertise and responses.

---

### Post by Bashing-om on 2022-07-12
Hey DuckHook --

Have you seen: [https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Drops-Swap-Kill](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Drops-Swap-Kill)

Where the parameter " ManagedOOMSwap=auto" is proposed - from the Jammy proposed archive.

I know that you know better then I -

[INDENT]just things I run across
[/INDENT]

---

### Post by DuckHook on 2022-07-12
Thanks for this, Bashing&#8209;om.

I'm happy to see that they are addressing the overly aggressive swap issue, but I'm not sure this applies to me. As you can see from my memory report, I have defined a 64 GB swap partition (in case I ever want to use hibernate, which I am unlikely to actually do), so I don't think my issue arises from running short on swap.

I think it is a bug in the OOM subsystem. I don't believe that I ever come close to using even half of my RAM. The only reason I have so much is for the few occasions when I am manipulating monster GIMP files, but I haven't even done that yet on this new(ish) box.

I'll keep an eye out for new OOM developments and I do appreciate your pointing me to this update. In the meantime, I'm wondering if I can disable OOM until it's more stable?

---

### Post by DuckHook on 2022-07-13
After reading up on OOM in a number of sources, I'm not sure I like the idea of disabling it. However, the way it is implemented in Jammy is a real problem. I've lost work because of its aggressiveness.

In the course of my research, I did come across [this gem]("https://lwn.net/Articles/104185/") from [Andries Brouwer]("https://en.wikipedia.org/wiki/Andries_Brouwer"):> An aircraft company discovered that it was cheaper to fly its planes with less fuel on board. The planes would be lighter and use less fuel and money was saved.

On rare occasions however the amount of fuel was insufficient, and the plane would crash. This problem was solved by the engineers of the company by the development of a special OOF (out-of-fuel) mechanism. In emergency cases a passenger was selected and thrown out of the plane. (When necessary, the procedure was repeated.)  A large body of theory was developed and many publications were devoted to the problem of properly selecting the victim to be ejected. Should the victim be chosen at random? Or should one choose the heaviest person? Or the oldest? Should passengers pay in order not to be ejected, so that the victim would be the poorest on board? And if for example the heaviest person was chosen, should there be a special exception in case that was the pilot? Should first class passengers be exempted?

Now that the OOF mechanism existed, it would be activated every now and then, and eject passengers even when there was no fuel shortage. The engineers are still studying precisely how this malfunction is caused.
Who says mathematicians don't have a sense of humour?

---

### Post by TheFu on 2022-07-13
Many thanks for being volunteer testers of new releases.
This problem has been discussed in public for at  least 3 weeks. Canonical should have addressed it already, right?

I can't imagine any way that a user would eat up 16GB of RAM, much less 64G.  If it were me, I'd disable it.  Of course, when you do have huge RAM usage, you'll need to "feel the swap" being used carefully, so you can manually restart the bloated browser(s) as needed.  

What I've done to prevent RAM abuse in browsers is to run them inside a firejail that is restricted to 10G of RAM use. I started with 4G, thinking that would be 3x more than any browser would need, but firejail was killing the browser about once a week due to out of memory.  the firejail option I use is: --rlimit-as=10200000000  I think it is a bit generous, but haven't noticed the browsers being killed in months, so I'm calling it a win.

I'm not running 22.04, so I don't have to fight with snap-only browsers.

---

### Post by DuckHook on 2022-07-13
> **TheFu said:**
> Many thanks for being volunteer testers of new releases.
:lolflag:
> This problem has been discussed in public for at  least 3 weeks. Canonical should have addressed it already, right?
](*,)
> I can't imagine any way that a user would eat up 16GB of RAM, much less 64G.  If it were me, I'd disable it.
I've resolved to give this a try, in the spirit of being a "volunteer tester of new releases".
> …Of course, when you do have huge RAM usage, you'll need to "feel the swap" being used carefully, so you can manually restart the bloated browser(s) as needed.
I'd be happy if it were only the browsers. I've had it happen with tiny apps like gedit. So far, thankfully, not with Libreoffice. Losing work there would be awful.
> What I've done to prevent RAM abuse in browsers is to run them inside a firejail that is restricted to 10G of RAM use. I started with 4G, thinking that would be 3x more than any browser would need, but firejail was killing the browser about once a week due to out of memory.  the firejail option I use is: --rlimit-as=10200000000  I think it is a bit generous, but haven't noticed the browsers being killed in months, so I'm calling it a win.
I run mine in a LXD container and can do something similar in terms of limiting resource usage. I will review my settings.
> I'm not running 22.04, so I don't have to fight with snap-only browsers.
I've worked around this by adding the mozillateam PPA and running firefox-esr. So far, so good. I don't miss the latest bells and whistles at all.

Thanks for the input, especially the encouragement to try disabling *oomd*. I'll report back if it creates problems. Otherwise, assume that the kludge works.

---

### Post by #&amp;thj^% on 2022-07-13
might I suggest that instead of disabling systemd-oomd it would be better to change the memory pressure limit and timeout so it's not aggressively killing processes.
IE: example of my /usr/lib/systemd/system/user@.service.d/10-oomd-user-service-defaults.conf:
```
[Service]
ManagedOOMMemoryPressure=kill
ManagedOOMMemoryPressureLimit=65%
```

With this, the daemon doesn't kill anything on my machine under considerable load. You can rise the ManagedOOMMemoryPressureLimit to 100% if you want a really "lazy" OOM daemon.
I'm not sure I would completely disable it, >> besides A disabled service will still start if it is a dependency of another service. This is not a bug.
EDIT: philhughes has pointed to this>>"user@1000.service: A process of this unit has been killed by the OOM killer" and not >> "systemd-oomd"
I also agree this is very bug worthy...

---

### Post by DuckHook on 2022-07-13
> **1fallen said:**
> might I suggest that instead of disabling systemd-oomd it would be better to change the memory pressure limit and timeout so it's not aggressively killing processes.
IE: example of my /usr/lib/systemd/system/user@.service.d/10-oomd-user-service-defaults.conf:
```
[Service]
ManagedOOMMemoryPressure=kill
ManagedOOMMemoryPressureLimit=65%
```

With this, the daemon doesn't kill anything on my machine under considerable load. You can rise the ManagedOOMMemoryPressureLimit to 100% if you want a really "lazy" OOM daemon.
I'm not sure I would completely disable it, >> besides A disabled service will still start if it is a dependency of another service. This is not a bug.
Wow. Thanks for this 1fallen.

Because of this problem, I guess I'm now down to tinkering with fundamental system settings on my production box. What could possibly go wrong with that, hey?

I can disable and then mask the service, so that's a workaround to the dependency problem, but I hear what you are advising.

Thanks for this option. It's much appreciated.

---

### Post by #&amp;thj^% on 2022-07-13
> **DuckHook said:**
> 
I can disable and then mask the service, so that's a workaround to the dependency problem, but I hear what you are advising.

Thanks for this option. It's much appreciated.
I'm curious what the side effects would be, I can promise there will be some, maybe small or a deal breaker.
> **DuckHook said:**
> 

Because of this problem, I guess I'm now down to tinkering with fundamental system settings on my production box. What could possibly go wrong with that, hey?

:lolflag: I have faith in your good sense. ;)

---

### Post by philhughes on 2022-07-13
From the log entries you have posted, it appears to me that the kernel's OOM killer (oom-killer) has been invoked before systemd-oomd, so it might be nothing to do with systemd-oomd. If you want to get to the bottom of this, it would be best to file a bug report with full logs. Where would be the best place to do that I'm not sure.

For reference, there is a mailing list thread on the systemd-oomd bug:

[https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042116.html](https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042116.html)

---

### Post by #&amp;thj^% on 2022-07-13
> **philhughes said:**
> From the log entries you have posted, it appears to me that the kernel's OOM killer (oom-killer) has been invoked before systemd-oomd, so it might be nothing to do with systemd-oomd. If you want to get to the bottom of this, it would be best to file a bug report with full logs. Where would be the best place to do that I'm not sure.

For reference, there is a mailing list thread on the systemd-oomd bug:

[https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042116.html](https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042116.html)

Good catch, I was more worried over DH disabling the service, and failed to read his logs.
Agreed very bug worthy. :)

---

### Post by grahammechanical on 2022-07-13
Some links I found on Ubuntu.com

earlyoom manpages

[https://manpages.ubuntu.com/manpages/impish/man1/earlyoom.1.html?_ga=2.251722829.535297680.1657659107-1174033420.1643366925](https://manpages.ubuntu.com/manpages/impish/man1/earlyoom.1.html?_ga=2.251722829.535297680.1657659107-1174033420.1643366925)

oom manpages

[https://manpages.ubuntu.com/manpages/impish/man1/oomd.1.html?_ga=2.221247196.535297680.1657659107-1174033420.1643366925](https://manpages.ubuntu.com/manpages/impish/man1/oomd.1.html?_ga=2.221247196.535297680.1657659107-1174033420.1643366925)

Progress reports

Jan 31 2022

[https://lists.ubuntu.com/archives/ubuntu-devel/2022-January/041819.html?_ga=2.12638963.535297680.1657659107-1174033420.1643366925](https://lists.ubuntu.com/archives/ubuntu-devel/2022-January/041819.html?_ga=2.12638963.535297680.1657659107-1174033420.1643366925)

June 9 2022

[https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042116.html?_ga=2.12638963.535297680.1657659107-1174033420.1643366925](https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042116.html?_ga=2.12638963.535297680.1657659107-1174033420.1643366925)

June 23 2022

[https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042159.html?_ga=2.207157335.535297680.1657659107-1174033420.1643366925](https://lists.ubuntu.com/archives/ubuntu-devel/2022-June/042159.html?_ga=2.207157335.535297680.1657659107-1174033420.1643366925)

I am reminded of the dispute that went on between Debian developers when it was proposed to replace Canonical's Upstart code with Redhat's Systemd. The Debian developers who disagreed with the proposal said that Systemd was intended to be more than a simple system for starting and stopping system services. It would end up with its tentacles in all parts of the OS. Many of those disagreeing developers quit Debian and forked the code to produce Devuan which was to be a version of Debian without SystemD

Regards

---

### Post by philhughes on 2022-07-13
In fact, re-reading the filtered logs, it is not clear that systemd-oomd was involved at all. The kernel's oom-killer killed a process (tracker-miner-f) and this was recognised by systemd, not systemd-oomd. There are no posted log entries for systemd-oomd. See the following on Fedora for where both oom-killer and systemd-oomd were involved (as this is Fedora, it is possible that the log entries may be different):

[https://bugzilla.redhat.com/show_bug.cgi?id=1941340](https://bugzilla.redhat.com/show_bug.cgi?id=1941340)

---

### Post by DuckHook on 2022-07-13
Just stepped away for a few hours and… wow. Thanks so much for the additional input from all parties.
> **philhughes said:**
> In fact, re-reading the filtered logs, it is not clear that systemd-oomd was involved at all. The kernel's oom-killer killed a process (tracker-miner-f) and this was recognised by systemd, not systemd-oomd. There are no posted log entries for systemd-oomd. See the following on Fedora for where both oom-killer and systemd-oomd were involved (as this is Fedora, it is possible that the log entries may be different):

[https://bugzilla.redhat.com/show_bug.cgi?id=1941340](https://bugzilla.redhat.com/show_bug.cgi?id=1941340)
This just goes to show how much more I need to learn about reading logs. I assumed that the concurrence of systemd messages with kernel messages meant that it was systemd-oomd at fault, but now that you've pointed out the kernel message origins, I'm not sure anymore. Thanks for the attention to detail.

I'm still sorta scratching my head about it though:

[LIST]
[*]This didn't happen at all on this box when I was running Impish.
[*]It doesn't happen on my other boxes that are running Focal.
[*]It only started happening when I upgraded to Jammy, which was also the first time that Canonical activated systemd-oomd by default.
[*]Ergo: I just assumed that the kills were related to systemd-oomd, especially given that so many others had identified this to be the culprit, but maybe I'm wrong.
[*]It would be a crazy coincidence though, that my problems would manifest at the same time as a known oom issue, yet be unrelated to it. But coincidences do happen and I'm more than willing to eliminate or confirm other possibilities.
[/LIST]
I'll wait until it happens again, then post full logs somewhere. I think I'll start on Launchpad. They may direct me elsewhere. They're usually pretty good about giving such redirects if they feel that the issue is upstream.

I'm also going to seriously look into tracker-miner. Preliminary research shows that this can be a crippling CPU/RAM hog, so I'll let everyone know what comes of that.

I just wish the issue was not on my production box—I don't mind contributing as a tester, but it's nerve&#8209;wracking doing so on my main machine.

---

### Post by DuckHook on 2022-07-13
Ahah!

It's happening again and look what top shows:```
duckhook@Zeus:~$ top

top - 15:02:30 up 49 min,  1 user,  load average: 1.99, 2.02, 1.62
Tasks: 567 total,   2 running, 565 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.4 us,  2.7 sy,  5.4 ni, 91.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  64209.9 total,    466.6 free,  62930.6 used,    812.7 buff/cache
MiB Swap:  65536.0 total,  54311.5 free,  11224.5 used.    571.9 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                          
   4743 duckhook  39  19   67.7g  56.6g   9696 R  93.3  90.2  48:08.75 tracker-miner-f 
```
So, the culprit has been identified!

Nothing to do with browsers or systemd-oomd or kernel oom at all. Just a runaway unimportant system process.

What a stupid way for a system utility to behave!

I don't even want /home directory searches. I'm going to look at ways of disabling or uninstalling tracker-miner-f.

---

### Post by DuckHook on 2022-07-13
Kudos to philhughes.

That's some discerning eye and sharp mind to note the real culprit, especially when presented with evidence as skimpy as that which I posted.

For the sake of posterity, I'm detailing what I've done:

I'm not alone in encountering this problem. tracker and its associated utilities (like tracker-miner-f) are utility services that are hard dependencies of Nautilus. Nautilus uses them to construct a database of all files in /home for faster searches of content, Nautilus bookmarks, starred searches, etc. By disabling these services, one also disables all of that Nautilus functionality, so a caution is in order for those who rely on these functions.

I don't use Nautilus for such searches. My searches are all done on the command line using CLI utilities like grep, find, locate, etc, so the loss of Nautilus search is immaterial to me. Simply uninstalling them won't work. They are hard Nautilus dependencies, so removing them also removes Nautilus. To disable tracker in Focal and earlier:```
systemctl --user mask tracker-store.service tracker-miner-fs.service tracker-miner-rss.service tracker-extract.service tracker-miner-apps.service tracker-writeback.service
tracker reset --hard
reboot
```
To disable tracker in Jammy and later:```
systemctl --user mask tracker-extract-3.service tracker-miner-fs-3.service tracker-miner-rss-3.service tracker-writeback-3.service tracker-xdg-portal-3.service tracker-miner-fs-control-3.service
tracker3 reset -s -r
reboot
```This disables the tracker functionality for the local user only. The process must be repeated for each user separately. This provides a welcome fineness of control since it can be applied only to those who want it.

I've already commented on how stupid it is to have a utility so unbounded that it will overrun CPU/RAM and oom&#8209;kill your work rather than constrain itself to using a max of, say, half the available system resources, but it is what it is.

Additionally, I want to note for posterity the following:

[LIST=1]
[*]This thread illustrates the danger of assuming that problems are due to a preconceived cause. I had read about systemd-oomd and a cursory log check appeared to confirm that assumption. But OS problems can be very subtle and they have no respect for our preconceived prejudices.
[*]Impatience is our enemy. Had I just dived into my initial plan and disabled systemd&#8209;oomd, I may have broken lots of things and now be facing a full reinstallation rather than a simple fix. This leads to:
[*]The collective brains in these forums are a lot lot smarter than dumb little ol' me. The total knowledge and wisdom of this community is like sunlight compared to the flickering candle of my knowledge. So, ***make use of it***.
[/LIST]
Lastly, I'm marking the problem "solved" and will change the thread title to reflect the real problem to faciliate future searches.

Thanks to all of you who responded and to the community at large—even those who did not respond to this problem but have helped others elsewhere. You saved me from a world of hurt and helped me learn something too.

---

### Post by TheFu on 2022-07-13
Live by the GUI.
Die (or be killed) by the GUI.

Just one more example.

And looking at the logs now, it is pretty clear that we all missed the root cause before  philhughes actually looked at the logs. Nice job Phil. I'm a bit embarrassed.

---

### Post by philhughes on 2022-07-14
Glad you worked out what was going on DuckHook.

To add for future reference: the process killed by the OOM killer isn't necessarily the one that is causing the problem. When the killer is invoked, it goes through a process to decide which process to kill. See for example:

[https://unix.stackexchange.com/questions/153585/how-does-the-oom-killer-decide-which-process-to-kill-first](https://unix.stackexchange.com/questions/153585/how-does-the-oom-killer-decide-which-process-to-kill-first)

That link is quite old, and the details may have changed, but the concept remains the same I think.

Of course in your case it is fairly obvious that tracker-miner-fs.service is the cuplrit.

---

### Post by #&amp;thj^% on 2022-07-14
> **TheFu said:**
> Live by the GUI.
Die (or be killed) by the GUI.

Just one more example.



:lolflag: agreed ;)
> **TheFu said:**
> 
And looking at the logs now, it is pretty clear that we all missed the root cause before  philhughes actually looked at the logs. Nice job Phil. I'm a bit embarrassed.

I was too, I just reacted too soon is all, but kudos to Phil for our oversight.:KS

---

