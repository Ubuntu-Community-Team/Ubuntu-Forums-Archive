---
title: "Help with log"
date: 2022-12-20
forum: General Help
---

### Post by 842qxgs2 on 2022-12-20
Hi all.
The first time I encountered a Unix (Ubuntu 22.10) system.
Therefore, I ask for help from respected experts.
I am faced with the task of understanding whether or not there were any user actions on the machine 10 months ago, within 2 weeks.
Began of course with the comand last.
I see it.

alex     tty2         tty2             Wed Feb 23 08:34 - crash (17+10:46)
reboot   system boot  5.13.0-30-generi Mon Jan 10 05:07 - 14:33 (139+08:25)
alex     tty2         tty2             Sun Feb 20 15:42 - crash (-41+10:34)
reboot   system boot  5.13.0-28-generi Sun Feb 20 15:42 - 14:33 (97+21:51)

Strange line (10.01.). Or failure, or change by hands?
I apply comand find m, a, c time to this date and I see many files and folders that have been accessed, modified and status changed. Most of them with  permission denied (no timestamp).
I look further. 23.02. was an authorized entry. But I can't trust it 100%. With the find command, the activity is visible at a completely different time and is associated only with the snap. 

2022-02-23 15:48:54.0000000000 /usr/lib/snapd/snap-confine
2022-02-23 15:48:54.0000000000 /usr/lib/snapd/snap-bootstrap
2022-02-23 15:48:54.0000000000 /usr/lib/snapd/info
2022-02-23 15:48:54.0000000000 /usr/lib/environment.d/990-snapd.conf
2022-02-23 15:48:54.0000000000 /usr/bin/ubuntu-core-launcher
2022-02-23 15:48:54.0000000000 /usr/bin/snapfuse
2022-02-23 15:48:54.0000000000 /usr/bin/snapctl
2022-02-23 15:48:54.0000000000 /usr/bin/snap
etc.

In the days that followed, there were also many files and folders that were accessed, modified. But since the laptop even works in sleep mode, it cannot be stated unequivocally that these were user actions. Unfortunately, I did not find how to view network activity 10 months ago. Couldn't find time change logs. I will be glad for any hints.

---

### Post by TheFu on 2022-12-20
'journalctl' allows bracketing dates in the logs. This is an advance query, so I'd have to read the manpage on the program.
```
man journalctl
```
to see it.

This assumes you allow logs to be kept that long.

BTW, no processing happens when in sleep mode.  The RAM is frozen (powered just to hold the current state for each byte) and the CPU stops cycling, except one core will wake up if a known event happens (power button or keyboard or mouse move are examples).  This is typically handled by the motherboard BIOS, not the OS.

---

### Post by 842qxgs2 on 2022-12-20
> **TheFu said:**
> 'journalctl' allows bracketing dates in the logs. This is an advance query, so I'd have to read the manpage on the program.
```
man journalctl
```
to see it.

This assumes you allow logs to be kept that long. 

Journal, unfortunately, will not help here.  Journal begins at Tue 2022-08-02

> **TheFu said:**
>  BTW, no processing happens when in sleep mode.  The RAM is frozen (powered just to hold the current state for each byte) and the CPU stops cycling, except one core will wake up if a known event happens (power button or keyboard or mouse move are examples).  This is typically handled by the motherboard BIOS, not the OS.

Unfortunately, this is not the case.

2022-12-16 06:27:34.0000000000 /snap/firefox/2211/usr/lib/firefox/gmp-clearkey/0.1/manifest.json
2022-12-16 05:26:51.0000000000 /snap/firefox/2211/usr/lib/firefox/application.ini
2022-12-16 04:22:37.0000000000 /snap/firefox/2211/usr/lib/x86_64-linux-gnu/pipewire-0.3/libpipewire-module-spa-node.so
2022-12-16 04:22:37.0000000000 /snap/firefox/2211/usr/lib/x86_64-linux-gnu/pipewire-0.3/libpipewire-module-spa-node-factory.so
2022-12-16 04:22:37.0000000000 /snap/firefox/2211/usr/lib/x86_64-linux-gnu/pipewire-0.3/libpipewire-module-spa-device.so
2022-12-16 04:22:37.0000000000 /snap/firefox/2211/usr/lib/x86_64-linux-gnu/pipewire-0.3/libpipewire-module-spa-device-factory.so
2022-12-16 04:22:37.0000000000 /snap/firefox/2211/usr/lib/x86_64-linux-gnu/pipewire-0.3/libpipewire-module-session-manager.so
2022-12-16 04:22:37.0000000000 /snap/firefox/2211/usr/lib/x86_64-linux-gnu/pipewire-0.3/libpipewire-module-rt.so

