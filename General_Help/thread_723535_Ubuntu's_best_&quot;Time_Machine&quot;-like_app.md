---
title: "Ubuntu's best &quot;Time Machine&quot;-like app"
date: 2008-03-13
forum: General Help
---

### Post by priegog on 2008-03-13
So, there are quite a few threads on here requesting something like Time Machine for Leopard.
On those threads  normally only one or other option is given, but the truth is there are quite a few apps out there that offer this functionality, some of them from waaaay before Time Machine was even conceived in the mind of some developer. 
So I present you with this poll, where you shall give your opinion on the matter. The only thing I ask of those who submit a vote is that they have tried AT LEAST the one they voted for; obviously having tried more than one would be ideal. 
You are more than welcome (actually encouraged)  to give your reasons for your choice, so that newbies looking for a solution will find a place where all the opinions and comparisons are gathered toghether. 
I know at least one of these has been proposed to be included in the official repos, so hopefully from this poll some proposal can out for an inclusion and integration in the default ubuntu installation (sort of like how compiz and tracker have been seamlessly integrated to serve the ubuntu experience) for future versions. 
Also, here are links to the aforementioned programs' homepages, so just give them a try and then post your opinion! I will keep this page updated with more links if some alternatives are given. 

[Dirvish]("http://www.dirvish.org/")
[flyback]("http://code.google.com/p/flyback/")
[rdiff-backup]("http://www.nongnu.org/rdiff-backup/")
[TimeVault]("https://launchpad.net/timevault")

---

### Post by pcjunkie on 2008-03-13
I wish part image or time vault were as simple to use as Casper is in windows or over a network, Norton Ghost.

I have had to revert to manual backing up since my bash skills are like a 3 year old learning a language. I have Ubuntu as a backup system protecting windows system folders and particular backups. I could not get Ubuntu to perform "Timed" backups over a network with folder /file monitoring but I could spend $50 bucks and get Ghost to go the other way very simply. So now I have Norton (hate norton) ghost perfoming backups across a network into a Samba share folder which is then "mirrored" using keep. 

What I needed was Ubuntu to be able to SIMPLY set up a mirrored RAID 1 set and then have keep or time vault do the work of saving files over the network with Samba providing a small repository for keeping manually dumped data for all systems. In windows this takes all of 3 minutes to set up. In linux it has taken me a week to discover the parts, discover the depth of complexity and my lack of understanding of that complexity and then only to realize it was easier to not use Linux other than for providing a secure DOS.

I tried....

---

### Post by fjgaude on 2008-03-13
I use two backup programs, for speed and ease of use: Unison and Grsync. They serve me well.

---

### Post by skipx on 2008-03-27
Flybak is pretty ok, but it lacks a good working cron system. Since the project seems a bit dead, nothing happenend since 14th November, i'm now looking into another system. I still voted flyback, would be great if new updates would come out..

EDIT:
TimeVault also doesn't seem to move on.. Anybody has an idea why??

---

### Post by CalvinK on 2008-04-02
I use timevault and grsync. However, when using timevault (which I value as a great software), I have a little problem : I backup my files on an externel USB harddrive. When I boot, timevault seems to create a new drive with the same name on my internal disk and to write the files in it. 

I am obliged to connect my external drive, to unmount it, to remove the node in /media, then to remount my drive. If I don't, I have multiples names for the same disk which becomes unreachable. It's  bit annoying.

I don't know flyback but I think I will give it a try...

---

### Post by xelapond on 2008-04-02
I have my home directory in a git repository, and then that is backed up with rSnapShot.  It seems to work very well, and its very fast, as git was written to be.

---

