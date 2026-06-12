---
title: "List of upstart events?"
date: 2008-03-14
forum: General Help
---

### Post by gaspard.leon on 2008-03-14
Hi, I would like to hack around with upstart, and I have already looked at the documentation.. There is mention of events, but I was wondering where the list of the actual existing or built-in events for ubuntu?

Pointer to the correct thread or whatever would be cool.

Cheers,

Gaspard

---

### Post by SpaceTeddy on 2008-03-14
google: "linux runlevel howto"
[http://www.cyberciti.biz/faq/howto-runlevel-configuration-tool-to-start-service/]("http://www.cyberciti.biz/faq/howto-runlevel-configuration-tool-to-start-service/")

for redhat but holds a few interesting points at the start of the article
[http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/runlevels.htm]("http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/linux-hn/runlevels.htm")

if you have any further question, ask - i was just to lazy to explain myself :)

---

### Post by gaspard.leon on 2008-03-15
to be specific my question was not about run levels... but upstart **events**

I had a look at the first link you posted...

the second link was blocked by my firefox... something about badware...

All I really want is a list of the existing built in events... perhaps I'm asking in the wrong forum?
:confused:

---

### Post by SpaceTeddy on 2008-03-15
ok, then i probably do not understand what you mean by startup-events. 
i *thought* you mean the services and programms that run at start, which are specified in the runlevels... if that is not the question, then what do you mean by events ?

---

### Post by kerry_s on 2008-03-15
upstart is just a different way of using run levels. the main programs are in /etc/init.d.

---

### Post by gaspard.leon on 2008-03-16
i have inspected the "Jobs" (see [http://upstart.ubuntu.com/getting-started.html]("http://upstart.ubuntu.com/getting-started.html")) in /etc/events.d ...

these have some clues to answering my question...

Basically in an upstart "Job" you can specify things like:

"start on [event]"
"stop on [event]"

just wondering where I can get a list of those [event] keywords... there are runlevel ones, and I saw one called control-alt-delete...

just interested to know what other built-in events are available.

Cheers,

Gaspard

---

### Post by SpaceTeddy on 2008-03-16
i didn't know they existied, and i have never used them so far... sorry to have confused that . i really cannot help there...

---

### Post by kerry_s on 2008-03-16
no idea, i use debian, which still uses the old style inittab. i'll post that so you can see the function's upstart now does for those, might give you a clue.
also, have you checked if there's a manpage for upstart? (man upstart)

```
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/rungetty tty1 --autologin user
2:23:respawn:/sbin/getty 38400 tty2
#3:23:respawn:/sbin/getty 38400 tty3
#4:23:respawn:/sbin/getty 38400 tty4
#5:23:respawn:/sbin/getty 38400 tty5
#6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3


```

---

### Post by gaspard.leon on 2008-03-16
thanks kerry I'll have a look and see if the man pages have anything.. when I get home.

I vaguely remember looking at the man page before, but I'll check it again..

I think eventually I will just have a poke around the source code... heh

gotta love open-source.

---

### Post by OmegaBLK on 2008-04-06
Looking for a list of Upstart events myself.  Doesn't really seem to be any good documentation to help those that want to create custom Upstart scripts right now, and the files in the /etc/event.d/ don't really help to much in regards to what the other possible events are.  If anyone finds something please share.

---

### Post by gaspard.leon on 2008-04-07
ok basic events are as expected...

I downloaded the source code, and looking in the file [FONT="monospace"]upstart-0.3.9/init/event.h[/FONT] which revealed the following list:

```


/**
 * STARTUP_EVENT:
 *
 * Name of the event that we generate when init is first executed.
 **/
#define STARTUP_EVENT "startup"

/**
 * STALLED_EVENT:
 *
 * Name of the event that we generate if the system stalls (all jobs are
 * stopped/waiting)
 **/
#define STALLED_EVENT "stalled"

/**
 * CTRLALTDEL_EVENT:
 *
 * Name of the event that we generate when the Control-Alt-Delete key
 * combination is pressed.
 **/
#define CTRLALTDEL_EVENT "control-alt-delete"

/**
 * KBDREQUEST_EVENT:
 *
 * Name of the event that we generate when the Alt-UpArrow key combination
 * is pressed.
 **/
#define KBDREQUEST_EVENT "kbdrequest"

/**
 * PWRSTATUS_EVENT:
 *
 * Name of the event that we generate when we receive SIGPWR, indicating
 * that the power status has changed.
 **/
#define PWRSTATUS_EVENT "power-status-changed"


/**
 * JOB_STARTING_EVENT:
 *
 * Name of the event we generate when we're ready to start a job; the job
 * is not actually started until the handling of this event finishes.
 **/
#define JOB_STARTING_EVENT "starting"

/**
 * JOB_STARTED_EVENT:
 *
 * Name of the event we generate once a job has been started and is now
 * running.  This is not generated until the spawned pid is located (if
 * appropriate) and the post-start script has finished.
 **/
#define JOB_STARTED_EVENT "started"

/**
 * JOB_STOPPING_EVENT:
 *
 * Name of the event we generate when we're ready to stop a job, which
 * includes arguments and environment indicating whether the job failed.
 * This is run after the pre-stop script has finished without setting the
 * goal back to start.  The job is not actually stopped until the handling
 * of this event finishes.
 **/
#define JOB_STOPPING_EVENT "stopping"

/**
 * JOB_STOPPED_EVENT:
 *
 * Name of the event we generate once a job has been stopped and is now
 * waiting.
 **/
#define JOB_STOPPED_EVENT "stopped"


```

hope it helps.

---

### Post by OmegaBLK on 2008-04-08
Ah, should have checked the header file(s).  Thanks.  Kinda sparse, was hoping that there were more events available, but I guess upstart is still a work-in-progress and additional events will be added in the future.

---

### Post by bodhi.zazen on 2008-04-08
Ubuntu uses upstart for booting and emulates system V start scripts for backwards compatibility.

FYI ~ I found a nice review of upstart a few weeks ago here :

[http://www.linux.com/feature/125977](http://www.linux.com/feature/125977)

After reading and writing a few events I have a better understanding of upstart.

---

### Post by gaspard.leon on 2008-04-08
hmm interesting... I'm reading the review now... just noticed the following:

> ...entering runlevel 2 triggers the runlevel 2 event, and a filesystem being mounted triggers the **path-mounted** event. Removing and installing...

I didn't see the path-mounted event in the basic header, so perhaps that's part of another package.. which brings me back to the question at hand:

A list of events is... where?

Well maybe I can start compiling all the different references to events found around the internet and we can test if they work or whatever and make a more complete list...

---

### Post by gaspard.leon on 2008-04-08
slightly unrelated, but check the re-written upstart startup post at [http://ubuntuforums.org/showthread.php?t=727224](http://ubuntuforums.org/showthread.php?t=727224)

---

### Post by bodhi.zazen on 2008-04-08
Hmmm ...

There is a nice discussion of events here :

[http://www.netsplit.com/2006/09/01/upstart-can-now-replace-sysvinit/](http://www.netsplit.com/2006/09/01/upstart-can-now-replace-sysvinit/)

Hope that helps.

---

### Post by Manslen on 2008-06-14
Is there any way to have a "debugging mode" for upstart? e.g. have all upstart events written to a log file.

EDIT: 
initctl can trace events:
```
sudo initctl events
```
However, trying to plug and unplug a USB mass storage device I got no event. Emitting an event using initctl emit shows correctly.

---

### Post by deci on 2008-06-14
I got another question ... how can I let scripts autostart when my linux starts ?

---

