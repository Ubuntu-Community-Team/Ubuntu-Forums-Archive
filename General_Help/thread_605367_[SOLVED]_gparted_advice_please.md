---
title: "[SOLVED] gparted advice please"
date: 2007-11-07
forum: General Help
---

### Post by antmenj on 2007-11-07
I'm trying to clone an intire hdd install of dapper to be installed in the same machine on a larger drive yet not have to download days worth of downloaded updates and programs again.

Edit [COLOR="Red"]Go to bottom of page for what worked
[/COLOR]
I plan to use partimage to copy the partitions.

1 Do I ignore the swap partition sda5?

2 Do I need to copy the extended section sda2?  Not sure what thats used for....

I tryed to used gparted form a booted "systemrescueCD" to edit the destination drive but I can't get the partition sizes of sda2 & sda5the same value as the original drive _after the decimal point_.

3 Does it matter if they are close enough?

4 Is it posable to edit later the value of the main  sda1 partition after the subsiquent partitions are made...or is it possable to make sda2 & sda5 before sda1 then give the rest of the disk to sda1?

We are talking single boot dapper.

Cheers :)

---

### Post by zvacet on 2007-11-07
[http://www.psychocats.net/ubuntu/backup]("http://www.psychocats.net/ubuntu/backup")

---

### Post by antmenj on 2007-11-07
Ok I'd already had a look at the above link + many many many........ others :neutral:.

Anyone want to have a stab at the 4 questions?

Since then I'v had a play with gparted on both the ubuntu live CD and the systemrescueCD.

Ubuntu live gparted shows hda/hdb and the systemrescueCD shows sda/sdb

I'v been able to copy sda1 to another drive but not sda2 or 5.  I tryed makeing partitions 2 and 5 but the drive won't boot so I presume the boot info is not in sda1...am I right?  The ubuntu live gparted shows lock images against hda2 and 5.

Tryed partimage - didn't work out how to set the file destination to a secondary hard drive.  How is that posable?

---

### Post by mike555 on 2007-11-07
I wondering why you didn.t  just use ÄptOnCD" to copy everything you have installed on to a CD , then install Ubuntu and then put in the CD and install from it ...............

---

### Post by antmenj on 2007-11-07
> **mike555 said:**
> I wondering why you didn.t  just use ÄptOnCD" to copy everything you have installed on to a CD , then install Ubuntu and then put in the CD and install from it ...............

Because I **presumed** I had to download an ISO of apps to burn to a CD.

Presume nothing...... :oops:.  This sounds very cool I will take a further look:guitar:. I hope it backs up updates too.

I worked out I have about 8 days of downloaded apps and updates on dialup to backup:lolflag:

If it backs up to a networked share even better.:)

I'd still like to know whats the go with hda2 and 5  I think hda5 swap is just blank drive thats used on the fly right?  But as for hda2?????

---

### Post by antmenj on 2007-11-08
Hooray:guitar:

*Well I'v done it in a somewhat odd way.  I tryed it on a guinea pig old install first on a no longer used drive.*

Disconect source drive.

Installed new hdd as master.

Install ubuntu from CD.  Shut down.

Reinstall source drive as master & new drive as slave.

Boot systemrescueCD and start gparted.  (gparted from ubuntu cd wouldn't do it)

delete sdb1 ext3 partition from slave.

copy sda1 ext3 from master to slave.

resize sdb1 ext3 on slave to fill the drive. Power off.

disconect source drive & reinstall new drive as master.

Power up and log in:guitar:

*Now to try it on the real drives in question.  Will mark solved if still working in a few days touch wood 8-[.*

---

### Post by antmenj on 2007-11-10
Still working:)

---

