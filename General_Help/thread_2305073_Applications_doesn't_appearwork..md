---
title: "Applications doesn't appear/work."
date: 2015-12-02
forum: General Help
---

### Post by jos13 on 2015-12-02
All of a sudden I can't run apps, they don't appear on launcher, can't upgrade my system cause appears [COLOR=#ff8c00]**"error with your apt-daemon"**[/COLOR]. When I run Synaptics Package Manager it closes and shows:

[B][COLOR=#ff8c00][FONT=Ubuntu]W: Not using locking for read only lock file /var/lib/apt/lists/lock[/FONT]
[FONT=Ubuntu]W: Not using locking for read only lock file /var/lib/dpkg/lock[/FONT]
[FONT=Ubuntu]E: Unable to write to /var/cache/apt/[/FONT]
[FONT=Ubuntu]E: The package lists or status file could not be parsed or opened[/FONT][/COLOR][/B][COLOR=#2C001E][FONT=Ubuntu]
[FONT=arial]
When I run a command in terminal such as "apt-get clean" it says[/FONT][/FONT][/COLOR][COLOR=#ff8c00][FONT=Ubuntu][FONT=arial][/FONT][/FONT]**W: Not using locking for read only lock file /var/cache/apt/archives/lock.**[/COLOR] When I run apt-get update it says: [COLOR=#ff8c00][B]sudo: unable to open /var/lib/sudo/"user"/5: No such file or directory
[/B][/COLOR]
I'm using Ubuntu 15.04 in a pen drive. Have 1.4 gb remaining. Already reinstalled the system 4 times, I use it for some hours then this problem happens again.

---

### Post by slickymaster on 2015-12-02
Hi jos13, welcome to the forums.

Open a terminal window (Ctrl+Alt+T) and run the following command```
sudo mount -o remount,rw /
```Afterwards run```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by jos13 on 2015-12-02
Thanks, when I run the first code I get 
**sudo: unable to open /var/lib/sudo/arkhariel/5: No such file or directory****mount: cannot remount /dev/sdb1 read-write, is write-protected**

When I run the second code:
[B]sudo: unable to open /var/lib/sudo/arkhariel/5: No such file or directory
[/B]then starts some loading and suddenly closes terminal.

Not solved.

---

### Post by furtom on 2015-12-02
You can try:

> df -h | egrep /$
to see if the partition is full.

Also, you may be having a hard disk failure/error. You can check dmesg for info.

Try booting into a live CD and then:

> sudo fsck -rfv /dev/sdXX 
(whatever your root partition is)


See if those don't get you on the right track.

---

### Post by jos13 on 2015-12-02
Thanks, **the partition is at 74%** at the moment. Checking** dmesg** doesn't work, as the terminal suddenly closes.

New information on the problem: I reboot and curiously the system **works fine in the first 10 minutes**, then the applications stops working again.
                                                     When I try to delete a directory via terminal it says: **rm: cannot remove ‘Genymotion’: Read-only file system.**  (Genymotion is the folder I'm trying to delete).
                                                     Also I **cannot create any new folder or download archives via browser.**

---

### Post by furtom on 2015-12-02
Hmm. I'm out of new ideas... I still suspect it's either a bad drive or it's [fulling up]("http://unix.stackexchange.com/questions/113840/whats-eating-my-disk-space"). 

Check the link for ideas.

---

### Post by matt_symes on 2015-12-02
Hi

Do you have a LiveCD/USB you can boot into ?

You may be able to fix things better from a live environment.

EDIT:

Have you checked the physical cabling connecting your hard drive. Have you check the hard drive is securely attached.

I would check this first.

Kind regards

---

### Post by deadflowr on 2015-12-02
Seeing that the user is not in the /var/lib/sudo folder, are you in the sudo group at all?
Run
```
id
```
and see if sudo is listed as a group.

---

### Post by jos13 on 2015-12-03
Furtom

I ran **sudo fsck -rfv /dev/sdXX** in a live cd and found: 

[B]fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
/dev/sdc is in use.
e2fsck: Cannot continue, aborting.
/dev/sdc: status 8, rss 2760, real 0.002122, user 0.000000, sys 0.000000[/B]

Hi matt_symes I`m using a live cd now and the ubuntu that is giving me problem is in a pen drive.

Deadflowr, when I go back to the system in the pendrive I wil run** id.**

---

### Post by furtom on 2015-12-03
> **jos13 said:**
> 
I ran **sudo fsck -rfv /dev/sdXX** in a live cd and found: 

[B]fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
/dev/sdc is in use.
e2fsck: Cannot continue, aborting.** id.**

Well, the whole point of booting a live cd enviornment is for that not to happen!

Did you mount anything, even inadvertently, before trying that? Make sure you just boot from the CD and run the terminal.

---

### Post by jos13 on 2015-12-03
Hi, I booted the cd and inserted my pen drive, which contains the Ubuntu where this problem is happening. So in the place of "sdXX" I wrote "sdc" and ran the command. If I do not plug my pen drive and run the terminal which command should I type replacing sdXX? Sorry can`t understand.

---

### Post by matt_symes on 2015-12-03
Hi

> **jos13 said:**
> Furtom

I ran **sudo fsck -rfv /dev/sdXX** in a live cd and found: 

[B]fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
/dev/sdc is in use.
e2fsck: Cannot continue, aborting.
/dev/sdc: status 8, rss 2760, real 0.002122, user 0.000000, sys 0.000000[/B]

Hi matt_symes I`m using a live cd now and the ubuntu that is giving me problem is in a pen drive.

Deadflowr, when I go back to the system in the pendrive I wil run** id.**

Two things:

You are trying to run e2fsck on a drive (*sdc*). You need to run it on a partition of the drive (*sdc1*).

You need to find the *partition* where the filling system is and run e2fsck again.

Boot from the LiveCD/USB again and run e2fsck on the *partition* on the drive that is giving you problems.

```
sudo fsck -rfv /dev/sdc1
```

If you get a "drive busy" error then you need to unmount the partition.

```
sudo umount /dev/sdc1
```
[B]
Change sdc1 to point to the partition that contains the filing system you want to check.[/B]

Kind regards

---

### Post by furtom on 2015-12-03
> **jos13 said:**
> Hi, I booted the cd and inserted my pen drive, which contains the Ubuntu where this problem is happening. So in the place of "sdXX" I wrote "sdc" and ran the command. If I do not plug my pen drive and run the terminal which command should I type replacing sdXX? Sorry can`t understand.

I understand! OK. when you insert the usb stick, it's auto mounting. So you need to unmount it before you run the command.

This is easy to do with many graphical tools, however, since we are using CLI:

```
sudo umount /dev/sdXX
```

sdXX in your case seems to be sdc1 (confirm it's "1" you didn't specify)

Sorry, I forgot about the auto mount or didnt realize it was an USB stick, or whatever. this should now make progress!

EDIT: Or just do what matt_symes says. He beat me to it. :)

---

### Post by jos13 on 2015-12-09
Hi guys, unmounted the partition and the check worked. Found this:

**fsck from util-linux 2.25.2**
**e2fsck 1.42.12 (29-Aug-2014)**
**Pass 1: Checking inodes, blocks, and sizes**
**Pass 2: Checking directory structure**
**Pass 3: Checking directory connectivity**
**Pass 4: Checking reference counts**
**Pass 5: Checking group summary information**

**      140739 inodes used (28.61%, out of 491904)**
**         148 non-contiguous files (0.1%)**
**         153 non-contiguous directories (0.1%)**
**             # of inodes with ind/dind/tind blocks: 0/0/0**
**             Extent depth histogram: 124754/34**
**     1038368 blocks used (52.79%, out of 1967104)**
**           0 bad blocks**
**           1 large file**

**      108601 regular files**
**       14578 directories**
**          57 character device files**
**          25 block device files**
**           0 fifos**
**           0 links**
**       17465 symbolic links (15857 fast symbolic links)**
**           4 sockets**
**------------**
**      140730 files**
[B]/dev/sdc1: status 0, rss 5676, real 6.189682, user 0.656000, sys 0.116000
[/B]
Sorry, can`t understand this data properly, but I think the drive is good, since is written** 0 bad blocks**. Why my apps still can`t run?

---

### Post by matt_symes on 2015-12-09
Hi

The problem you have is that your root file system is being mounted read only. This is a fail safe system so that your files don't get (more) corrupted than they might already be.

There are a number of reasons for this and they include loose cabling and poor connection between the drive drive and the PC or laptop, failing hard drive (including badblocks on platters and circuitry), corrupt filing system or ext3/4 journal, failing motherboard and even inadequate power supply.

The first thing i would do is back a backup of any important files you may have in case the drive is failing.

Then i would run a SMART test on the drive from a LiveCD/USB to see what reports.

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sdX
```

where X is the drive this time and not a partition on the drive.

After the test has finished, it will take a while, enter this to get the results.

```
sudo smartctl -a /dev/sdX
```

Post the results back here.

Then i would try to get the logs files from the disk and post them here. Post the log files syslog and dmesg from the root partition on your hard drive.

There are a whole bunch of things that can cause this problem though and it may take a while to find out what is causing the problem. As you're new to the forums and potentially Ubuntu, if you need it fixed quickly then backup and reinstall. If you do want to try to fix it then check the hardware and run smartctl on the drive. You'll find plenty of people here willing to help you.

Kind regards

---

### Post by jos13 on 2015-12-10
Yes I`m new and appreciating this support, hope to contribute as well. 

When I installed smartmontools I chose the **"no cofiguration"** option in the **post-fix page** that appears. The test showed: 

[SIZE=2][B]smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.19.0-15-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

/dev/sdb: Unknown USB bridge [0x0930:0x6545 (0x110)]
Please specify device type with the -d option.

Use smartctl -h to get a usage summary[/B][/SIZE]

And when I try to get results I receive the same message.

Later I will get the **syslog **and **dsmeg**, since I think, in order to get it, I should boot from the drive where root partition is.

I already tried to** reinstall Ubuntu**, about 3 times, and the same problem continues to happen, guess I will have to fix it exploring **another alternative**. Finally we`re getting some light on this issue.

---

### Post by matt_symes on 2015-12-10
Hi

> **jos13 said:**
> Yes I`m new and appreciating this support, hope to contribute as well. 

When I installed smartmontools I chose the **"no cofiguration"** option in the **post-fix page** that appears.

This is fine.

>  The test showed: 

[SIZE=2]```
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.19.0-15-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

/dev/sdb: Unknown USB bridge [0x0930:0x6545 (0x110)]
Please specify device type with the -d option.

Use smartctl -h to get a usage summary
```[/SIZE]

Can you post a list of all the hardware (make and model) you are using Ubuntu, on especially the hard drives.

> /dev/sdb: Unknown USB bridge [0x0930:0x6545 (0x110)]

Are you trying to install Ubuntu on an external USB hard drive ? 

> I already tried to** reinstall Ubuntu**, about 3 times, and the same problem continues to happen,

If this is the third time this has happened to you then something is wrong.
[I]
Please supply as much detailed information about your setup as possible.[/I]

> Later I will get the **syslog **and **dsmeg**, since I think, in order to get it, I should boot from the drive where root partition is.

You can get them from the LiveCD/USB. Open the File manager (Nautilus usually) and click on the drive to mount it. You can then attach the files into a post on these forums from the LiveCD/USB. 


Kind regards

---

### Post by jos13 on 2016-03-11
Returning here to put a conclusion: the problem was a damaged pen drive. It was working very well, but it started to have some bad sectors in the drive.

---

