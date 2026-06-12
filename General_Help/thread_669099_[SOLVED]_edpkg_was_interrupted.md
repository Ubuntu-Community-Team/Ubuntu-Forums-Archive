---
title: "[SOLVED] e:dpkg was interrupted"
date: 2008-01-16
forum: General Help
---

### Post by dpwilson on 2008-01-16
I've read past threads on this problem, but I guess mine is a little unique.  As I try to install anything in add/remove, synaptic or recommended updates, I get the message,
 [I]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I].
  I have put that in a terminal and when i hit enter it hangs at ** Installing 1 assembly from libgmime2.2-cil into Mono*.  I go to copy so I can paste it here as it reads and it jumps to another line and hangs  at* Installing 1 assembly from libndesk-dbus1.0-cil into Mono* and then copy and  then another line that hangs.  Here is the output from terminal.  Any suggestions would be greatly appreciated.  By the way, this is on 7.04 as I got fed up with trying to get sound in 7.10.

Terminal Output:
wilson@wilson:~$ sudo dpkg --configure -a
Password:
Setting up mono-gac (1.2.3.1-1ubuntu1.1) ...
* Installing 1 assembly from libgmime2.2-cil into Mono
* Installing 1 assembly from libndesk-dbus1.0-cil into Mono
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
dpkg: error processing mono-gac (--configure):
 subprocess post-installation script killed by signal (Interrupt)
dpkg: dependency problems prevent configuration of mono-runtime:
 mono-runtime depends on mono-gac (= 1.2.3.1-1ubuntu1.1); however:
  Package mono-gac is not configured yet.
dpkg: error processing mono-runtime (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libmono2.0-cil:
 libmono2.0-cil depends on mono-runtime (>= 1.1.8.1); however:
  Package mono-runtime is not configured yet.
dpkg: error processing libmono2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of tomboy:
 tomboy depends on mono-runtime (>= 1.1.8.1); however:
  Package mono-runtime is not configured yet.
 tomboy depends on libmono2.0-cil (>= 1.2.3); however:
  Package libmono2.0-cil is not configured yet.
dpkg: error processing tomboy (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mono-gac
 mono-runtime
 libmono2.0-cil
 tomboy

---

### Post by zvacet on 2008-01-16
```
sudo dpkg --configure -a
```

---

### Post by scizzo on 2008-01-16
I got this same error in Hardy when it was updating mono. What happened in the end was that it seemed the package was broken. After trying to run apt-get -f install and apt-get update && apt-get -u dist-upgrade the package fixed itself.

This is a --configure error for the actual package and seems to be broken. Best is to contact the package maintainer about it being broken if it is not fixed in the upgrade or by using apt-get -f install which will try to configure it.

---

### Post by scizzo on 2008-01-16
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

He used sudo......

---

### Post by dpwilson on 2008-01-16
> **scizzo said:**
> I got this same error in Hardy when it was updating mono. What happened in the end was that it seemed the package was broken. After trying to run apt-get -f install and apt-get update && apt-get -u dist-upgrade the package fixed itself.

This is a --configure error for the actual package and seems to be broken. Best is to contact the package maintainer about it being broken if it is not fixed in the upgrade or by using apt-get -f install which will try to configure it.

I don't want to sound stupid, but I am pretty new to linux/ubuntu.  Should I try the commands you have listed above to fix the problem?  Who is the package maintainer that I should contact?

Thanks for the help so far.

---

### Post by scizzo on 2008-01-16
> **dpwilson said:**
> I don't want to sound stupid, but I am pretty new to linux/ubuntu.  Should I try the commands you have listed above to fix the problem?  Who is the package maintainer that I should contact?

Thanks for the help so far.

Try to run:

```
sudo apt-get -f install
```

If that does not help:

```
sudo apt-get update && sudo apt-get -u dist-upgrade
```

Then see if there is any dependency problem in the apt-get -u dist-upgrade. According to the error it actually looks like a package might be missing in the repos or something simular since it is complaining about dependencies. So check this and see what happens.

---

### Post by dpwilson on 2008-01-16
Will try that this evening.  Thanks for the help.  Will let ya know if it works or not.

---

### Post by dpwilson on 2008-01-16
I ran the commands above and  I end up getting the same message, "e:dpkg was interrupted...."

Any other ideas?  If not, who do I report this problem to so as to find a fix or workaround?

All help is appreciated

---

### Post by seringen on 2008-01-23
i have the same problem. I personally haven't cared too much about it since all the things I need to run still work, but don't feel too bad because I can't figure out what's wrong with it, either.

---

### Post by seringen on 2008-02-04
wget [http://launchpadlibrarian.net/11307378/policy.2.1.FlickrNet.dll](http://launchpadlibrarian.net/11307378/policy.2.1.FlickrNet.dll)
sudo mv policy.2.1.FlickrNet.dll /usr/share/cli-common/policies.d/libflickrnet2.1.5-cil/


someone had the proper file linked to in launchpad

---

### Post by zvacet on 2008-02-04
```
sudo apt-get install mono-gac mono-runtime libmono2.0-cil tomboy
```

```
sudo apt-get update
```

---

