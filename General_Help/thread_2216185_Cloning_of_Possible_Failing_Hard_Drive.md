---
title: "Cloning of Possible Failing Hard Drive"
date: 2014-04-10
forum: General Help
---

### Post by Redalien0304 on 2014-04-10
My Smart data & self test shows Pre-Fail on Several Attributes & Failed in the Past in Airflow Temperature. If someone can show me how to confirm HDD Failure. Have Tried making a backup of Ubuntu 13.10 Via Gparted Copy/Paste to different hard drive get Read errors, i ignore the read errors during copy. When i Boot the copied hard drive i it i get "bash: /usr/bin/nemo: cannot execute binary file" so cannot see my via nemo. The 2nd partition (Ubuntu 14.04) is ok nemo works just Fine can see my files when i mount the 13.10Partition.  I would like to clone the Failing hard drive if possible & be able to boot also. I have done Data Backup of my Documents & Stuff.  Any help is Appreciated.

---

### Post by papibe on 2014-04-10
Hi Redalien0304.

Here are my thoughts:
[LIST]
[*]Stop using your system immediately
[*]Use an Ubuntu live CD/USB to start recovering your files.
[*]Here's a guide of tools available:[ Data Recovery]("https://help.ubuntu.com/community/DataRecovery").
[/LIST]
Hope it helps. Let us know how it goes.
Regards.

P.S.: in case you need confirmation of the drive failure, take a look at the logs on /var/log. Both dmesg and syslog may show some clues. For example, if your partition is /dev/sda1:
```
grep sda1 /var/log/dmesg

grep sda1 /var/log/syslog
```

---

### Post by Redalien0304 on 2014-04-10
ok here is Results from grep sda1 /var/log/dmesg >  [    1.214928]  sda: sda1 sda2 sda3 sda4
[    8.072390] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   19.151823] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
& grep sda1 /var/log/syslog >  Apr 10 08:31:34 craig-ThinkPad-T61 kernel: [    8.072390] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Apr 10 08:31:34 craig-ThinkPad-T61 kernel: [   19.151823] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro 

Is using Redobackup to make an image a good idea?

---

### Post by monkeybrain20122 on 2014-04-10
To clone your system, you can try this if you can still access your file system.
Boot into the working partition (14.04), install fsarchiver from repo
```
sudo apt-get install fsarchiver
```
Now run it in 14.04, let's say the partition you want to clone is /dev/sda1 (with 13.10 on it) and you want to save the clone to your 14.04 home, let's give it a name, say ubu1310. 

Open a terminal and type
```
sudo fsarchiver -v -j2 savefs ~/ubu1310.fsa /dev/sda1
```
and just wait, shouldn't take too long. -j2 means use two threads, you can adjust it if you can use more threads. Just leave it out if you have only one.

1) /dev/sda1 has to be unmounted.
2) make sure your destination to save the clone has enough space for the content of the sources (slightly less is ok as the file is compressed, so say if your /dev/sda1 has 20G of contents, your 14.04 home, where the clone is saved, should have 20G of usable space, if not you can either save to an external drive or use a higher level of  compression [http://www.fsarchiver.org/Compression](http://www.fsarchiver.org/Compression), or you can exclude some directories by appending "--exclude=foo --exclude=bar" ... from the savefs command above (without quotes)

The actual size of the partition is not important, just the amount that is used (unlike clonzilla or Redobackup)

Will give you the instruction to restore if this works and you have gotten your new hd.

---

### Post by Redalien0304 on 2014-04-11
ok got Failing Hard Drive Cloned used Redobackup still got some errors but i geuss that is expected with a failing Drive right? Am now using a Different drive with Ubuntu 14.404 from the Bad Drive which had no Copy Errors only 13.10 partition. Used Gparted for Ubuntu 14.04 to copy to Diffrent Hdd & Redobackup for the 13.10 which had Read Errors.

---

