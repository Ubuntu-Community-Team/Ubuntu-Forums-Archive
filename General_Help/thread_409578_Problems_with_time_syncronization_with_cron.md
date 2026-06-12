---
title: "Problems with time syncronization with cron"
date: 2007-04-14
forum: General Help
---

### Post by dave-gallagher on 2007-04-14
Hello,

I'm running Ubuntu Edgy Server 6.10 inside of a VMWare Server environment on top of a Windows box.  Because it's virtualized, time gets out of sync often even though VMWare-Tools is installed.  For every 60 minutes that pass, the clock is about 5 minutes behind.  So in about 12 hours, it'll be an entire hour behind the real time.

I'm trying to get the clock to sync automatically, but am having no luck.

ntpdate is installed, and it works if I run it manually with sudo (sudo ntpdate ntp.ubuntu.com).  However, the _[Ubuntu docs indicate]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/NTP.html")_ that if I add it to a cron file, I can automate it.

I added this line to /etc/cron.hourly/ntpdate as noted in the link above (the link says to add things to /etc/cron.daily/ntpdate instead, but I need this to run hourly rather than daily due to the time-lag caused by virtualization):

```
ntpdate ntp.ubuntu.com
```

That fails to do anything every hour, and I can't seem to figure out why.  I attempted creating the file, and then running "sudo crontab ntpdate," and even "chmod 755" the file to make it look like other cron jobs living in other /etc/cron.* directories, but nothing works.  Any clues as to what I'm doing wrong?



I've also tried installing ntp-server and ntp-simple, which run ntpd in the background.  However, they fail to change the time too.  top indicates that the daemon is running, but it just never does a thing with the clock.

I honestly don't care whether this is implemented through ntpdate or ntp-server.  Whichever works.  And yes, I uninstall ntp-simple and ntp-server whenever I attempt to do anything with ntpdate, as I know ntpdate won't work if the simple/server variants are installed.

I've had ntpd running just fine on a Gentoo box before.  I'm not sure if that's because I built the entire system through a root account rather than the Ubuntu-way which keeps you locked out of root for security measures.  Ta and thanks!  :D

---

### Post by acormack on 2007-04-15
Dave

This sounds like a very interesting problem.  I have never heard of a computer losing anything like 5 minutes in every hour  before.

If I were you I would try to find out why the time is drifting so much.  It almost sounds like there is a timezone mismatch (between windows and LINUX) and that one or more of vmware / ntp-server / ntp-simple daemon is attempting to gradually synchronise the LINUX clock.

Have you tried disabling vmware tools and the synchronise time option in vmware?  If you do this and set the time in LINUX does it strill lose 5 minutes an hour?

you could check how much drift occurs using the ntpdate -q option to just query the time rather than set it e.g. create a script something like this and run it for an hour


#!/bin/bash
while true
do
        sudo ntpdate -q ntp.ubuntu.com
        sleep 60
done

This will query the ntp server and report (but not change) the current time every 60 seconds.  This should give you a better idea about how the 5 minute error occurs.

Here is the output if I run this on my PC

server 82.211.81.145, stratum 2, offset -0.034260, delay 0.06918
15 Apr 09:38:58 ntpdate[6661]: adjust time server 82.211.81.145 offset -0.034260 sec
server 82.211.81.145, stratum 2, offset -0.062804, delay 0.11870
15 Apr 09:39:59 ntpdate[6663]: adjust time server 82.211.81.145 offset -0.062804 sec


Alec

---

### Post by dave-gallagher on 2007-04-17
Hi Alec,

Thanks for the reply, and the script!  I tried what you said but that didn't solve the problem.  However, you led me in the right direction to solve it, which I did.

I'm not sure why the ntpdate/ntp-server/ntp-simple packages, along with cron in the case of ntpdate, couldn't fix the problem, but it's fixed now the "right" way.

Time was getting out of sync simply due to the emulated BIOS in the Ubuntu VMWare Guest OS falling behind real-time.  That's pretty typical of Guest OS's in a virtualized environment.  VMWare-Tools, which is installed on the Guest OS, is suppose to fix this normally.

In my case, VMWare-Tools wasn't syncing the Ubuntu clock with my Host OS hardware clock for some reason.  To fix it, I had to edit a text file, with the .vmx extension, that lives in the same directory as my Guest OS, on the Host OS.  Changing this variable to TRUE from FALSE fixed the problem:

```
tools.syncTime = "TRUE"
```

After doing so, I rebooted the Guest OS, and time stays perfect now!  :D

Again, thanks for your help Alec, it's appreciated!

---

### Post by Macdude-StL on 2008-03-27
After reading the posts on this topic, I checked my system. Running Hardy Heron Beta in VMWare on a MacBook (OSX 10.4 Tiger) (core duo 2GHz, using single core for VM). 

I see:

tools.syncTime = "FALSE"

and under System: Administration: Time and Date, the selection is "Manual".

I do have the Mac set up to use an NTP server, but why is my VM staying in perfect sync? When I start it up, time has been lost since suspend, but the clock corrects itself by the time I get control back.

This is my first experiments with Hardy, don't remember any anomalies on previous versions. Also my first post -- your patience is appreciated.

--Don

---

