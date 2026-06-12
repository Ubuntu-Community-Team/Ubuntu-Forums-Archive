---
title: "Simple stupid resolution question"
date: 2007-10-25
forum: General Help
---

### Post by pylon42 on 2007-10-25
Is it normal for the login screen to be at a lower "default" resolution?

My desktop is at 1920x1200, but my login looks to be 1280ish, then switches when the desktop loads. Not a serious problem by any stretch of the imagination, i'm just curious if this is normal.

---

### Post by mahousaru on 2007-10-25
Could be this...

[http://ubuntuforums.org/showpost.php?p=3568252&postcount=2](http://ubuntuforums.org/showpost.php?p=3568252&postcount=2)

---

### Post by pylon42 on 2007-10-25
I understand that this is unrelated, but I made the change described in the article, rebooted and got a "kernal panic" 

I can't get the system booted, I'm typing this from my windows box.

Any ideas how I can get back up and running?

---

### Post by mahousaru on 2007-10-25
Kernel panic???  

Okay to eliminate if it is the usplash causing it, you need to disable the splash from starting.  When u reboot, press ESC to get into the boot options.  Press e to edit, move down to the line beginging with kernel, press e to edit.  Change splash to nosplash=y and press enter.

---

### Post by pylon42 on 2007-10-25
hrmm... that doesn't seem to have done anything.

I'm trying to remember any other changes I may have made before that reboot, but I'm quite certain there wasn't any.

---

### Post by pylon42 on 2007-10-25
I found this thread:
[http://ubuntuforums.org/showthread.php?t=583036&highlight=kernal+panic](http://ubuntuforums.org/showthread.php?t=583036&highlight=kernal+panic)

Think this "noapic" stuff might help?

---

### Post by mahousaru on 2007-10-25
When does it kernel panic?  Can u edit the boot options and get rid of splash and quiet so you should then see all the messages scroll up.

---

### Post by pylon42 on 2007-10-25
It says:

Using IPI No-Shortcut mode
Magic number: 11:626:690
hash matches device mem
Freeing unused kernel memory: 364k freed
Loading, please wait...
Kernel panic - not syncing: Attempted to kill init!


There was a lot more above that... but I'm typing this by hand... and I'm ashamed at the fact that i've been misspelling "kernel"

---

### Post by pylon42 on 2007-10-25
Well... that sucks. I'm just going to format and start over tonight I guess.

---

### Post by mahousaru on 2007-10-25
> **pylon42 said:**
> Well... that sucks. I'm just going to format and start over tonight I guess.

Can you try running a memory test from the live cd?  Normally a message like this is caused by hardware problems.

---

### Post by pylon42 on 2007-10-26
I'll run a memtest later today. I formatted last night and I'm back up and running.

---

### Post by mahousaru on 2007-10-26
How is the resolution issue?  I hope it wasn't usplash that caused a kernel panic, will need to add a warning sign next time I suggest it :p

---

### Post by pylon42 on 2007-10-26
Heh, well the resolution problem is indeed gone. Still not entirely sure what I did to cause that in the first place.

---

### Post by pylon42 on 2007-10-26
memtest checked out. I'm going to chalk this one up to "angry wizard"

---

