---
title: "Case of the No-Show App"
date: 2012-12-21
forum: General Help
---

### Post by Karl10 on 2012-12-21
Hi everyone

Been running 10.10 for quite awhile with few problems, on an Asus G73JH-A1 laptop.  Wanted to upgrade, but got shot down 'cuz there ain't enough disk space to do it.

Okay.  Bought an external hard drive dock, and a 1Tb hard drive, figuring that would solve things.

Installed Mondo, went to run it... no Mondo.  Everything says it's  installed, but there's no menu icon in ANY category.

Found the files in "File System" in the usual place(s), but am unable to identify the correct executable (not the way I want to invoke the app, anyway; I want a regular menu item).

Tried using Ubuntu Software Center, Synaptic Package Manager, apt-get install, and a .deb package from the Mondo site.

Tried un-installing it and re-installing it... same result every time; it goes in, no error messages or anything... but still no Mondo.

I REEALLY want to back up my stuff to the new drive and clean house on my laptop so I can upgrade (gonna NUKE the Unity desktop, tho... seen it... hate it!)

What'm I doing wrong??

---

### Post by 2F4U on 2012-12-21
A quick Google search reveals that this application is started from a terminal:

[http://www.itworld.com/software/310388/install-mondo-rescue-utility-ubuntu-1204-or-1210](http://www.itworld.com/software/310388/install-mondo-rescue-utility-ubuntu-1204-or-1210)
[https://help.ubuntu.com/community/MondoMindi](https://help.ubuntu.com/community/MondoMindi)

---

### Post by Karl10 on 2012-12-21
Speedy reply is most appreciated.

However... neither of the links you provided applies to me.  I'm running 10.10 (Maverick Meercat), and the first link is specifically for releases 12.04 and 12.10, and the second link discusses just about every release... except mine.  Not a mention.

Trying to invoke from the terminal results in nothing but this:

[TH=4346] libmondo-tools.c->reset_bkpinfo#858: Hi
root is mounted at /dev/sda

No, Schlomo, that doesn't mean /dev/sda is the root partition. It's just a debugging message. Relax. It's part of am_I_in_disaster_recovery_mode().
[TH=4346] libmondo-devices.c->am_I_in_disaster_recovery_mode#147: Is this a ramdisk? result = 0
        [TH=4346] libmondo-tools.c->setup_tmpdir#842: Failed to create global tmp directory /97%/mondo.tmp.odNSaW for Mondo.
        [TH=4346] libmondo-files.c->register_pid#815: Unregistering PID
        [TH=4346] libmondo-files.c->register_pid#817: Error unregistering PID
running: umount /mnt/cdrom > /mondo-run-prog-thing.tmp 2> /mondo-run-prog-thing.err
--------------------------------start of output-----------------------------
umount: /mnt/cdrom: not found
--------------------------------end of output------------------------------
...ran with res=256


Any other ideas??

---

### Post by Karl10 on 2012-12-22
Really?  228 views and only one reply?

This install is becoming squirrely, and I am MOST anxious to get a ton of files offloaded so I can upgrade to a clean and more recent release.

Have had no success with Mondo, BackInTime, or any other backup program worth installing.

Gotta be someone out there who has a clue (admittedly, I don't, not anymore...)

---

### Post by sandyd on 2012-12-22
simplest way is to use rsync
```

rsync -r /path/to/source /path/to/destination
```
or rdiff-backup if you want the ability to do versioning (i.e. going back in time/revisions)
```

rdiff-backup -v5 /path/to/source /path/to/destination
```

rdiff-backup isn't included by default - you will have to install it

---

### Post by Karl10 on 2012-12-24
Thanks, sandyd!

I just bare-knuckled it; using file manager to copy to external hard drive the files I wanted to save.  I WAS going to back-up the full install (for a 100% restore, OS and all), but if I'm upgrading anyway, that probably isn't necessary anyway.

Just to be on the safe side, I'll install and use your recommendations as well.

Merry Christmas!

---

