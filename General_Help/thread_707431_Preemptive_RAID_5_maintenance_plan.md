---
title: "Preemptive RAID 5 maintenance plan"
date: 2008-02-25
forum: General Help
---

### Post by mavicus on 2008-02-25
I am about to build a file server computer that comes with 4 onboard SATA ports.
I will also add a card that supplies 4 more SATA ports.

I plan on using software RAID to build two RAID 5 arrays, one on each set of 4 SATA ports.

The OS will run from an IDE Drive.

After I create these arrays, are there hard drive attributes that I should record in the event that either a drive or the OS goes down?

The only other time I used software RAID in Ubuntu, the OS died and was reinstalled. The separate mirror set was mysteriously inaccessible to me, the drives were inaccessible as neither a set nor individually. The data was not "vital" and the drives were reused elsewhere. Later on, I heard there was a way I could have gotten back into the drives by observing and somehow manipulating the attributes about sectors, cylinders, etc. etc, if I had recorded them in the beginning.

What is this magical data, and how do I get it?

Should a software raid array be more easily mounted under a brand new OS than my previous experience?

Also, I am assuming from the start that with software RAID, it doesn't matter if the controllers are capable of any type of RAID at all?

I have only found basic tutorials on the subject that do not address these exact concerns. Any links?

Thanks.

---

### Post by astrotech226 on 2008-02-25
Depending on how you built the software raids to start with, the only thing you really need to start up a raid5 again after an OS reload would be the config files.  You could do it by hand if you remembered the ordering but this is easier.  I would guess it would be one of the following files you'd need:

```
/etc/mdadm/mdadm.conf
/etc/raidtab
```

Having a copy of these somewhere else is helpful because you can easily access the raid if you ever boot up using a live cd.  I really like the Gentoo minimal cd to help troubleshoot issues and I've mounted up a raid built on a different os using one of those files.

If your sata controllers are giving you a bios raid, I'd avoid them if you can and use a software raid.  Here's an article explaining a little bit about the differences between hardware, software and bios raids.

[http://www.astroshapes.com/information-technology/blog/archives/14-hardware,-software-or-fake-raid.html]("http://www.astroshapes.com/information-technology/blog/archives/14-hardware,-software-or-fake-raid.html")

---

### Post by fjgaude on 2008-02-25
One other thing that has been an issue is the actual physical drive, its SN, and the name that the OS gives to it, e.g., /dev/sda1.

The command 

```
hdparm -i -v /dev/sd[nn]
```

will relate the physical to the SN for the drive. There are other ways, even GUI ways. <smile>

Now you have to vable each drive to know which is which, if you get my drift, knowing which drive to physically remove from the bay.

---

