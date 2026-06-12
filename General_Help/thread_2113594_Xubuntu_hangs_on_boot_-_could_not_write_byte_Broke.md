---
title: "Xubuntu hangs on boot - could not write byte: Broken Pipe"
date: 2013-02-07
forum: General Help
---

### Post by kpuz on 2013-02-07
I am getting an error on boot up.  The Xubuntu logon screen comes up for a second, but then I get thrown to the verbose login with the first line saying:

*could not write byte: Broken Pipe*

and it then hangs until I press the power button.

When I press the power button to shutdown, it says:

*acpid exiting*

and then shuts down.

Any ideas on how to find out the cause of this error?

---

### Post by kpuz on 2013-02-09
Well after checking my linux partition, it seemed like the partition was full.  I deleted my most recently saved files which seemed to fix the problem.  Hopefully this helps someone out in the future.

---

### Post by Seadust on 2013-02-23
I get the same thing except at shut down
----------------
could not write bytes: Broken pipe
 *Checking battery state...

hecking for running unattended-upgrades:

                                                                     acpid: exiting
 speech-dispatcher disabled:  etc/default/speech-dispatcher

----------------
I'm running Xubuntu 12.04.2 & have a adobe flash plugin problem. 
flash just isn't working even after installing xubuntu-restricted-extras .
This is a fresh install with just checking for up dates and installing xubuntu-restricted-extras .

Seadust

---

### Post by Hodevah on 2013-02-23
I have the same problem sometimes. I dont think I quite understand what you guys are doing to solve this issue. Would you mind explaining please?
Are you just basically cleaning out your system before shut-down, is that what you mean?

---

### Post by Seadust on 2013-02-24
My problem (I think) is my video card driver I have an ATI Radeon 9600 after trying to get a driver that works every thing cleared it's self & flash works with jumpy video & and sound.  I'll keep trying to fix the video card driver problem. 

so I think this is Solved for me ....Good Luck
Seadust

---

### Post by Ron_Kerlin on 2013-08-21
> **kpuz said:**
> Well after checking my linux partition, it seemed like the partition was full.  I deleted my most recently saved files which seemed to fix the problem.  Hopefully this helps someone out in the future.

Could you please explain how you did that since I only boot to a flashing cursor?

---

