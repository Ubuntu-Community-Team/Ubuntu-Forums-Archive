---
title: "Firefox not starting when using RDP"
date: 2024-01-20
forum: General Help
---

### Post by michael351 on 2024-01-20
Whey trying to startup Firefox (installed with Ubuntu) from remote desktop running Xfce, nothing happens. The load icon spins for a bit then goes away. Rebooting did not resolve the problem.
I am not familiar with how Firefox runs and checking logs shows nothing that I can find (may be looking in the wrong place).

I uninstalled and reinstalled Firefox via snap and the process completed normally. It just doesn't load via remote desktop like it used to.

Help is appreciated on how to properly troubleshoot. Thanks

p.s.
When I try starting Firefox from the command line, I get:
> /user.slice/user-1000.slice/session-c3.scope is not a snap cgroup

---

### Post by TheFu on 2024-01-20
The fix is not to use the snap packaged version of firefox.  Mozilla packages Firefox-ESR and has a PPA for this purpose.  There are guides for how to setup the PPA and install the software.

Snaps and their mandated constraints get in the way far too often.

---

### Post by michael351 on 2024-01-20
Should I first uninstall Firefox (snap) and then install the PPA version?

---

### Post by TheFu on 2024-01-20
> **michael351 said:**
> Should I first uninstall Firefox (snap) and then install the PPA version?

Both can be installed concurrently. Also, you might need a browser to follow the instructions, right?  The 

RDP probably isn't needed at all.  Any Unix client with X/Windows can run remote commands/programs on other systems, including 99% of GUI programs over an ssh connection.

IMHO, the only reason to use RDP is if your client is MS-Windows and you aren't allowed to use a better tool - corporations are like that.  On a home network, rather than RDP, use x2go. There's a client and server (one for each side).  They connect using ssh tunnels automatically, and ssh keys/certs can be used for more secure, more convenient authentication.  ssh security is what all Unix admins around the world use, so it is watched carefully and well maintained against all known attacks and bugs.

I use x2go only over the internet OR if for some terrible reason, I'm stuck on MS-Windows.  Otherwise, I'm using remote X11.

Right now, I'm using ssh tunnels to run about 20 programs on other systems, not the system I'm physically using.  That includes web browsers, GUI video transcoders, a password manager, and my fat email client, just to list a few.  The general form is 
```
$ ssh -X {remote server DNS name}  {command to be run with options}
```
For example, I create a script to run firefox on a different system. That script looks like this:
$ more ~/bin/firefox.sh 
```
#!/bin/bash
FJ_OPTS="--join-or-start=browserNormal --rlimit-as=10200000000 --ignore=seccomp "
FF_OPTS="-no-remote "

# limit RAM VSS to 4G
ssh -X deneb "/usr/bin/firejail $FJ_OPTS /usr/bin/firefox-esr $FF_OPTS $@" &

```
I want my browsers running inside some constraints, but not the constraints that snap packages mandate.  With firejail, I have 100% control over the constraints used. Most of the time, the defaults are fine, but sometimes, I need to relax 1 or 2 of the constraints to do something sketchy. ;)
As you can see from that script, I'm using firefox-esr myself.  I did this when Canonical forced snaps onto us.

Sometimes, I don't want any trace that the browser was used at all, so I use firejail's "private" mode to ensure nothing touches disk from that program.

---

### Post by michael351 on 2024-01-20
Firefox is working again as per your suggestion (via PPA)! Thank you.

I'll look into x2go. I use RDP when I want a GUI otherwise I use SSH to connect. The Ubuntu machine is my HTPC. I maintain it from my home office which is a windows desktop. I do the same for a Centos installation I use on a couple of servers as well.

---

### Post by MAFoElffen on 2024-01-20
The solutions TheFu recommended will work very well, with a few missing pieces added on your side from Windows...

Speaking from years of Windows Systems Administration experience, i could tap-dance around the sugar coatings, but... The truth is: RDP is an Microsoft Windows based protocol that has some on-purpose builtin limitations to use as non-free... Using it, you accept those limitations or pay dearly to overcome those.

xrdp works, but within those limitations.

From a Windows machine, for admin, I use WSL2, shh, scp, and Xming. 

Turn on WSL2, and install Xming. I have ssh XForwarding working well from a Windows 10 VM RSTAT console machine to do my admin... 

But seriously, if you have more than just a few Linux machines that you want to maintain from a Windows based machine, install a Linux VM and do it from there. Linux works best and easiest from Linux-to-Linux. No confusion. Best performance.

I don't know what your infrastructure is, but if you shared that, we could recommend what might work best. (Instead of having to guess for the what-might-be's)

---

