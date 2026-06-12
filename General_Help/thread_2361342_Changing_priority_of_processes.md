---
title: "Changing priority of processes"
date: 2017-05-15
forum: General Help
---

### Post by penman131 on 2017-05-15
Hello
I would like to know how to permanently change the priority of a process. The reason for asking is that when I open the system monitor, the pulseaudio process is set at a very high priority. Since the rest of the running processes are either "normal" or lower, I am curious as to why pulseaudio should be set to "very high". I can set it to normal but after a reboot, it reverts to very high.

p

---

### Post by TheFu on 2017-05-15
I don't know how to change it at startup.  It is probably that way to avoid stuttering of audio.
Priorities in Linux range from +19 to -20.  I don't know what "very high" translates into.  Anything above 0, requires root to force.  Users can use the **renice** tool to modify their process priority between 0 and -20 (or is it positive?).  I always get the +/- mixed up.

```
RENICE(1)                        User Commands                       RENICE(1)

NAME
       renice - alter priority of running processes

SYNOPSIS
       renice [-n] priority [-g|-p|-u] identifier...

DESCRIPTION
       renice alters the scheduling priority of one or more running processes.
       The first argument is the priority value to be used.  The  other ...

SEE ALSO
       nice(1), getpriority(2), setpriority(2)

BUGS
       Non-superusers  cannot increase scheduling priorities of their own pro-
       cesses, even if they were the ones that decreased the priorities in the
       first place.
```

The manpage says users can reduce the priority of their process, but due to a bug, they cannot increase the priority of previously reduced processes.

Ok, moving on ... systemd stuff is spelled out here: [https://www.freedesktop.org/software/systemd/man/systemd.exec.html](https://www.freedesktop.org/software/systemd/man/systemd.exec.html)
```
Nice=

    Sets the default nice level (scheduling priority) for executed processes. Takes an integer 
    between -20 (highest priority) and 19 (lowest priority). See setpriority(2) for details.
```
So you just need to find the systemd startup for pulse audio and find the 'Nice=' option in that text file.

I searched under /etc/systemd/ and didn't find any file with 'pulse' in the name or inside the files there. Dead end, this time.

Ok, moving on ... pulse on my frankenstein 16.04 system has settings in /etc/pulse/
/etc/pulse/more daemon.conf 
Inside that file is the settings showing default values for scheduling (they are commented out):
```
; high-priority = yes
; nice-level = -11

```
Looking at the process table using 'top', I see

```
2634 thefu         9 -11  418840  11528   8092 S   0.0  0.3   0:00.24 pulseaudio 

```
with the '-11' in the priority column.  So, I'm fairly certain that changing that file and restarting the daemon/system will alter the priority for pulse.

Thanks for helping me to learn more about this. ;) Hopefully the steps I've taken is helpful (how to fish) for other running into similar, but not the same issue.

---

### Post by 1clue on 2017-05-15
Audio requires a good time source to sound good. A high priority helps assure that the job is scheduled regularly. Pulseaudio uses very little cpu time while running, meaning the task takes very little time to complete a single run, and then it's rescheduled and relinquishes the cpu in short order.

If you don't use audio on your system or don't care about playback quality, then reducing priority on pulseaudio might reduced the load on your CPU by a tiny amount, but if your system is even close to adequate you'll never notice.

---

### Post by penman131 on 2017-05-15
@TheFu thanks for the info. It worked like a charm... just did a gedit on daemon.conf rebooted and it's now running at normal priority.

@1clue I think I'll leave it at normal and if I get any audio issues, then I'll put it back.

TNX

P

---

### Post by TheFu on 2017-05-15
Please be VERY careful using *sudo gedit*.  Sometimes there are unexpected side effects.  Better to use '**sudoedit**' which is always safe. You can use gedit with sudoedit, if you like. Just add **export EDITOR=gedit** to your .profile or .bashrc or whatever other init file your shell uses. Much safer.

Sometimes pulseaudio breaks and does funky things.  I've seen it use 200% of CPU and I've seen it crash because a different application wanted to play some sounds. I used to purge it from my systems as part of setup, but now that Firefox only supports pulse for sound, don't have that option anymore, if I want sound from firefox.

If this is solved, please mark the thread solved to help everyone in the community.

---

### Post by 1clue on 2017-05-15
> **TheFu said:**
> ...Sometimes pulseaudio breaks and does funky things...

I wasn't going to say anything. I personally can't understand why people still use it.

---

### Post by oldos2er on 2017-05-15
Moved to *General Help*.

---

