---
title: "Auditing outdated packages"
date: 2021-11-18
forum: General Help
---

### Post by emoreno1981 on 2021-11-18
[FONT=Arial]I'm conducting an audit to determine if our Ubuntu server has the latest patches installed, especially the ones related to security issues. I was able to get a report with the list of installed packages from our IT team by executing the following command:  **apt list --installed**[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Do you know if there is a way to scan this report by an automated tool to determine if any of the packages are outdated?[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Thanks in advance for your help,[/FONT]

---

### Post by TheFu on 2021-11-18
The commands are slightly different based on the release. Which release? One is:
```
$ ubuntu-support-status --show-unsupported
```
There's a different, but similar command for other releases.

On a 20.04 system I have here, there are 7 packages listed as unknown. Most are connected to an all-in-one printer-scanner-fax device. The others are connected to opensnitch - which is a per-user, per-application, firewall sorta like what Windows users would expect.

On 18.04, the list is ... er ... over 1000 packages unsupported.

Newest isn't the same as supported, BTW. 
New is the enemy of stable, so it is very likely you don't actually WANT the newest. You probably want packages are are maintained.  In a professional organization, there would be 2 different "supported" branches of code.
[LIST]
[*]current +1
[*]current
[*]current -1
[/LIST]

In the ubuntu world, that would translate to

[LIST]
[*]Current non-LTS
[*]Current LTS
[*]Prior LTS
[/LIST]

So, if we look at the kernels (you need to do this for each package), the Ubuntu 20.04 kernels are either
5.4.x (actually 5.4.0-90-generic today)
5.11.x (I don't use this HWE kernel)

On 18.04 (the prior, but supported LTS), the kernels are:
5.4.0-90-generic (HWE) and a 4.15.x version which was shipped with the original release. I'm running the 5.4.x version to make the planned upgrade to 20.04 just a little smoother, as those systems get migrated before April ... probably.

---

### Post by dragonfly41 on 2021-11-19
As a sole developer (not part of any company) I was pondering a few days ago about the feasibility pf somehow applying machine learning tools to server configurations including looking at classifiers such as frequency of usage of packages .. there are so many threads about freezing etc. so I explored ideas as presented here:

[https://www.youtube.com/watch?v=PJ_kx9-OPgc&ab_channel=DevOpsDaysTelAviv](https://www.youtube.com/watch?v=PJ_kx9-OPgc&ab_channel=DevOpsDaysTelAviv)

I also researched these two commands

ls -ltu /usr/bin | less 
popularity-contest | grep '<OLD>'

Also look at 
lynis auditing tool  (lynis should be in Ubuntu repo if not installed

These might or might not help your auditing.

Also I use Stacer monitoring tool.

I still feel that the machine learning approach has some merit so I intend to keep digging. But I would prefer to run it locally rather than on a service.   And follow up lynis idea.

---

