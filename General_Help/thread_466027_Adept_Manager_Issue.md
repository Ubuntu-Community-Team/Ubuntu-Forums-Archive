---
title: "Adept Manager Issue"
date: 2007-06-06
forum: General Help
---

### Post by BostonBrother on 2007-06-06
I was trying to install the pptp-linux package on my kubuntu system and I had a message come up asking me to place the kubuntu install cd in the cd drive and press enter.  So, following directions I do and nothing happens.  I press enter over and over again and nothing.  Eventually a window pops up asking me what I would like to do with the cd, open it in konqueror etc.

I´m guessing that adept-manager is asking for the install cd because there is some change to the kernel or something?  Am I right on that?  Also, I´m thinking that maybe I have something set or not set to work properly when I place an .iso in the drive which is snarfing things up.  Any ideas out there as to why this might be happening and how to fix??

Thanks

---

### Post by taurus on 2007-06-06
I bet you have an IDE CD drive while your /etc/fstab is pointing to SCSI drive.  However, you can comment out the CDROM repo in /etc/apt/sources.list so it would not ask you to insert the CD into a drive again.  It will grab it from the net then.

```
kdesu kate /etc/apt/sources.list
```
and place a # in front of the line that has CDROM in it (usually near the top).  Save it and run

```
sudo aptitude update
```

---

