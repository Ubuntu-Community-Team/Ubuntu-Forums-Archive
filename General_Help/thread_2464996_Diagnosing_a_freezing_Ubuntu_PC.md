---
title: "Diagnosing a freezing Ubuntu PC"
date: 2021-07-18
forum: General Help
---

### Post by iamlegenda on 2021-07-18
[COLOR=#141414][FONT=&amp]My work computer has recently started freezing up. When I leave it running for a longer period of time (such as overnight) and returning to it, it looks much like it went to sleep (the screens are turned off but don't give any "no signal" messages, the power button on the PC is still turned on, and the fans are still working). However, I cannot wake it up, regardless of what I do (I've tried moving the mouse, pressing keys, pressing ctrl+alt+del, and even the power button). I also cannot [/FONT][/COLOR]  ssh [COLOR=#141414][FONT=&amp]to it any more and the system logs also do not get recorded properly. So I have to force reboot it (by holding the power button).[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]In all this time it has never frozen/crashed on me while I was actively using it. Additionally, the idle time required for it to freeze up varies wildly. Once I left an [/FONT][/COLOR][FONT=lucida console]rsync[/FONT][COLOR=#141414][FONT=&amp]command running over lunch (roughly an hour) and it froze by the time I came back, while another time it was on for over a week (successfully executing daily [FONT=lucida console]rsync [/FONT]and [FONT=lucida console]rclone [/FONT]jobs via [FONT=lucida console]cron[/FONT] the whole time) with no freezes.[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]I tried some solutions I found online to turn off sleep/suspend, such as turning off "Automatic Suspend" in Power settings, turning off "Suspend when laptop lid is closed" in gnome Tweaks, and adding [/FONT][/COLOR][FONT=lucida console]intel_idle.max_cstate=1[/FONT][COLOR=#141414][FONT=&amp] to [/FONT][/COLOR][FONT=lucida console]/etc/default/grub[/FONT][COLOR=#141414][FONT=&amp]. None of these prevented the issue. I've also messed around with several BIOS settings that could plausibly cause something like this (namely, turning off AMD's XMP feature, adjusting RAM voltage to the exact recommended values I found on the seller's website, and changing Wake Up Event settings) to no avail.[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]I've also considered a hardware issue, so I ran memtest86 and got no errors. I also checked my SSD and HDD for errors as best I could (using SMART diagnostics) and got nothing.[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]The system logs aren't helpful as they aren't written to when the freeze happens (as noted above) - I'm attaching [/FONT][/COLOR][[COLOR=#0000ff][FONT=lucida console]/var/log/syslog[/FONT][/COLOR]]("https://pastebin.ubuntu.com/p/PKhzDzzT6s/")[COLOR=#141414][FONT=&amp] from the most recent freeze anyway. I found a solution to this online, namely following the logs live over an SSH connection from a different computer (using [/FONT][/COLOR][FONT=lucida console]ssh user@workstation journalctl -f[/FONT][COLOR=#141414][FONT=&amp]), however nothing in the logs jumped out at me as an obvious cause of the freeze - I'm attaching [/FONT][/COLOR][FONT=&amp][[COLOR=#0000ff]two such[/COLOR]]("https://pastebin.ubuntu.com/p/SdDVmV5y5P/") [[COLOR=#0000ff]log files[/COLOR]]("https://pastebin.ubuntu.com/p/PQmy5zRyZ4/") [/FONT][COLOR=#141414][FONT=&amp]leading to freezes here regardless.[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]I'm kind of at a loss on how to continue diagnosing this problem. Are there perhaps some other log files I could look at to get an idea of what's going on and whether it's a software or hardware issue? Some way to check for motherboard and CPU errors? Maybe even PSU errors?[/FONT][/COLOR]

[COLOR=#141414][FONT=&amp]Computer specs:
[/FONT][/COLOR]
[LIST]
[*][COLOR=#141414][FONT=&amp]OS: Ubuntu 20.04.2 LTS
[/FONT][/COLOR]
[*][COLOR=#141414][FONT=&amp]CPU: AMD Ryzen 7 1700
[/FONT][/COLOR]
[*][COLOR=#141414][FONT=&amp]MB: MSI X370 SLI PLUS
[/FONT][/COLOR]
[*][COLOR=#141414][FONT=&amp]RAM: G.Skill Ripjaws V 16GB DDR4-3200
[/FONT][/COLOR]
[*][COLOR=#141414][FONT=&amp]GPU: NVIDIA Titan V[/FONT][/COLOR]
[*][COLOR=#141414][FONT=&amp]SSD: [/FONT][/COLOR]Samsung - 860 Evo 500GB M.2-2280
[*]HDD: Toshiba - P300 3TB 3.5" 7200RPM
[/LIST]

---

### Post by TheFu on 2021-07-18
My Ryzen 2600 is really picky about RAM speeds.  I had to slow the RAM down from 2800 to 2733 just a few weeks ago when new crashes started happening every few hrs.  I have the same RAM hardware you have.  There were errors showing up in the system HW log file.  Here's the command that would show that multiple RAM faults were happening.
```
journalctl -b |grep  'System manufacturer System Product' |wc -l
```
I was seeing 50-400 issues in the logs before the system would lock up.  On a perfectly working system, the result is 1. It has been stable for over a week now.
```
$ uptime 
 18:51:40 up 8 days,  9:58,  4 users,
```

Hopefully, this is helpful.  If you don't run the RAM tests at least 24 hrs, I don't think it can be claimed the RAM is fine.

To see older boots, use **journalctl -b -1** ... and just change the number to go back further in boot times.

---

### Post by iamlegenda on 2021-07-21
Hmm...
```
[COLOR=#000000][FONT=&quot]journalctl -b |grep  'System manufacturer System Product' |wc -l
```
didn't find any errors (the wc -l printed out 0).

I've tried setting the RAM speed to 2733 anyway (it was 3200 before when I had XMP turned on and after I turned XMP off it was set to Auto, which resulted in 2133 speed). However, now my computer is acting quite sluggish and unresponsive. I'll try a few more different RAM speeds and see if anything works though.[/FONT][/COLOR]

---

### Post by TheFu on 2021-07-21
That command could be very specific to my system.  I took a shot, trying to help.  Look through the log files, determine where the logs show problems.

AMD doesn't use XMP.  They call it something else. I have it on, except that the speed is manually made slower in the BIOS settings.  My system has been stable since setting the RAM speed to 2733 and it does get very busy a few hours every day.
```
$ uptime 
 08:58:38 up 11 days, 5 min,  4 users,  load average: **12.28, 7.03**, 3.51

```
Your system may not have the same issue. Only the log files AND you LOOKING AT THEM can tell.

---

