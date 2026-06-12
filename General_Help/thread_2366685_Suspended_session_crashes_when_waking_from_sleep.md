---
title: "Suspended session crashes when waking from sleep"
date: 2017-07-20
forum: General Help
---

### Post by dewdrop_world on 2017-07-20
So, I'm about a week on Ubuntu Studio 16.04 (after about seven years on a few versions of plain Ubuntu).

A problem I haven't seen before: Sporadically, when I wake the computer from a suspended session, it looks like the existing session crashes and the window manager restarts. That is:


[LIST]
[*]Normally, wake-from-sleep displays the password prompt within a couple of seconds.
[*]When the problem occurs, it takes about 10 seconds to get the password prompt. During that time, the screen reverts briefly to the boot-up console. After logging in, all of the open windows from the suspended session are gone.
[/LIST]

The system doesn't freeze and I don't have to do a hard reboot -- which is helpful, but then I have to start over reopening apps (and Linus help me if I forgot to save something).

(Note, this is Ubuntu Studio -- the window manager is xcfe4 and *not* Unity.)

What should I check, next time I see this problem?

$ uname -a
Linux dlm-E431 4.8.0-58-lowlatency #63~16.04.1-Ubuntu SMP PREEMPT Mon Jun 26 19:54:15 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

ThinkPad Edge E431.

TIA,
James

---

### Post by BenginM on 2017-07-20
Salutations!

you might want to check the logs in /var/logs , specifically apport logs and kern.l 

what is the suspend setting you set in system settings , as in , are you suspending to 

(suspend-to-idle)

suspend-to-RAM

or 

(hibernate-to-disk)

is this on a desktop or a laptop .. you might want to run tail -f /var/log/syslog  in a terminal window before the suspend and catch live logs ..

also , what is the swap status , is it ON, and used!

$ swapon -s

---

### Post by dewdrop_world on 2017-07-22
Thanks for the tips. I've saved them locally, and if I see the problem again, I will check those logs.

No issue in the last couple of days. One difference is that I installed a script to reset the network manager when waking from sleep[1] -- so, if I go for the next couple of weeks or so and I don't see the problem, then I'd be willing to conclude that the network manager failure was causing the session to go down. (Mental note, I should mark this thread closed in that case.)

hjh

[1] [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1585863/comments/40](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1585863/comments/40)

---

### Post by dewdrop_world on 2017-07-22
PS Swap space might be slightly small for a 4GB RAM machine, but I avoid suspending with lots of apps open. Shouldn't be high memory use when I suspend.

$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda6                                  partition    2927612    0    -1

---

### Post by dewdrop_world on 2017-07-22
Well. Coincidentally enough, it just happened again.

syslog says:

```
Jul 22 11:59:45 dlm-E431 kernel: [   93.675817] [drm] GPU HANG: ecode 7:0:0x86ffbff9, in Xorg [1195], reason: Hang on render ring, action: reset
Jul 22 11:59:45 dlm-E431 kernel: [   93.675818] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
Jul 22 11:59:45 dlm-E431 kernel: [   93.675819] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
Jul 22 11:59:45 dlm-E431 kernel: [   93.675819] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
Jul 22 11:59:45 dlm-E431 kernel: [   93.675819] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
Jul 22 11:59:45 dlm-E431 kernel: [   93.675820] [drm] GPU crash dump saved to /sys/class/drm/card0/error
Jul 22 11:59:45 dlm-E431 kernel: [   93.675867] drm/i915: Resetting chip after gpu hang
```

That looks suspicious. "Please file a _new_ bug report" -- I'll do that later.

James

---

### Post by dewdrop_world on 2017-07-22
Update: I logged the bug, and they came back to say that it's already fixed in kernel 4.9 and later. So I checked the software updater, and indeed, an update to kernel 4.10.something is available. (I don't know why it didn't invite me to do the update already.)

Anyway, I bet that will take care of it, so I'll mark this topic closed.

James

---