At this time, I was definitely asleep, the laptop lid was closed, sleep mode.

---

### Post by MAFoElffen on 2022-12-20
Ubuntu is not Unix, it is Linux. Semantics, but differences are there.

In sleep mode in a laptop, the lid switch signals the OS to write it's memory out to disk, in either a file or partition. All processing stops, until it gets a signal to resume.

"You" would have to hard code this OS to not turn off by telling it to ignore the lid switch signal. Not saying you couldn't do that, but I doubt that you have done that.

---

### Post by TheFu on 2022-12-20
[https://www.kernel.org/doc/html/v5.0/admin-guide/pm/sleep-states.html](https://www.kernel.org/doc/html/v5.0/admin-guide/pm/sleep-states.html)

Consider these terms:
UNIX - proprietary UNIX OSes, like Solaris, HP-UX, AIX, Ultrix, Digital Unix, others.
Linux - any system running the Linux kernel.  Android is Linux.
Unix that is a group of BSD, UNIX, Linux and other UNIX-like OSes.  Just the capitalization matters.

If the goal is for forensic analysis, I don't have the skills beyond looking at what the system already provides. Or looking in my backup sets.

---

### Post by 842qxgs2 on 2022-12-20
> **MAFoElffen said:**
> Ubuntu is not Unix, it is Linux. Semantics, but differences are there.

In sleep mode in a laptop, the lid switch signals the OS to write it's memory out to disk, in either a file or partition. All processing stops, until it gets a signal to resume.

"You" would have to hard code this OS to not turn off by telling it to ignore the lid switch signal. Not saying you couldn't do that, but I doubt that you have done that.
I am confronted with the fact, as it is, so it is. Therefore, the answer is sought taking into account the realities. Of course, I'm interested in signs that say 100% that these are the actions of the user and not the system.

---

### Post by 842qxgs2 on 2022-12-20
> **TheFu said:**
> [https://www.kernel.org/doc/html/v5.0/admin-guide/pm/sleep-states.html](https://www.kernel.org/doc/html/v5.0/admin-guide/pm/sleep-states.html)


If the goal is for forensic analysis, I don't have the skills beyond looking at what the system already provides. Or looking in my backup sets.
This is what interests me, to get the maximum out of the logs. And the advice of connoisseurs, which files or folders the system can change or open, and which not (in sleep mode). And 3 more important things. Where are time changes stored? How to view the network connection log for the past months? Under what circumstances might an authorized login look like an error?
I naively assume that it should be stored somewhere.
At least as far as time is concerned, it's a matter of security.

---

### Post by 842qxgs2 on 2022-12-20
Perhaps with the find command and a specific (? what) word it can be found?

---

### Post by TheFu on 2022-12-20
> **842qxgs2 said:**
> This is what interests me, to get the maximum out of the logs. And the advice of connoisseurs, which files or folders the system can change or open, and which not (in sleep mode). And 3 more important things. Where are time changes stored? How to view the network connection log for the past months? Under what circumstances might an authorized login look like an error?
I naively assume that it should be stored somewhere.
At least as far as time is concerned, it's a matter of security.

I don't really understand some of the paragraph above. Sorry.

Network connections aren't automatically logged.  

That would be something extra that you'd need to add and doing all that logging would slow a system.  In enterprises, they use specialized hardware and switch taps to capture network packets.  Depending on how paranoid you are, you can use wireshark or an IDS/IPS tool. These aren't light processes.

Creation, Access, and modified times for files are stored in the inode for the file, assuming you don't disable those with mount settings.  I disable atime in my mounts, since there is little to be learned by some process reading a file and it would drastically increase writes to an SSD, drastically shortening the expected SSD life.  The 'stat' function can provide more information about the extra information stored with files.  Besides the C function, there's a command with a manpage.  I'm assuming Linux native file systems.  Other, foreign, file systems like NTFS and FAT-whatever probably have some of the same fields, but not all of them, so YMMV.

In the 1990s, there was a tool called "cops" that we'd run weekly to track any file changes.  For the last 20 yrs or so, I've used versioned backups for that same purpose.  Versioned backups have 1001 uses.

---

### Post by TheFu on 2022-12-20
If you are looking to learn computer forensics, get in contact with a local DEFCON group.  [https://defcon.org/](https://defcon.org/)   I've never seen anyone pay to be a member. About the most payment that happens is to buy food & drink at the meeting places as a form of compensation for providing the space.  So for the cost of a beer and meal, my local DC group provides informal access to experts of all sorts AND presentations on a wide range of topics.  Most of the presentations I recall is about specific tools for red-teams or blue-teams.  

I'm a member of a few locally and have visited some others internationally when travel and their meetings lined up.  Some may be meeting virtually due to COVID still.  My local group does hybrid meetings ... in-person and online.  The other local group only meets in-person except when govt COVID restrictions effectively closed the normal bar where they met.  Due to traffic in my area, there are 4 surrounding groups, so the hour drive isn't needed to get to the main group.  Typically, someone will present at each of the groups, with the most polished presentation being last at the main group to 30-75 people.  Beginners are welcome.  I remember a few who showed up 10 yrs ago just as they were starting college courses in data security.  Now they've been working 5 yrs in the industry and are the people to know for specific techniques ... or to get an introduction for a job at their company.

It is sorta scary what some of the presentations show.  One guy showed how to get passed a bank's login protections, without any credentials, for example.  He did it live.  15 yrs prior, that was where my money was!  I know people who work for that bank, but not in the web-security part.

When my group does a meeting, we use handles (no names) and no photography is allowed.  This is to protect everyone - good guys and bad guys.  Locally, we have lots of people doing govt work, so they can't really talk about their jobs, but that doesn't mean they won't talk about general stuff they happen to know.  The state govt people talk about anything.  One guy worked in the University where some voter information was made publicly available by accident and the local news and Feds got involved. It became a national story ... because someone figured out how to manually type in a URL to access data.  The state police and lawyers all wanted laws changed to call that "hacking".  He was data made public by someone on accident. No hacking involved.  With the DC member explaining what really happened, it was clear the problem was with a state worker putting data where it should never have been placed.  That didn't matter. The district attorney and state legislature passed a terrible law. Fortunately, the Governor refused to sign it. It would have gutted IT security industry from our state, just to prevent politicians and state employees from looking stupid for doing stupid things.

Sigh.

If the DC group has a speaker lined up, you never know what you'll get. Could be amazing or it could be the worst presentation you've ever seen.

Defcon group names usually tie back to telephone area codes. Different parts of the world do that differently.  [https://forum.defcon.org/node/231135](https://forum.defcon.org/node/231135) is the link to international groups.  The count of members at those links doesn't reflect reality, BTW.  That's just a number of people that registered through that website, which has little 


And if you have any security conferences within travel distances - GO!  Expect all your electrons to be hacked while there, so only bring stuff you expect to wipe and don't bring any smartphone.  I promise, it will be hacked.  I have an old flip phone for those conferences.  If I take a laptop (because I'm presenting), then I expect to wipe it when I get home.  One year I was helping with the "capture the flag" team competition and had a fresh Ubuntu install from the day before, 100% patched.  That evening, I found some files in my HOME on the box that clearly proved it had been hacked.  The laptop never left my sight/side the entire time I was there.  I never joined it to any network. Didn't even have wifi enabled in the BIOS.  When I got back home, I spent a bit trying to figure out how they got in.  All I could come up with was via bluetooth.  Because I'd done a fresh install, Ubuntu enables bluetooth, which I don't use, but had forgotten to disable and remove the drivers+libraries+tools.  Nobody had time to even connect a flash drive to the system for 15 seconds, so I determined it was bluetooth they'd hacked.

I was convinced.

Then I wiped the system and did a fresh load of the OS.

Anyway, find and go to a few local defcon meetings. Even if the first meeting isn't great, go at least 1 more time. I think you'll be surprised.

---

### Post by 842qxgs2 on 2022-12-24
I started to study the topic of Linux Forensics.
Found it.
who -t, --time print last system clock change
But I don't have an answer. To which log, journal is this request?
Is there any way to find out: last system clock change?
Maybe inode analysis will help here?
Tell me, what are the requests?

---

### Post by condeprincedusang on 2023-01-15
Hello
I wanted to say thanks for your answer. I am fairly new at all of this, and was brought into it because I have been hacked by an adversary who had access to my systems, devices, credentials for a longtime. When I got to install my own VMs in November 2022, I was shocked to see that Ubuntu (and all the other ones) were already present prior to my installation and for a while back. 
According to the logs, a straight DDOS attack was performed (regularly) and files were installed, removed, virtual microphones, cameras were started etc... The only positive thing about it, is that it explained the series of events, that before starting to dive into the matter, I could see, or sense, but couldn't explain. By the way, if anyone sees the notification "your screen is being observed" on their MacBook, I can guarantee you that a remote access via VM has been successfully established and that your screen IS being observed.
The command Sudo less . log was the best way to access all the logs. 
Thanks again for your cool answer, I am planning on joining my local DEFCON group as soon as possible. 
Cheers!







> **TheFu said:**
> If you are looking to learn computer forensics, get in contact with a local DEFCON group.  [https://defcon.org/](https://defcon.org/)   I've never seen anyone pay to be a member. About the most payment that happens is to buy food & drink at the meeting places as a form of compensation for providing the space.  So for the cost of a beer and meal, my local DC group provides informal access to experts of all sorts AND presentations on a wide range of topics.  Most of the presentations I recall is about specific tools for red-teams or blue-teams.  

I'm a member of a few locally and have visited some others internationally when travel and their meetings lined up.  Some may be meeting virtually due to COVID still.  My local group does hybrid meetings ... in-person and online.  The other local group only meets in-person except when govt COVID restrictions effectively closed the normal bar where they met.  Due to traffic in my area, there are 4 surrounding groups, so the hour drive isn't needed to get to the main group.  Typically, someone will present at each of the groups, with the most polished presentation being last at the main group to 30-75 people.  Beginners are welcome.  I remember a few who showed up 10 yrs ago just as they were starting college courses in data security.  Now they've been working 5 yrs in the industry and are the people to know for specific techniques ... or to get an introduction for a job at their company.

It is sorta scary what some of the presentations show.  One guy showed how to get passed a bank's login protections, without any credentials, for example.  He did it live.  15 yrs prior, that was where my money was!  I know people who work for that bank, but not in the web-security part.

When my group does a meeting, we use handles (no names) and no photography is allowed.  This is to protect everyone - good guys and bad guys.  Locally, we have lots of people doing govt work, so they can't really talk about their jobs, but that doesn't mean they won't talk about general stuff they happen to know.  The state govt people talk about anything.  One guy worked in the University where some voter information was made publicly available by accident and the local news and Feds got involved. It became a national story ... because someone figured out how to manually type in a URL to access data.  The state police and lawyers all wanted laws changed to call that "hacking".  He was data made public by someone on accident. No hacking involved.  With the DC member explaining what really happened, it was clear the problem was with a state worker putting data where it should never have been placed.  That didn't matter. The district attorney and state legislature passed a terrible law. Fortunately, the Governor refused to sign it. It would have gutted IT security industry from our state, just to prevent politicians and state employees from looking stupid for doing stupid things.

Sigh.

If the DC group has a speaker lined up, you never know what you'll get. Could be amazing or it could be the worst presentation you've ever seen.

Defcon group names usually tie back to telephone area codes. Different parts of the world do that differently.  [https://forum.defcon.org/node/231135](https://forum.defcon.org/node/231135) is the link to international groups.  The count of members at those links doesn't reflect reality, BTW.  That's just a number of people that registered through that website, which has little 


And if you have any security conferences within travel distances - GO!  Expect all your electrons to be hacked while there, so only bring stuff you expect to wipe and don't bring any smartphone.  I promise, it will be hacked.  I have an old flip phone for those conferences.  If I take a laptop (because I'm presenting), then I expect to wipe it when I get home.  One year I was helping with the "capture the flag" team competition and had a fresh Ubuntu install from the day before, 100% patched.  That evening, I found some files in my HOME on the box that clearly proved it had been hacked.  The laptop never left my sight/side the entire time I was there.  I never joined it to any network. Didn't even have wifi enabled in the BIOS.  When I got back home, I spent a bit trying to figure out how they got in.  All I could come up with was via bluetooth.  Because I'd done a fresh install, Ubuntu enables bluetooth, which I don't use, but had forgotten to disable and remove the drivers+libraries+tools.  Nobody had time to even connect a flash drive to the system for 15 seconds, so I determined it was bluetooth they'd hacked.

I was convinced.

Then I wiped the system and did a fresh load of the OS.

Anyway, find and go to a few local defcon meetings. Even if the first meeting isn't great, go at least 1 more time. I think you'll be surprised.

---

