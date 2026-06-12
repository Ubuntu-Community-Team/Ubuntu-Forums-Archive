---
title: "beagled-helper eats up to 100% CPU"
date: 2006-10-30
forum: General Help
---

### Post by anodizer on 2006-10-30
This happens from the day I installed Edgy Eft beta. I made a clean install but used my home folder from edgy, thus keeping all the configuration files. Removing beagle and deleting ~/.beagle folder didn't help. It is annoying so some help would be appreciated.

---

### Post by reclusivemonkey on 2006-10-30
> **anodizer said:**
> This happens from the day I installed Edgy Eft beta. I made a clean install but used my home folder from edgy, thus keeping all the configuration files. Removing beagle and deleting ~/.beagle folder didn't help. It is annoying so some help would be appreciated.

Try letting beagle finish its indexing. I had this behaviour when I first installed Edgy, but after a few days the index had finished and beagle now works much better than it did in Dapper. If you need full power for your CPU, just kill beagle, but leave it to do its thing at some point.

---

### Post by MattFlower on 2006-11-02
Did waiting work out for you?  I've had this same problem since I upgraded my laptop to Edgy about 3 weeks ago.  I had been thinking about filing a bug, but I wasn't sure if it was some quirky thing I messed up myself.

*** Correction ***
I think I have found a solution by reading through the Fedora forums.  As long as there isn't anything valuable in yours, delete your ~/.beagle directory.  Once mine rebuilt itself, it seems to use a normal amount of cpu.

---

### Post by Luggy on 2006-11-11
> **MattFlower said:**
> Did waiting work out for you?  I've had this same problem since I upgraded my laptop to Edgy about 3 weeks ago.  I had been thinking about filing a bug, but I wasn't sure if it was some quirky thing I messed up myself.

*** Correction ***
I think I have found a solution by reading through the Fedora forums.  As long as there isn't anything valuable in yours, delete your ~/.beagle directory.  Once mine rebuilt itself, it seems to use a normal amount of cpu.

I found that waiting did not fix the problem. I would leave my computer on all day for several days but beagled would still make out the CPU.

deleting ~/.beagle worked for me.

---

### Post by Bokonon on 2006-11-26
For me, I had to shutdown beagle and then delete the ~/.beagle directory.  I then restarted beagled and it seems to be using a reasonable amount of CPU.

Simply deleting the directory while it was running didn't help.

```
ps -ef | grep beagle

kill -9 <#### of beagled & beagled-helper>

rm -rf .beagle

beagled & (or a restart)
```

I didn't have to do this as sudo.

EDIT:  This did not help me after all.  It appeared to be working and my cpu usage from beagled(etc) dropped to almost nothing, but I checked a few hours later and it is back at 100% (on one of my cores).  Sorry....

---

### Post by funk19 on 2006-12-02
Hi Bokonon

Just followed your step-by-step here and I too am now back to 100% CPU usage. Did you get this resolved?

---

### Post by Bokonon on 2006-12-05
I have been messing with it somewhat.  I went into the beagle-settings and made some adjustments that seem to have helped.

```
$ beagle-settings
```

Then hit the "Indexing" tab.

I noticed that the two hard disk partitions I had mounted into my /home/<me>/ directory were checked as items to skip in the indexing.  I removed them both from the list (making them indexable) and right now I am running beagled and beagled-helper without full CPU utilization.  

Since I *thought* I had it fixed before, I am going to give it a few days to see if this indeed does work, but right now it seems beagle is working correctly.

UPDATE:  It has been working fine for two days now, so I am pretty sure that this or the combination of this plus my previous steps fixed the problem.  FWIW, I had an upgraded Dapper->Edgy install with beagle running before and after the upgrade.  No problems on my Edgy fresh install with no 'private/non-indexed' directories.

---

### Post by funk19 on 2006-12-07
> **Bokonon said:**
> I have been messing with it somewhat.  I went into the beagle-settings and made some adjustments that seem to have helped.

```
$ beagle-settings
```

Then hit the "Indexing" tab.

I noticed that the two hard disk partitions I had mounted into my /home/<me>/ directory were checked as items to skip in the indexing.  I removed them both from the list (making them indexable) and right now I am running beagled and beagled-helper without full CPU utilization.  

Since I *thought* I had it fixed before, I am going to give it a few days to see if this indeed does work, but right now it seems beagle is working correctly.

UPDATE:  It has been working fine for two days now, so I am pretty sure that this or the combination of this plus my previous steps fixed the problem.  FWIW, I had an upgraded Dapper->Edgy install with beagle running before and after the upgrade.  No problems on my Edgy fresh install with no 'private/non-indexed' directories.

Thanks for the post and the update. I was running Edgy off a fresh install when this issue happened with me. I, along with the developers of beagle, noticed that I had quite a lot of RTF files which are very untested with Beagle.

I removed all my RTF files from the hard drive and must admit I have not had a problem since doing this.

Just a quick question:- you said you were playing with the settings "beagle-settings" - Where did you find these? I tried to run beagle-settings in the terminal but got nothing.

---

### Post by Bokonon on 2006-12-08
> **funk19 said:**
> Just a quick question:- you said you were playing with the settings "beagle-settings" - Where did you find these? I tried to run beagle-settings in the terminal but got nothing.

I am not sure if you are missing a package or something, but I just run it in the terminal and then a GUI configuration utility comes up.  You can search here for "beagle-settings" and find some others who used it--which is how I found it.

My CPU usage is normal now with beagled & beagle-helper running for about 3-4 days now.

---

### Post by Cable on 2006-12-08
[This]("https://launchpad.net/distros/ubuntu/+source/beagle/+bug/64326") bug report might be informative.

---

### Post by Bokonon on 2006-12-10
I left my system on over the weekend and just checked this monday and I am back at 100%.  ](*,)   I thought I had it fixed, but it looks like I might have to wait for a new version of Beagle.

Thanks for the link to the bug report.  Very informative.

---

### Post by Corbelius on 2006-12-11
> **Bokonon said:**
> I left my system on over the weekend and just checked this monday and I am back at 100%.  ](*,)   I thought I had it fixed, but it looks like I might have to wait for a new version of Beagle.

Thanks for the link to the bug report.  Very informative.

If u have an ubuntu edgy 64bit, try beagle 0.2.13 in my repository, resolve this bug.

---

### Post by jimbz on 2007-02-04
I was having this problem too until I installed the version 0.2.14. It is on its way in the backports but 'failed to build' for a dependency problem. However, I managed to build the backport version myself, you can find it [_there_]("http://j.brauxzin.free.fr/beagle_0.2.14-0ubuntu3~edgy1_i386.deb"). I hope it can help.

---

### Post by casper911ca on 2007-02-21
If you go on thier website, Beagled-helper is supposed to run at 100% CPU for a few minutes. It treis to operate when the user is not using his computer ( on the "nice" status). If it goes indefinately then it is a bug.

---

### Post by hmich176 on 2008-07-08
I just had the same problem today.  I was running Transmission and Firefox and then it just killed my system.  Can I just delete the program, or is it necessary to have?

---

