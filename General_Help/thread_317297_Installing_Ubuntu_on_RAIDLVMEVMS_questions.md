---
title: "Installing Ubuntu on RAID/LVM/EVMS questions"
date: 2006-12-12
forum: General Help
---

### Post by RoboJ1M on 2006-12-12
Hi,

I'm after some pointers to guides to do the following.

How would I go about installing Ubuntu (Kubuntu actually, but I assume it's not going to be any different at install) on LVM over (initially) RAID0?

I say initially because I want to be able to get more drives for my PC and migrate from RAID0 to RAID5 as my Big Box PC is going to be moving into the loft/attic/cupboard to become a multimedia server.

So I guess that I need EVMS for that as well, right?

Is all of this possible/easy/sensible on Ubuntu?

Do I need a "normal" disk to boot from?

Thanks,

J1M.

---

### Post by keithweddell on 2006-12-12
Not exactly what you're after but [this]("http://users.piuha.net/martti/comp/ubuntu/raid.html") might help get you started.

Keith

---

### Post by RoboJ1M on 2006-12-12
Does this mean that it's not possible to install Ubuntu on a Software RAID0 disk?

Do I need a bit of ordinary disk space somewhere to boot from (containing the /boot drive, right?)

Thanks,

J1M.

---

### Post by keithweddell on 2006-12-12
I'm no expert on this - just sharing something I found while researching.  But the howto in the link put everything onto raid and then put grub on both disks.  I know he's doing raid1 and you're thinking about radi0 but I'm guessing that the requirements will be similar.  Either way, it looks as though the installer handles it.  If this is a new set-up you could just try it out and wipe it if it doesn't work out.

Keith

---

### Post by fopetesl on 2006-12-13
RAID1 : about to go over to SUSE!
I followed Keith's link which at first scan looked good.
However once I've set up "physical volume for RAID" that's IT.
It's not possible to create ANY other partitions.
So how in h*ll do I create /root, swap, /var, etc., as RAID volumes _before_ I run mdmap?](*,)

---

### Post by RoboJ1M on 2006-12-13
How about:

One RAID1 volume to rule them all.

Put that into an LVM group.

Into that LVM group create your /, /swap, /home, etc

And then (I think) put EVMS on top of that to manage it all (RAID level migration, recovery, LVM re-partition, etc, etc)

I think I'm going to create:

/dev/hda = 120Gb HDD
/dev/hdb = 80Gb HDD

/boot on 0.5Gb part on hda

RAID0 across the remaining space on both HDDs

LVM on top of that

EVMS on top of that?

J1M.

---

### Post by fopetesl on 2006-12-13
Hummm.  I need to understand LVM & EVMS first I think. Or be hand fed through it.

Expect a response in about 99 years or when Mordor falls.

OK, couple of days then.;)

---

