---
title: "GUI non-functioning"
date: 2007-01-07
forum: General Help
---

### Post by echomikeromeo on 2007-01-07
I'm running Ubuntu v. 6.10 (Edgy) on a six-year-old Dell laptop. All of a sudden (without me having changed any code or anything like that) the GUI seems to have stopped working. The OS boots as normal, but instead of getting the screen asking for username and password, I get an error message which reads "Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected."

Upon pressing enter the following comes up on my screen, in white plain text on black:

```

syslogd: /var/log/news.crit: Read-only file system
syslogd: /var/log/news.err: Read-only file system
syslogd: /var/log/news/news.notice: Read-only file system
syslogd: /var/log/debug: Read-only file system
syslogd: /var/log/messages: Read-only file system
Error reading block 1406454 (Attempt to read block from filesystem resulted in short read).

/dev/hda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options
fsck died with exit status 4

* An automatic file system check (fsck of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: dircolors: command not found

```

I then am left with a command prompt, but because I'm a total noob I have no idea what to do. Someone suggested to me that the OS might somehow be running in "simple" mode, but I don't really understand what that means, how it could have happened or how to fix it. Does any one have any ideas that preferably don't involve reinstalling the entire OS?

---

### Post by Rich78 on 2007-01-07
Looks like a file system problem on the hard drive, ie It's corrupt.

At the prompt type: fsck and hit return.

Then reboot

---

### Post by echomikeromeo on 2007-01-07
Thank you very much; that seems to have fixed everything. I'm amazed to see how all that got corrupted -- I swear I didn't touch anything I shouldn't have!

---

### Post by Rich78 on 2007-01-07
Why does any hard disk get corrupt?

To be honest it may just be down to it being a laptop, they're not the most stable of beasts  (heat related).  

They're a little better nowadays.

Happy to help :)

---

