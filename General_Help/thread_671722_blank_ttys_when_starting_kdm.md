---
title: "blank ttys when starting kdm"
date: 2008-01-18
forum: General Help
---

### Post by TeeAhr1 on 2008-01-18
This is a repost of [this thread]("http://ubuntuforums.org/showthread.php?t=667550"), which I have (obviously) not yet solved, but I've got a little more of a handle on what's going on now, so I thought I'd repost and see if I can get a reply.

This all started when I installed KDE4.  I chose to use kdm-kde4 instead of kdm, and it screwed everything up.  For a day I couldn't log in at all, until I booted to recovery mode and did a dpkg-reconfigure kdm.  The problem with the disappearing ttys has been ongoing since that time (last week).

Here's a blow-by-blow.  When I boot up, I see boot messages (I've got usplash turned off), so I know tty1 is working.  As soon as KDM starts, the screen goes to sleep for a second, then pops back up with KDM.  I can then log in to KDE normally.  However, when I press ctrl-alt-f(1-6) my monitor goes to sleep.

The gettys are running.  ps says so, and they will take input if I type blind.  Pressing ctrl-alt-f7 brings me back to X.  If I shut the machine down, the monitor goes to sleep (presumably going back to tty1).

The only other clue I have is that in my /var/log/kdm.log, I see this: "(EE) intel(0): I830 Vblank Pipe Setup Failed 0".  And that's all I know right now.  Messing around with vga= in the grub conf doesn't help, because they're coming up fine when I boot, it's not until kdm starts that something goes haywire.

Anyone able to help me with where to go next?  Thx to all, as always...

-pd-

---

### Post by TeeAhr1 on 2008-01-31
This is a test of the emergency /bump system. This is only a test. If this were an actual /bump, the link you just clicked would have been followed by vague, nondescriptive whining followed by plaintive pissing and moaning about the general state of affairs and how very unfair life is. We now continue with our regularly scheduled programming.

-pd-

---

