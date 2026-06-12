---
title: "32 bit to 64 bit upgrade?"
date: 2008-05-23
forum: General Help
---

### Post by th1bill on 2008-05-23
I have an Amd 64 bit computer running Gutsy i386 and would like to upgrade to Hardy amd64.  I have burned the iso file to disk.  Is it possible to do so without crashing the old system and loosing all my data?

---

### Post by sdennie on 2008-05-23
It depends on how your system is setup.  If you have a separate /home partition then blasting the installation should be pretty painless (I think the Hardy installer may do something to protect /home partitions across installs as well but haven't tried it).  You will likely want to make a backup of /etc before re-installing though:

```

tar cvf /etc etc-backup.tar

```

It's always handy to have a backup of /etc.

Regardless of all that, is there a specific reason you want to move from 32bit to 64bit?  Depending on your workload and machine config, there isn't a hugely compelling reason to do so if the machine is already working fine with a 32bit install.

---

### Post by th1bill on 2008-05-23
Yes, Wine freezes solid as a rock and requires a reboot, every time.  I need wine to work for a couple of my programs to function.  i.e. My CD labeling program for CD Stomper.  I do a great deal of church work, creating photo disks for them and I supply folks with Ubuntu disks promoting the system and it is very unprofessional to hand them a disk with Scripto Pen writting on it.  And I can't afford thirty-four dollars a disk to give them away.

p.s. I tried 32 bit hardy with the same result.

---

### Post by sdennie on 2008-05-23
If wine is your primary motivation to move to 64bit, I'm not sure that you're going to be pleased with the transition because I believe wine runs better under 32bit.  One thing you might try to do would be to get wine directly from the wine repo.  Check: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Edit:
You could also investigate virtualization.  VirtualBox might do what you need really well.

---

### Post by th1bill on 2008-05-23
Thank you.  I'll try the Winehq and I already have Virtualbox with Windows 2K running but I seem to be able to get the video driver to work and I can't print from there.

---

