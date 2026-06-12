---
title: "Smart test"
date: 2016-07-26
forum: General Help
---

### Post by poorguy on 2016-07-26
Howdy All,

SMART Test in Ubuntu Mate 16.04 shows my HDD to have failed SMART test and has 238 bad sectors.

I ran the Extended SMART Test in the bios and it took 55 minutes to run and it shows my HDD 0 errors and passed.

My question is which do I believe?

Why would the HDD SMART Test in Ubuntu Mate 16.04 fail if the SMART test in bios passed?

Thanks

The PoorGuy

---

### Post by sudodus on 2016-07-26
I guess that the extented S.M.A.R.T. test is the best, but I don't know what it does, because it is built into BIOS.

You can install smartmontools and run smartctl and more or less advanced ways. That is what I think will give the most reliable results.

```
sudo apt-get install smartmontools
```

Check in the manual, which commands to run

```
man smartctl
```

You can also check and try to repair the file system and also mark the bad sectors, so that they will not be used. But if there are really 238 bad sectors, I would clone the drive to ***[COLOR="#cc0000"]save what can be saved as soon as possible[/COLOR]***. You can use ***ddrescue*** for that purpose.

When booted from another drive, unmount the ext4 partition(s) and run

```
sudo e2fsck -cf /dev/sdxy
```

Use Windows tools to repair Windows file systems (NTFS and FAT32).

See this link for more details: [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986). It works for internal drives too :-P

---

### Post by poorguy on 2016-07-26
Hey Sudodus,

Ok I will run that and see what it shows.

This is a brand new clean install could for some reason that may be damaged or corrupt and creating a problem?

Thanks

---

### Post by sudodus on 2016-07-26
It is common that computer hardware fails during the first weeks. If it survives those first weeks it will usually work for years until it fails ultimately (unless damaged by mechanical abuse or electrical shock).

---

### Post by poorguy on 2016-07-26
Hey S[COLOR=#000000]udodus,

Well the hard drive bit the dust while running smartmontools so I will have to pick through my spare parts box and find another hard drive.

Thanks for your help [/COLOR][COLOR=#000000]Sudodus.

The PoorGuy[/COLOR]

---

### Post by sudodus on 2016-07-26
I hope and wish that you had backed up all important files. The hardware is easier to replace ;-)

---

### Post by poorguy on 2016-07-26
> **sudodus said:**
> I hope and wish that you had backed up all important files. The hardware is easier to replace ;-)

Hey Sudodus,

This was a new install on my neighbors old Widows XP computer so there was nothing to save thankfully.
Yeah I always back up stuff it's to easy to not.

Thanks again.

The PoorGuy

---

### Post by sudodus on 2016-07-26
You are welcome *poorguy* :-)

---

