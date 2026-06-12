---
title: "ubuntu 13.10 wont upgrade to 14.04. keep saying &quot;could not calculate the upgrade ?"
date: 2014-07-07
forum: General Help
---

### Post by mj360 on 2014-07-07
hi. ubuntu won't upgrade to 14.04. it gives me this

Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.

---

### Post by ubudog on 2014-07-07
Hi,

What command are you using to upgrade?

---

### Post by monkeybrain20122 on 2014-07-07
Well who cares? Just backup your data and do a clean install. A lot faster and safer. "upgrade" takes a long time and is quite unreliable, you are off to a bad start with those errors.

---

### Post by ubudog on 2014-07-07
> **monkeybrain20122 said:**
> Well who cares? Just backup your data and do a clean install. A lot faster and safer. "upgrade" takes a long time and is quite unreliable, you are off to a bad start with those errors.

Definitely a +1 to this, upgrades have always left my system broken in some way or another.

---

### Post by uRock on 2014-07-07
Have you installed any software via a repository you had to add yourself? 

If yes, then you may have to go into Software Sources and disable that repository, then try again. You may still want to create the bug report for the sake of fixing this issue for others.

If no, then you should run the command to create a bug report and link it here so that the people have the knowledge to resolve the problem to help get you on your way to upgrading your system.

As for backing up data, this should always be done whether you are running a clean install or upgrading.

---

### Post by slickymaster on 2014-07-07
> **ubudog said:**
> Hi,

What command are you using to upgrade?

Anyway, it would be interesting to know what were the commands the OP used.

---

### Post by mj360 on 2014-07-07
i'm doing it through the software update and i did sudo do-release-upgrade and got the samething.

---

### Post by mj360 on 2014-07-07
i do have the nemo files installed cause i dont like the files 3.8.2 on ubuntu. maybe thats causing the problem.

---

### Post by mj360 on 2014-07-07
if i back up will it save all my firefox bookmaker and files i download ?

---

### Post by ubudog on 2014-07-07
If you really want to do the upgrade, try disabling any PPAs or extra repos you have installed.

You should backup regardless of what you do, and as long as you backup your /home directory, your downloads, pictures, and everything in your home directory will be backed up.

---

### Post by monkeybrain20122 on 2014-07-07
> **mj360 said:**
> if i back up will it save all my firefox bookmaker and files i download ?

The firefox configurations and settings are all in the .mozilla folder (which is hidden) so just have to save that and replace the new one with it after a fresh install. You don't even need to reinstall your addons.

---

