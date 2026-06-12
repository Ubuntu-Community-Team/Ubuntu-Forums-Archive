---
title: "Gparted - the &quot;scanning all devices&quot; problem..."
date: 2007-12-17
forum: General Help
---

### Post by Prodromoi on 2007-12-17
Yesterday Gparted worked just fine on my system.  It ran from the launcher/alias/icon and had full functionality.

But today... no.  When starting it up it always stalled at the "scanning for devices" point.  Sometimes it asked for a system password, sometimes it didn't.  I haven't installed any new hardware or software since yesterday; indeed the machine has been off for most of the day.

I've found out how to get round the problem - namely by disabling the floppy drive in the BIOS (haven't actually got a floppy drive connected at the moment, so having to disable it seems somewhat laughable), or running in from the command line in the terminal - although with that you can't change between hard drives on the fly.

So... I have to ask...  What's going on?  What would have resulted in it suddenly failing to start correctly when nothing has changed that (so I would think) would effect it?  And why would one need to disable the floppy in the BIOS?

Perplexed...
A

---

### Post by NT4usB on 2007-12-17
I see this behavior when I run gparted or qtparted and I have a drive that (I know) has a corrupted journal or improperly mounted, or something. The ap hangs for a very long time. 
I have waited it out but usually resort to killing it and fixing the corrupted drive.
You running anything odd like dual boot or multiple HDD's or something?
Has fsck ran on the drive(s) lately?
[I'm confused?] Running gparted from a terminal should pop up the same gui as running from the icon. Open a terminal and```
sudo gparted
```then alt tab back to the terminal and read what the ap is doing... Might give some clues what's hanging.

---

### Post by Prodromoi on 2007-12-18
QTparted hangs similarly for me (forgot to mention that).  I only installed it *after* experiencing the Gparted problem so I can't guarantee that it would have worked before, but I suspect whatever is effecting Gparted is the same thing causing QTparted to hang.

I'm not running a dual boot system.  I do have two separate hard drives installed (both IDE on the same chain).  The disks have been *thoroughly* checked for errors and are fine; both by fsck and the Western Digital drive diagnostic software.

The only thing that might be considered unusual is that the partitions on the second drive (sdb I think) are NTFS partitions from a Windows machine.  The contents are going to be transferred onto Linux partitions once the machine is completed.  *However* this same disk was there when Gparted was working...

Running Gparted from the terminal does indeed bring up the same GUI as running it from the launcher (except one that doesn't hang!).  I'll give the idea of alt-tabbing back to the terminal a go later today.

---

### Post by Prodromoi on 2007-12-18
Hmm.  Curiouser and curiouser...

Now Gparted started up just fine again from the launcher, just as it had done before.
QTparted tries to start up but finds no devices.

Again, no hardware or software changes since trying yesterday.  The machine seems to have developed a (cantankerous) mind of its own!

---

### Post by NT4usB on 2007-12-18
gparted is supposed to be run as root. iirc, it prompts for a password or otherwise wenches at you when you run it from the launcher. 
I've removed mine from the menus so the only way I can run it is from a terminal.
Could possibly the password prompt be hiding behind the gui and it's not stuck, just waiting for the pw? Another Alt+Tab opportunity...

---

### Post by thoffland on 2007-12-21
I had the same problem, it was because Gparted was scanning my FAT32 drive which takes forever. You can use gparted by running it from a terminal on the specific partition you want to work on. 

For example: 
```
sudo gparted /dev/hda1
```

If you don't know how your partitions are arranged, you can find out by: 
```
cat /etc/fstab
```

Maybe this helps?

---

### Post by Prodromoi on 2007-12-21
I think it might also be taking ages to scan the NTFS drives too.  I've now completed my migration from XP to Linux and got rid of all the NFTS formatted partitions - and Gparted has stopped playing up and works just fine again - even with the floppy drive enabled in the BIOS.

---

### Post by ^Albe^ on 2008-01-09
strange
in the past,
gparted works perfect and i had , time ago, 1 ext3 hd (the ubuntu one), 5 ntfs hd,s and 2 fat hds (all connected and mounted by default)
in the last times (i dunno if is gutsy related or not) gparted annoying me with this "finding devices" message
some months ago i detached many hds and now  i have only 1 ext3 drive, 2ntfs hd (not mounted), and no other 
obv, always with the same pc

for me there's some "feature/bug" added in the last time: in the past works well

in the hope to read some suggestion for solve (is good to know that specifing the dev the scan is not needed, thx, but obv i prefer to have all the drives available in a single gparted session)

---

### Post by evil316 on 2008-01-09
My gparted scans forever too.  I have 2 Hdd.  The smaller of the two is a fat32 partition I think.  Is there anyway to repartition without using gparted or do I simply need to let it run forever until it finishes?  Qparted says it doesn't find anything or something to that effect as I recall.

---

### Post by leonidas666 on 2008-01-09
I also have the same problem, gparted is taking forever to start up. 
I tried running it with
```
gksudo gparted /dev/sda
```
and then it worked. Note that i am running it with the whole hd, not only with one partition. 
I have also seen that i have lots of accesses to fd0 in my dmesg output, so i guess gparted is getting stuck trying to access my non-existant floppy.

> Is there anyway to repartition without using gparted or do I simply need to let it run forever until it finishes?
There are several command-line programs for changing the partitions. However, gparted is much more comfortable to use. If you don't get gparted to work (letting it run longer will probably not help you...), you can try cfdisk or fdisk. I think cfdisk was the tool with the semi-decent ui. But read the documentation carefully, it's easy to accidentally delete something....

---

### Post by ^Albe^ on 2008-01-10
only for knowledge
i have just reinstalled gutsy, the old one (upgraded from feisty and from the previous one) had two little issue and i take the decision for a "from zero" reinstallation
well
after the home copy and some apt-get install/update/upgrade, i have gparted working (same pc, same hds as before)
the "finding devices" desappear , or is so fast...
perhaps some, or one, package make gparted crazy


regards

---

### Post by mahiyar on 2008-01-15
You can open up more than one disks at once using command like  >>gksudo gparted /dev/sda /dev/sdb

---

