---
title: "Detaching processes from getting killed when X dies"
date: 2018-11-27
forum: General Help
---

### Post by ogilvierothchild on 2018-11-27
Hi,

In the past, I have used GNU screen(1) to shield long-running processes from the X server dying.

Now however, using Ubuntu 18.04 with lightdm/gdm, and Gnome/MATE/XFCE, this doesn't work.  When restarting X using "sudo /etc/init.d/lightdm restart" from a virtual console, this kills any process that was started through X.  So upon restarting X, for example, running "screen -d  -r" says there's no screen to connect to.

This behavior isn't limited to screen, also things like FUSE-mounted filesystems die when restarting X.

I often run long-running processes, like simulations, media analysis programs, or bulk copying to remote computers, that need to stay up even if the windowing system fails.  For some programs, I use nohup and disown, but processes that daemonize themselves are common also, and for interactive processes the canonical approach has been to use screen or tmux to ensure their survival. 

How can I create processes that survive the destruction of the underlying X server?

--------

To reproduce:

1. In an X session terminal emulator (e.g. "gnome-terminal") run "screen"

2. Switch to a virtual console terminal, e.g. by pressing ctrl-alt-F1, login and type "sudo /etc/init.d/lightdm restart"

3. Log in again to X, open a terminal application, and type "screen -d -r"

Expected result: the still-running screen process re-attaches to the current terminal.

Observed result: the screen process has been killed.

---------

Any suggestions for how I should execute long-running processes would be greatly appreciated.

Also, since things like "ps" and "pstree" show that daemonized processes take systemd as their parent, there is obviously some newer association being used to link these deamonized processes with the X server.   Any insight as to what is going on would also be very much appreciated.

Thanks!

---

### Post by HermanAB on 2018-11-27
I believe that you can thank a certain Mr Poetering for that improvement.

You should try Slackware or OpenBSD if you want a real computer system.

---

### Post by Skaperen on 2018-11-27
try this:  start the screen session at the virtual console terminal (ctrl-alt-F1).  then, leaving it at a shell prompt, detach it.  then, in X running a terminal window, attach to that detached screen session.  start your long running program (or just "sleep 99999" for testing).  restart X like you have before.  does it go away even in this case?

---

### Post by ogilvierothchild on 2018-11-29
That works -- the question is, how to detach subprocesses from the X server?

Thanks!

---

### Post by 1clue on 2018-11-29
I need to know this too. Mr. Poettering seems to have a knack for "improving" Linux in exactly the way it does not need to be improved.

---

### Post by ogilvierothchild on 2018-11-30
Some related links[INDENT][URL="https://github.com/tmux/tmux/issues/1307"]
https://github.com/tmux/tmux/issues/1307[/URL]

[https://www.reddit.com/r/programming/comments/4ldewx/systemd_kills_screen_and_tmux_by_default_on_logout/](https://www.reddit.com/r/programming/comments/4ldewx/systemd_kills_screen_and_tmux_by_default_on_logout/)

[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=825394](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=825394) .
[/INDENT]

It seems the solution is to either reconfigure systemd (specifically, the "KillUserProcesses" flag), or to run long-lived processes as:[INDENT][FONT=courier new][COLOR=#1C1C1C]
systemd-run --scope your_long_lived_process[/COLOR][/FONT][/INDENT]

or maybe[INDENT][FONT=courier new][COLOR=#1C1C1C]
systemd-run --scope --user your_long_lived_process[/COLOR][/FONT][/INDENT]

then it should work.

And yes, this is the work of this Poettering character, since the main reason this was done by default is because a few X processes couldn't bother to sort themselves out on exit, such as PulseAudio (written by Poettering) and perhaps settings daemons and dconf daemons.  Note I haven't tested the solution, but when I FUSE mount a remote ssh or S3 filesystem, or run something in screen, I'll give this a shot and report back here.  Typically this only matters when I'm working on some visualization or GPGPU program that does something bad to OpenGL and I cause X to crash or lock-up.

---

### Post by ogilvierothchild on 2018-11-30
Ok, yes it worked.

The form that succeeded is:

[INDENT][FONT=courier new]systemd-run --scope screen[/FONT][/INDENT]


For some reason on the first invocation all the sub-processes died (e.g. the inner shell survived, but vim processes crashed with an ICE error), but the 2nd and 3rd tries worked fine.

It forces you to type your password, which I would like to disable somehow.

---

### Post by 1clue on 2018-11-30
> **ogilvierothchild said:**
> ...And yes, this is the work of this Poettering character, since the main reason this was done by default is because a few X processes couldn't bother to sort themselves out on exit, such as PulseAudio (written by Poettering)...

I would ask why he didn't just go fix pulseaudio, but it was broken from the beginning. It's one of the first things I remove when I install a new Linux.

> **ogilvierothchild said:**
> Ok, yes it worked.

The form that succeeded is:
[INDENT][FONT=courier new]systemd-run --scope screen[/FONT]
[/INDENT]


For some reason on the first invocation all the sub-processes died (e.g. the inner shell survived, but vim processes crashed with an ICE error), but the 2nd and 3rd tries worked fine.

It forces you to type your password, which I would like to disable somehow.

I'll have to try it out.

By "first invocation" what exactly do you mean? You tried it, logged out, everything died and then logged back in again to try a 2nd and 3rd time?

---

### Post by ogilvierothchild on 2018-11-30
I mean that the first time I tried using the systemd-run command, the screen session survived, as did the subshells created by screen, but 4 separate instances of vim died, each with some kind of "ICE" error.  Each pseudo-terminal in screen that was running vim was dropped to the shell prompt in raw mode, meaning I had to type "reset" to use the terminal normally.  

After that, at some point I rebooted, due to a hard-lockup of X or the whole system (from a bad GLSL program I was debugging) which wouldn't let me switch to a VT.  After the reboot, I tried systemd-run again and it seemed to work fine.

I'm not happy with having to retype my password every time I launch screen, or mount a remote FUSE filesystem, etc.

Suggestions on how to enable permissions to be set such that I don't need to re-authenticate on each invocation of "systemd-run --scope" would be greatly appreciated.

---

### Post by 1clue on 2018-11-30
Thanks for the clarification and the research.

WRT the password, All I can think of would be the forbidden /etc/sudoers magic. Personally I'd rather type the password than create a hack like that.

---

