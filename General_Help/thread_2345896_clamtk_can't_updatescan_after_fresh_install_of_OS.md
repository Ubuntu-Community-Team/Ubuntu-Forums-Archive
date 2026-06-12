---
title: "clamtk can't update/scan after fresh install of OS"
date: 2016-12-09
forum: General Help
---

### Post by Mike_Andrews on 2016-12-09
After a fresh install of Lubuntu 16.04, Clamtk, installed from Synaptic PM, will neither update nor scan. 
Checking Synaptic it appears that there are no further packages that should have a bearing on this glitch.
Anybody deal with this issue B4?
I'm going to change servers after Bleachbit finishes running a disk wipe and see if it helps.

---

### Post by deadflowr on 2016-12-09
Clam runs it's own updating system, separate to Ubuntu's.
It's updater updates the virus signature database and connects to the clam servers.
I have noticed that the setting is now double clicking to open the various options in clamtk.
But if you go to settings you can change that.
Also in settings make sure to set the scan folders recursively.
(Bonus to disable the scan PUAs feature, as the scanner gets rather trigger happy with various files that are normally harmless, imho)
(I am not sure if you knew/know that, but figured i would mention it anyway)

Outside of that you can update clam manually with:
```
sudo freshclam
```
note that this can, at times, be slow.

hope it helps or something

---

### Post by howefield on 2016-12-09
> **Mike_Andrews said:**
> After a fresh install of Lubuntu 16.04, Clamtk, installed from Synaptic PM, will neither update nor scan.

What does the terminal command..

```
clamscan -V
```

At the time of typing this message (Fri  9 Dec 09:23:44 UTC 2016) the latest definitions file is 22683

```
clamscan -V
ClamAV 0.99.2/22683/Fri Dec  9 07:36:22 2016
```

---

### Post by Mike_Andrews on 2016-12-09
deadflower, 

Thanks for your input.
Yes, I'm aware of all you revealed and have been a Clamtk user for years off and on; I have other (Ubuntu 16.04) computers that run Clamtk without a hitch.
Like you, I seldom allow Clam to scan for PUA's as there will almost always be false readings that way.
No -- this time Clamtk's refusal to allow Update and inability to scan (as it lists 0 definitions), remains a complete mystery.

 To howefield:

Thanks for your input; after running sudo clamscan - This is the result:
ClamAV 0.99.2/22686/Fri Dec  9 14:38:40 2016

The anomaly is occurring on an old HP box, C. 2003 that I fixed up with max RAM and a hi-powered AGP card.
Originally I'd installed Ubuntu but there wasn't enough hardware-horsepower for the old box to get out of level 5-verbose mode running graphics-intensive Ubuntu, so I eventually landed on Lubuntu ('L' for light-weight) and now have a decent system, albeit a bit slow.
I sometimes wonder if the mobo may not be carrying an unwanted gift (that keeps on giving) that a disk wipe cannot eliminate, since there have been other strange anomalies which were marked down to age and the old machine's very limited graphics capability.
I plan to try installing more packages using Synaptic in hopes of hitting the missing quotient. But Terminal did throw up an error  dialog once, advising that something was wrong with Clam's logfile.
I used sudo rm (and name of string) to remove the errant file and it looked for a minute as if the issue were solved. But upon going back and trying to run update, Clamtk bombed again. Wish I could recall what I was doing at that juncture, but it's gone. 
It is noted that the full array of packages was not present in this recent install and some were missing even after running a full update-upgrade-install from Term.
. . . One example is the gufw firewall front-end, which I happen to like better than Firewalld.
If it comes down to it I'll remove the drive and subject it to a Macintosh OS X 10.5-Leopard disk wipe, which in my experience NEVER skips a beat and removes everything from all sectors.
. . . Only drawback is that it sometimes takes several days, and if its a cmos infection, wiping the HD won't make any difference.

Thanks again folks, for trying to help.
Please come back if you have any new ideas.
M.

---

### Post by howefield on 2016-12-09
> **Mike_Andrews said:**
> Thanks for your input; after running sudo clamscan - This is the result:
ClamAV 0.99.2/22686/Fri Dec  9 14:38:40 2016

So it is updating fine then, as you have the latest definitions file.

The problem with not scanning.. how are you initiating the scan and what error(s) are you getting ?

---

### Post by Mike_Andrews on 2016-12-09
It's all over but the long wait; just removed the HD and it is being subjected to Mac the rife in a 3-pass random overwrite, which takes about 18 hours.
Will come back and post results following re-re-reinstall dejavu.
M.

---

### Post by Mike_Andrews on 2016-12-11
> **howefield said:**
> So it is updating fine then, as you have the latest definitions file.  (No!)

The problem with not scanning.. how are you initiating the scan and what error(s) are you getting ? (Plz see below)
------------------------------------------------------------------------------------------------------------------------------------------------------------------

It remains a mystery, howefield. According to the input query you offered, the update process WAS running; but the clamtk interface remained blank and all attempts at running update from there immediately ended with no result.

. . . Doesn't matter now, since the HD from the old box has been bare-metal-wiped and Lubuntu 16.04 LTS has been reinstalled. It took three tries B4 the install was successful, but the third seems to be a charm, ha.

One anomaly, however that keeps recurring during the initial phase of setup for a fresh install is an error/abort of the installation due to the (supposed) presence of a 'swap drive' that poses a dire security risk, etc. This, even after a 3-pass random overwrite and removal of all partitions on the disk, so that there only remained one extended area of free space for the Lubuntu Installer to deal with.

This has happened with two different HD's in the past and continues, unabated. I'm completely 'out to sea' as to what's causing it, unless the installer is detecting input from a cmos hitch hiker and reading said input as coming from a swap drive.

At any rate, following the abort, Lubuntu Live CD comes up quickly and there I have access to Terminal, where I run sudo swapoff -a, after which the installer (usually) runs without a hitch.

The only issue now is that Desktop Manager is not active. This apparently stands in the way of changing the abysmal wallpaper that serves as the Lubuntu default, to something that I can look at without taking two Dramamine pills for nausea. (Kidding.)

But in answer to your question as to errors -- the only one I recall was generated in Terminal after I tried to update Clamtk using: sudo freshclam. It kicked back an error that something was amiss pertaining to the clam-scan log. Maybe it had to do with Desktop Manager? The latter was down for the count on the old system, too. . . a jinx that seems to follow me much like the dark clouds over Joe Bfpsplicke, one of the Dogpatch characters in 'Lil Abner.

The new install is doing fine, however and I'm a happy camper 4 now.

. . . Thanks 4 your help, howefield. Visit any time -- [email]mike1792@yandex.com[/email]

---

