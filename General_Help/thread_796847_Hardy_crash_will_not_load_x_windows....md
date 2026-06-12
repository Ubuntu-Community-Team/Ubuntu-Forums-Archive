---
title: "Hardy crash will not load x windows..."
date: 2008-05-16
forum: General Help
---

### Post by Blakstar26 on 2008-05-16
after a crash and reboot, x windows will no longer load and instead leaves me with...

> 
/dev/sda5: Unattached inode 3375457



/dev/sda5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
fsck died with exit status 4
Checking drive /dev/sda5: 94% (stage 4/5, 206/308
								[fail]
 * An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
THe fsck should be performed in maintenance mode with the 
root filesystem mounted in read only mode.
 * The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@<username>-desktop:`#


Any suggestions on fixing problem?

---

### Post by Blakstar26 on 2008-05-16
bump. :guitar:

---

### Post by rlcomstock3 on 2008-05-16
It looks like you have a hard drive data integrity problem to me.  I would run the command it suggests.  Check google on recovering whatever file system you have.

---

### Post by Blakstar26 on 2008-05-16
I did. I ran the command and it stops at 94% and gives me the same error.

---

### Post by kloy1334 on 2008-05-16
I am receiving the same problem. Did not install any software lately manually to have caused this. Just downloaded all of the updates Ubuntu was pushing on me.

Any solutions as of yet?

EDIT:
Ran fsck, it's all good now.
Thanks for being there, Ubuntu community.
I'll come back if something else occurs.
Still don't know why this happened though.

---

### Post by Blakstar26 on 2008-05-17
Problem solved!

Manually running fsck would stop at 94% then crash. I solved this by running the live cd, un-mounting the partition and then running fsck manually with the suggested command in this thread [HERE]("http://ubuntuforums.org/showthread.php?t=546258"). When the disk check was complete and repaired, X windows ran as normal after reboot.

Thank you all for your suggestions and input.

---

