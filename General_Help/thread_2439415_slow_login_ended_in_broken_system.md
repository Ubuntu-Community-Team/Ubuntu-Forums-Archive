---
title: "slow login ended in broken system"
date: 2020-03-27
forum: General Help
---

### Post by kuntergunt on 2020-03-27
Since yesterday each login to Ubuntu seemed to take longer. This also applied to shell commands like "sudo ls" or unlocking the software updater. I was afraid that I would soon not be able to login to my machine any more. I was running Ubuntu 18.04.04 LTS. All available updates were installed. Logins were already in +5 minutes area.

I decided to give an update to 19.10 a chance. The update ended with an error. I could not login any more and I also was not able to shut down.  It only showed an image (sad smiley) with a message "system found an error that it cannot resolve. please log off and try login again" (translated). A hard reset ended in a broken system that would not boot but only shows this "sad smiley" flickering. I have an automatic login to the guest account configured, so there is no login screen when booting. 

The system is unusable now.

---

### Post by EuclideanCoffee on 2020-03-27
The sad smile is a Windows prompt and unrelated to the login problem.

Your problem isn't the slow logins. Logins check one or two files in your system. Since the check is taking longer, your problem is most likely related to hardware. I recommend moving your thread there to diagnose with knowledge community members.

There is a small chance this is malware related. But I gathered no information from the context you supplied to lead me to that conclusion.

---

### Post by slickymaster on 2020-03-27
*Thread moved to **General Help**.*

---

### Post by kuntergunt on 2020-03-29
There is no Windows on the system, never was.

But I made some progress - it seems that the problem is related to an update of Python.
I managed to boot the system into recovery mode, which also failed to start.
But from there I could move to another console from which I could get into a root login shell.
Finally I found out, that one of the errors was "no module named apt_pkg", which came from a Python code.
Some posts I've found are related to a wrong/too high Python version being installed or updated. But none of the solutions there fixed my problem.

The good news: login from the (recovery mode) command line is now as fast as it always was. 
The bad news: I have a broken system and no idea how to fix it.

---

### Post by kuntergunt on 2020-03-29
I finally fixed it by running
apt install -f (which failed after some minutes)
dpkg --configure -a
apt install -f (which succeeded this time)

---

