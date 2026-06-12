---
title: "Brining Compromised Server Back to Life"
date: 2007-12-06
forum: General Help
---

### Post by ehsan on 2007-12-06
Hi all,

I have an Ubuntu 7.04 server, which was recently hacked into.  The hacker had gained root access, and replaced the SSH binary to make an open door for his future logins.  I tracked the problem, fixed the SSH binary, and made sure that unauthorized SSH logins are impossible.

Now, I'm looking for a way to bring the compromised server back online, without having to reinstall the whole server from scratch.  Here is what I have in mind:

1. Somehow get a list of all installed packages.
2. Verify that list to make sure only the packages that I want are included in it.
3. Do apt-get install --reinstall on all of them to make sure that no other binaries have been changed.
4. Install a number of security utilities such as fail2ban and OSSEC to keep an eye on things for a while.

I appreciate any helps and suggestions that you may be able to provide.

Thanks!
Ehsan

---

### Post by patr547 on 2007-12-06
in my opinion, it would be best to completely rebuild the server, even though you might not want to. if a hacker obtained root access to your server, there may be numerous backdoors and configuration changes in your system now, some of which could be very difficult to find, depending on the skill level of the hacker.

one point to note is, how did the hacker gain root access? did you enable your root account? the whole point of the sudo feature is to make the environment more secure. there should not be an active root account, and if you have a program that requires it, try to find a way around that.

---

### Post by ehsan on 2007-12-06
> **patr547 said:**
> in my opinion, it would be best to completely rebuild the server, even though you might not want to. if a hacker obtained root access to your server, there may be numerous backdoors and configuration changes in your system now, some of which could be very difficult to find, depending on the skill level of the hacker.

I agree with what you're saying.  I'm just looking for a way to reinstall all the packages, and possibly get prompted by apt in case of configuration files that differ from the ones provided in the packages, and diff the config files to see what has been changed, and whether it's OK or not.  Something like what happens when you update a package and the update includes new configuration files...  I really really want to avoid doing a full rebuild.

> **patr547 said:**
> one point to note is, how did the hacker gain root access? did you enable your root account? the whole point of the sudo feature is to make the environment more secure. there should not be an active root account, and if you have a program that requires it, try to find a way around that.

The root account was disabled on that machine.  There was only a single user allowed to sudo in /etc/sudoers, so the attacker must have gained access to that account and elevated from there, or used a vulnerability in another package which allows root access...  The latter case seems unlikely because I kept the system up-to-date.  Anyway, one thing that the attacker did was to get rid of all of the log files before the attack, so I can't tell much in that regard...

Ehsan

---

