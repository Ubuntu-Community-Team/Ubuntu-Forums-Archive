---
title: "Help! Worst mistake ever: Renamed /etc"
date: 2006-11-02
forum: General Help
---

### Post by steveM49 on 2006-11-02
Things just went from bad to worst.  

Trying to install edgy eft failed. Synaptic demanded that the broken installs be fixed.  I told it to go ahead. It seemed to remove almost all functionality.  I had the (poor) bright idea of restoring /etc from a backup. To keep things clean, I mv'ed /etc to /etc_broken.

/etc contains files crucial to running the system.  Backuppc couldn't think about restoring without it.  I tried to move /etc_broken back to /etc, but now I am not in the sudo list on /etc.  (Because /etc isn't there!)

I'm afraid that I now own a piece of hardware with no operating system on it.  I tried to login as root, but without the /etc files, I can't!

Please help!](*,)

---

### Post by taurus on 2006-11-02
Did you boot your machine up as a regular desktop when you moved /etc back and forth?  You're supposed to use the LiveCD when you want to move system directories around...

---

### Post by bsussman on 2006-11-02
I know it is not fun.  Now is the time to minimize losses in time and labor.
Since you have backups, you might be in a situation where re-installing is the least labor.

I am having a tough time thinking of any situation where renaming of any of the standard directories is ever the correct answer to any question except "How do I guarantee myself a major learning experience?".

---

### Post by dcstar on 2006-11-03
> **taurus said:**
> Did you boot your machine up as a regular desktop when you moved /etc back and forth?  You're supposed to use the LiveCD when you want to move system directories around...

I thought you could boot the live CD, mount the hard disk and do whatever you wanted to it?

---

### Post by bsussman on 2006-11-03
> **dcstar said:**
> I thought you could boot the live CD, mount the hard disk and do whatever you wanted to it?

Yes you can.

And when you are done, the hard disk might not boot or might behave strangely when booted if you did things like change permissions or  names that affect the operation of linux.

I owe my unix career to being able to boot from a diskette to reset a root password on a system whose sysadmin had literally disappeared.  But you can be sure I had somebody there watching while I did it :)

Understanding the consequences of a particular action, prior to taking the action, is a good idea.  This seems to get lost in these forums, where experts post answers that beginners follow blindly, without understanding what can happen.

---

### Post by steveM49 on 2006-11-03
Other than eventually laughing at my stupidity, I think "major learning experience" is the best I'll get out of this.

Thanks for the help.

---

### Post by Lord Illidan on 2006-11-03
Well..you should never rename such important folders.. for the same reason that you shouldn't rename C:/Windows

---

### Post by bsussman on 2006-11-03
> **steveM49 said:**
> Other than eventually laughing at my stupidity, I think "major learning experience" is the best I'll get out of this.

Thanks for the help.

:)

You are now in the best frame of mind to repair and learn - and, of course, help the next person.

BTW, a form of post I would love to see more often is "I plan to do x because of y.  How will this affect my system?".

---

