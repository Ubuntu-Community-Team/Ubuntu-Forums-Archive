---
title: "How to Speed Up OS"
date: 2015-09-17
forum: General Help
---

### Post by eric75 on 2015-09-17
I've switched from Windows, where I could tweak the OS to run faster by removing startup items, stopping services and more.

I read how to do it with Ubuntu which I am running, but I am not familiar with the startup items enough to know which to stop.

Currently, I see:

backup monitor
Certificate & Key Storage
Files
GPG PW agent
Gsettings 
Indicator application
mount helper
network
onboard
orca scrn reader
pers file sharing
policykit...
pulseaudio
secret storage ...
SSH key agent
update notifier
user folders update

which, if any, would be best to turn off?
anything else i should do to speed up my system?

---

### Post by Bucky Ball on 2015-09-17
I don't see anything I would turn off, but I don't use Ubuntu desktop so not sure what's essential. I would presume you'd need what you have to autostart at boot, though. You are looking at the autostart apps in 'Sessions and Start'? Which Ubuntu release are you using and what flavour? What are the specs of your machine, make, model?

The best way to speed up your system is to add more RAM or use a lighter flavour (or even a minimal install).

In Windows you need to switch off a ton of stuff you will never need that's running in the background at boot. In Ubuntu this is generally not the case.

---

### Post by eric75 on 2015-09-17
OK, thanks. Running ubuntu 14.04 LTS.

I went to Startup Applications in the apps folder, and the machine is an Asus X550C laptop with 4 GB RAM. Not sure about the flavour. How do I find out?

---

### Post by Bucky Ball on 2015-09-17
Ubuntu is the flavour. Other official flavours of Ubuntu that we support here are Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu and Ubuntu Mate.

14.04 LTS. Good. That is supported until 2019 and stable. 

You don't look in any folder, although I guess you could, but don't know about it. What I'm talking about, and this is how I get there, your route might be different, is Settings> Software and Session> Autostart Applications tab. Alternatively, I think you could get there by looking for 'software and session' in the Dash. (Sorry, I think I used 'sessions and startup' previously. Wrong.)

Tick or untick what you want/don't.

---

### Post by chemist931 on 2015-09-17
Compared to Windows 8.1, Ubuntu should really appear blazing fast! Besides upgrading your hardware, you could uninstall unimportant programs, install programs to regulate your processor, or just switch to Xubuntu or Kubuntu.

---

### Post by ian-weisser on 2015-09-17
Time each segment of the startup process:
How many seconds from poweron to grub?
How many seconds from grub to login?
How many seconds after login to usable desktop?

There is software what will time them for you, but they provide much more information than you really need at this stage. Timing it manually is quite acceptable,
Most important: Which of the three segments is most annoying to you?

Also look in /var/log/syslog for the (very long) record of your most recent boot. Are there any long gaps of time? Any cryptic errors?

---

### Post by v3.xx on 2015-09-17
As Bucky Ball said, there is not a lot of bloat with Ubuntu.

Mate and Lubuntu are the fastest out of the box.

If you notice a lag with a particular software package, this could also be dealt with.

One thing that can generally cause a problem is having the wrong video driver or just needing a better one.

---

### Post by grahammechanical on 2015-09-17
Removing items from Startup will reduce boot loading times. But you may not notice the small reductions and it does nothing to speed up the OS once you are at a desktop. And you are asking about speeding up the OS are you not? 

Linux uses a utility to start and stop services. Ubuntu used to use Upstart but now it uses SystemD. I am not sure which is being used in Ubuntu 14.04 but from Ubuntu 15.04 onwards it is SystemD.

I have a lot less RAM than you do and I find the Linux/Ubuntu by default is making good use of system resources. When an application is closed then memory is quickly freed for other uses. 

What may be true of Microsoft Windows is often not true of Linux. Every release of Windows requires ever more powerful hardware. That is not true of Linux/Ubuntu. You may have needed to tweak Windows but I do not think it is true of Linux.

And making the kind of adjustments you are looking to do can easily break the OS. So, have backups of your data and be prepared for a re-install.

Regards.

---

### Post by eric75 on 2015-09-19
To answer Bucky Ball's question:

> You don't look in any folder, although I guess you could, but don't know about it. What I'm talking about, and this is how I get there, your route might be different, is Settings> Software and Session> Autostart Applications tab. Alternatively, I think you could get there by looking for 'software and session' in the Dash. 

I got there from usr/share/applications/Startup Applications. 




Also, in general, it seems to bog with fewer things running. For example, if I have 3 instances of Chromium, with about 15-20 tabs total, plus Thunderbird Mail, and I try to do something new, the screen starts to fade, like it's being overworked. 

And, from the little I know, I open terminal, and type 'top', while I see many processes, I also see Teamviewer running, which I only need on occasion. I didn't know it would have its process running all the time. How can I turn that off?

So, I am wondering:

why is it bogging down with fewer programs running?
should i be looking at, and turning off services?
should i be looking at, and turning off start up programs? If so, which ones?

Or should I go more drastic and start over with another flavor? (I've been trying to set up a dual boot for some time)

---

### Post by ian-weisser on 2015-09-19
> **eric75 said:**
> why is it bogging down with fewer programs running?
It's not about the number of programs.
It's about the CPU and memory consumption of whatever programs are running.
Look for CPU and memory hogs among the 'top' processes.

> **eric75 said:**
> should i be looking at, and turning off services?
Rarely is a service a resource hog. Though occasionally it happens. 'top' will tell you.
More likely are GUI applications...like lots of browser tabs open.

> **eric75 said:**
> Or should I go more drastic and start over with another flavor?
Good question. If your hardware is rather close to Ubuntu's minimum requirements, then a more lightweight flavor has helped others.
However, if the problem is your workflow (like too many browser tabs open), then a different flavor seems unlikely to help much. Try a different browser instead.


Oh, and here is how to [prevent teamviewer from starting]("http://askubuntu.com/questions/267010/how-to-configure-teamviewer-so-it-does-not-load-unless-needed") at login.

---

### Post by Bucky Ball on 2015-09-19
Also, three Chromiums running at the same time is going glug up the PC. Especially with Teamviewer running and a bunch of other things.

---

### Post by eric75 on 2016-02-20
> **ian-weisser said:**
> Oh, and here is how to [prevent teamviewer from starting]("http://askubuntu.com/questions/267010/how-to-configure-teamviewer-so-it-does-not-load-unless-needed") at login.

Thank you, I seemed to have missed this helpful tip earlier. 

I am running TeamViewer 11, and although that post referred to v8, I ran the command, and it seemed to work.  I don't see it in top anymore.

---

### Post by eric75 on 2016-02-20
> **Bucky Ball said:**
> Also, three Chromiums running at the same time is going glug up the PC. Especially with Teamviewer running and a bunch of other things.

I installed Chrome, and stopped using Chromium. Plus I added 8 GB memory. Running better now.

---

### Post by Bucky Ball on 2016-02-20
Please mark the thread as solved. Thanks. 

8Gb of RAM is going to speed up most machines sufficiently. Good luck.

---

### Post by Randy_Moses on 2016-02-21
I migrated from windows 7 to lubuntu....running on my Acer TimelineX..4GRam.......it literally "SIZZLES".....Shuts down in 6 sec,and reboots in under 30 sec........never going back.to windows slavery!

---

