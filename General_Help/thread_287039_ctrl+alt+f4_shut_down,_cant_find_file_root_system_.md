---
title: "ctrl+alt+f4 shut down, cant find file root system on boot"
date: 2006-10-28
forum: General Help
---

### Post by romankoval on 2006-10-28
While running Ubuntu, I pressed ctrl+alt+f4 hoping it would close a current window(I think Im still stuck in the WindowsXP mindset) and it went to a black screen and restarted. Upon boot, it stopped at "checking root filesystem" and took me to another screen which said something about fsck and filesystem. I'm not totally sure what happened, but if anyone can help me from the information Ive given, that would be awesome.

-Roman

---

### Post by Tomosaur on 2006-10-28
fsck is similar to Windows' 'ChkDsk' utility. Normally, fsck runs every 30th boot, and can fix many filesystem errors on its own. However, it is possible that your problem is more serious, but without the exact error, nobody is likely to be able to help you I'm afraid.

---

### Post by DaveBorealis on 2006-10-28
Hello Roman,
Can't help you with your problem, but maybe I can give you a little direction to get started.

> **romankoval said:**
> While running Ubuntu, I pressed ctrl+alt+f4
This should have taken you to a virtual terminal with a command-line interface (all text), however it should not have rebooted your machine.

> and it went to a black screen and restarted.
Are you sure you didn't accidentally type ctrl+alt+del?
> Upon boot, it stopped at "checking root filesystem" and took me to another screen which said something about fsck and filesystem.
If it dumped you into single-user mode, then the sudden shutting down of your machine messed something up in your drive's filesystem, which ctrl-alt-del should not have done as it will cause a proper shutdown.

By any chance did you previously change your /etc/inittab file?

Best regards,
Dave

---

### Post by galileon on 2006-10-28
ctrl+alt+f4 takes you to a console

Linux has six text consoles acessed thru ctrl+alt+F1-F6, ctrl-alt-f7 gives you a graphical environment, called x-server (its the default, unless you choose to change it yourself)

if it restarted, it may be that ctrl-alt-f4 is associated with some other program, which tried to run, and that happened to crash the system...

post any error you see, or take a picture if you want to and post it here...

---

### Post by romankoval on 2006-10-28
Well Im on windows right now, and I went back to ubuntu and wrote down what was on the screen starting with that check root filesystem failure. This is what I got:

/dev/hdb2 contains a file system with errors, check forced.
/dev/hdb2:
Inode 1524689 has illegal block(s)
/dev/hdb2:Unexpected Inconsistency:
RUN FSCK manually. (ie. without -a or -p options)
*An automatic file system check of the root filesystem failed.
*A manual fsck must be performed, then the system rebooted.
*This fsck can be performed in maintenance mode.
*Please note  that this root filesystem is currently mounted read-only.
*The fsck should only be performed while the root filesystem is mounted read-only. However, the command to remount it read-write is: # mount -n -o remount, rw/
*In order to exit from the maintenance shell, press control D and the system will reboot.
bash: groups: command not found
bash: lerspipe: command not found
bash: dircolors: command not found
root@roman-desktop:~#_

If this clears up my problem, Id like some help.

---

### Post by galileon on 2006-10-28
ahhh do the fsck then, something along the lines 

fsck /dev/hdb2 <----------check it in the man fsck if it doesnt work

but be aware that it might mean some files might get lost during the proces, so if theres important stuff, try to backup it first using a live cd..

---

