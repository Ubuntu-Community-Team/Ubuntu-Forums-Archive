---
title: "Error Message After Trying to Edit /etc/default/rcS"
date: 2017-02-18
forum: General Help
---

### Post by John_Patrick_Mason on 2017-02-18
I'm getting an error message after trying to edit /etc/default/rcS to set the time on my Ubuntu partition to local time.
I've been following these instructions: [https://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot](https://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot) but for some reason I think I made a mistake. Could somebody help me? 


E325: ATTENTION
Found a swap file by the name "/etc/default/.rcS.swp"
owned by: root dated: Sun Feb 12 19:48:41 2017
file name: /etc/default/rcS
modified: YES
user name: root host name: Ubuntu-Laptop
process ID: 4424
While opening file "/etc/default/rcS"
dated: Fri Jan 20 17:57:36 2017

(1) Another program may be editing the same file. If this is the case,
be careful not to end up with two different instances of the same
file when making changes. Quit, or continue with caution.
(2) An edit session for this file crashed.
If this is the case, use ":recover" or "vim -r /etc/default/rcS"
to recover the changes (see ":help recovery").
If you did this already, delete the swap file "/etc/default/.rcS.swp"
to avoid this message.

---

### Post by Keith_Helms on 2017-02-18
What is in the rcS file now?  Does it look like it did when you tried to edit it?  If so, delete the .rcS.swp file and try again.

---

### Post by oldos2er on 2017-02-18
Which version of Ubuntu are you running?

---

### Post by John_Patrick_Mason on 2017-02-18
> **Keith_Helms said:**
> What is in the rcS file now?

```
#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

# delete files in /tmp during boot older than x days.
# '0' means always, -1 or 'infinite' disables the feature
#TMPTIME=0

# spawn sulogin during boot, continue normal boot if not used in 30 seconds
#SULOGIN=no

# do not allow users to log in until the boot has completed
#DELAYLOGIN=no

# be more verbose during the boot process
#VERBOSE=no

# automatically repair filesystems with inconsistencies during boot
#FSCKFIX=no
```

Do the contents of the file look normal to you?

I also found three swap files under the same file name:

```

-rw-r--r--   1 root root 12288 Feb 12 20:05 .rcS.swn
-rw-r--r--   1 root root 12288 Feb 12 19:51 .rcS.swo
-rw-r--r--   1 root root 12288 Feb 12 19:48 .rcS.swp

```

Can I safely delete the three files?

> [INDENT]Which version of Ubuntu are you running?                   
[/INDENT]
 

16.04

---

### Post by Keith_Helms on 2017-02-18
Yes that looks like what's in the rcS file on my system.  How did you get 3 swap files?  Did you make multiple attempts to edit the file and they all crashed?   You can delete them.

---

### Post by John_Patrick_Mason on 2017-02-18
> How did you get 3 swap files?

While I've come a long way with the command line, the truth is, I don't really have the skills to edit text files, yet. I was just trying to set the time on my Ubuntu partition to local time, so that next time, when I decide to boot into my Windows partition, I don't have to deal with a clock that's five hours ahead. I was really just looking for a quick online solution. I figured the keyboard commands would be the same with the less program, up/down arrow left/right arrow, guess I was wrong.

---

### Post by Impavidus on 2017-02-19
It seems you tried editing the file with vim. vim makes a swap file for recovery if the editor crashes or is killed. Maybe you killed vim instead of properly saving and closing? To properly save a file and close vim, use **:wq** or **ZZ**. To close without saving changes, use **:q!**. I suggest you search for a vim quick reference card and, later maybe, the Vimbook. It's not an easy editor to learn, but when you get used to it, it's very good.

Your /etc/default/rcS is empty, in the sense that all lines are commented out. This is how it should be by default on 16.04. No changes were ever saved. You can safely remove the swap files.

On 16.04, changing /etc/default/rcS is no longer the right way to solve this time zone problem. This is, I believe, because of the change to systemd. See this thread: [https://ubuntuforums.org/showthread.php?t=2321876](https://ubuntuforums.org/showthread.php?t=2321876)

---

### Post by oldos2er on 2017-02-19
@John_Patrick_Mason, you might find the nano editor a bit easier to use. 

[https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

---

### Post by John_Patrick_Mason on 2017-02-19
> On 16.04, changing /etc/default/rcS is no longer the right way to solve  this time zone problem. This is, I believe, because of the change to  systemd. See this thread:

You're right. The link you provided solved the problem. I also deleted the swap files as suggested by others, which got rid of the error issue. Thanks a bunch.

---

