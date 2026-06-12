---
title: "Log shutdown event"
date: 2017-02-03
forum: General Help
---

### Post by Dr_Lion on 2017-02-03
I'm trying to log when i computer is shutdown properly, or from the other side, check when it goes down by energy failure.

I've searched some tuturials on the net, and i thought the best option would be to create some script on rcX.d dirs. I've tried on rc0.d and rc6.d but surprisingly i got nothing.

Or it simply doesnt work this way, or i'm doing something wrong, maybe with permissions, or the comand itself, i dont know... I tried to write to /home/username/, i tried, /tmp/, with the full path and with relative one. Nothing... I'm using a command line script, i even checked all permissions, being user and group root, and nothing. 

Anyone can pinpoint me in the right direction? This shlould be something easy, but it makes me frustrated, when i have to do something when starting up or shutting down, because its simply a main pita to write a simple log line.

---

### Post by DuckHook on 2017-02-04
Think carefully for a moment about what you are actually asking.

Shutdown is not an *event*. It is a *process* comprised of a *succession* of events whereby the system methodically and systematically winds down services, elegantly terminates processes, unmounts disks and disconnects from peripherals. The only "event" that approximates what might be considered a "shutdown" would be the final acpi call to the BIOS to power off. By then, the disks have been unmounted and the logging service is long gone. How, exactly, is the system supposed to "record" that?

Similarly, in the event of an energy failure, the system will die as if its plug was pulled. How can it possibly "record" such an event??? Yes, computers have come a long way, but they are not yet prescient.

BTW, some of the processes that comprise an elegant shutdown are already logged. In syslog. If you *tail* syslog.1 you will likely see a flurry of "stop" events, at least until the logging daemon, *rsyslogd*, itself gets stopped. But any one of these events could happen for other reasons, such as the admin issuing a stop command to the service in question. A computer cannot tell *why* something happened; just that it *did* happen. Ergo, it can't record a "shutdown". As for the energy failure scenario&#8213;if you come up with a way to log that, you'll earn a place in the history books and probably get a Nobel prize.

---

### Post by Dr_Lion on 2017-02-06
Well, after i red your post carefully let me clarify some points. I'm not trying to earn nothing, nor a Nobel nor history, and i'm not trying to get PCs to guess. 

My question has a reason, and it is because i cant find a single and only "stop", on my log files namely: alternatives.log, alternatives.log.1, auth.log, boot.log, dmesg, dmesg.0, dpkg.log, dpkg.log.1, faillog, kern.log, lastlog, syslog, syslog.1, ufw.log, wtmp, wtmp.1, Xorg.0.log, Xorg.0.log.old checked myself now.

I know shutdown is a complex process, with a lot of steps, so lets put it simply: It might not be the most accurate way, it might not be the proper way, but to detect energy failure or badly turned off for me, i only need to know when the user click the shutdown or reboot button. So plain and simple, i only want to write one line on a text file saying: "user pressed shutdown button". After that i write another line to the file when computer starts/restarts and if i get the same line twice i know something has occurred meanwhile!

It leads me as you said shutdown is not an event, but a mouse click, or a keypress is, and all im trying here is to try to detect it.

As i see you understand this subject could you please help and enlight me how to write a simple text line, can be to /tmp dir, or any other you might think the better, in or out the user directory. 

Thanks DuckHook

---

### Post by dragonfly41 on 2017-02-06
So you want to detect when the user clicks shutdown button ... and not a random power glitch ...
Will this idea help you ..  
[http://askubuntu.com/questions/473693/run-a-script-when-power-button-is-pushed](http://askubuntu.com/questions/473693/run-a-script-when-power-button-is-pushed)

---

### Post by DuckHook on 2017-02-06
You are correct that the system does not record events like use of the "stop" button in the GUI. It seems to me that any system that does so would need to add something akin to keylogging, and this would raise far larger concerns than the issue you are trying to solve.

This is made more complicated by the fact that there are many ways to shut down a system. I often bypass the GUI altogether and use the command line with a simple "reboot", "poweroff" or "shutdown -P now", so capturing clicks of the GUI stop button would not even work in my case.

There are also the sysrq functions <Sysrq>+<B> and <Sysrq>+<O> which bypass even the void-kernel shutdown functions.

There are probably even more ways that I am not aware of.

What this means is that a userland method will not catch everything. You need a system-level function that traps shutdown events at a very basic level. @dragonfly41 gives you a useful link. The easiest method that might work for you is the last post in that thread: adding your script call into */etc/acpi/powerbtn.sh*   Even then, I do not believe that this would capture the sysrq methods, but they are rarely used and usually only for emergencies, so may not be a concern to you.

Your script could simply echo "Controlled shutdown on:" then *date -u* then >> to a file of your choice. I'm not very good with scripts and hopeless with coding, so will not risk leading you astray with an attempt at one.

You should be alerted to the danger that fiddling with low level system events like this could break your system. They can also lead to nasty unintended consequences like data corruption. But if you have a need for this, back up your data religiously and do proper testing, then I suppose any possible risk can be mitigated.

The big problem in your scenario, as I see it, is that you still can't log a sudden power loss. This is just physically impossible. I suppose you could point a battery powered video camera at your computer that timestamps frame by frame. Or you could hitch a UPS to your machine which keeps it running and *will* log blackouts and brownouts, but the first is an external monitoring tool and the second isn't really a power-off.

My understanding of your original question was that it wasn't the actual controlled shutdown that interested you, but distinguishing between controlled versus sudden power loss. Knowing only one side of that equation won't give you that distinction.

---

### Post by Dr_Lion on 2017-02-07
I understood that i've not been clear, no problem. When i refer power outage it was an example. Yes, i'm save cause i always use a test machine, but sometimes its impossible to change some options when directions were already taken. 

Im a bit sad because, the "i thought" supposed easy way "acpi" dragon pointed out there is not on my system.. 

So i tried the to put a script on /etc/init.d/  and create a link on /etc/rc0.d and /etc/rc6.d  but i'm having some troubles here! First time i did update-rc and it was writing to file yes, but!! it would only write once, and it means, it wasnt appending i would like, but was rewritging the file! 

And anothter issue that i face is, it only writes the file, when the link is on /etc/rc2.d!!!   I put the links on  /etc/rc0.d and /etc/rc6.d  and the script doesnt write to file. I created the shortcuts as K20scriptname and S20scriptname. I will try some more times to see if i can get any conclusion.

For last, when you talk about sysrq, what action does that represents?  Is there a way that you are aware of of detecting the shutdown when user presses one time the power button on the pc?

Thanks for your time.

---

### Post by Dr_Lion on 2017-02-09
Well, i did it, and im ashamed!!

It was working all from the begining, but i did one giant mistake, it makes me feel worst than a newbie, a completely noob. I was writing the file to /tmp, and tmp dir is as it says tmp; means it is erased on ever single time pc is shutdown/rebooted.

So everything was working well, but i only could see the log when it booted. Mistery solved.

It is very easy ti do this, just create a script on /etc/init./d and create shortcuts on /etc/rcX-d/ where X is the runlevel you want to log; usualy 0 to shutdown, 6 to restart and 2 to run.... You can check your runing level, by type runlevel in cmd!

To log the action i used a one line script

> 
#!/bin/sh
echo "$(date +"%b %e %T") Pc correctly shutdown by user"  >> /home/user/power.log
exit 0



Thanks for your time DuckHook

---

