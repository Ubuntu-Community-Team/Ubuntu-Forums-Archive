---
title: "[SOLVED] kjournald and pdflush constantly writing to HD"
date: 2008-06-18
forum: General Help
---

### Post by sebrock on 2008-06-18
I have a 2.5" 40GB HD (new) in my frontend for mythtv (using mythbuntu). I have before used 7.10 aswell. The following problem is new to the Hardy release.

The problem is that kjournald and pdflush is constantly writing to my HD. I'm talking maybe 1-2 times/sec. This will in the end dramaticly decrease the life of my HD (and its just plain irritating to watch). Now my system is fairly new with 1GB of RAM, so in theory I would easy fit the whole OS in there. Now I have tried mounting my ext3 filesystem with "noatime" with no results at all.

Here is a output of my logs (just a few seconds) when I echo 1 >/proc/sys/vm/block_dump:

```

[  644.768128] syslogd(4911): dirtied inode 1515680 (syslog) on sda1
[  644.768137] syslogd(4911): dirtied inode 1515668 (kern.log) on sda1
[  644.768145] syslogd(4911): dirtied inode 1515668 (kern.log) on sda1
[  644.768153] syslogd(4911): dirtied inode 1515663 (debug) on sda1
[  644.768160] syslogd(4911): dirtied inode 1515663 (debug) on sda1
[  644.769718] kjournald(2473): WRITE block 29096 on sda1
[  644.769824] kjournald(2473): WRITE block 29104 on sda1
[  644.769859] kjournald(2473): WRITE block 29112 on sda1
[  644.769883] kjournald(2473): WRITE block 29120 on sda1
[  644.770001] kjournald(2473): WRITE block 29128 on sda1
[  644.770553] kjournald(2473): WRITE block 29136 on sda1
[  649.756681] pdflush(174): WRITE block 48742856 on sda1
[  649.756706] pdflush(174): WRITE block 48742752 on sda1
[  649.756722] pdflush(174): WRITE block 48742640 on sda1
[  649.757104] syslogd(4911): dirtied inode 1515680 (syslog) on sda1
[  649.757114] syslogd(4911): dirtied inode 1515680 (syslog) on sda1
[  649.757119] syslogd(4911): dirtied inode 1515680 (syslog) on sda1
[  649.757128] syslogd(4911): dirtied inode 1515668 (kern.log) on sda1
[  649.757135] syslogd(4911): dirtied inode 1515668 (kern.log) on sda1
[  649.757139] syslogd(4911): dirtied inode 1515668 (kern.log) on sda1
[  649.757147] syslogd(4911): dirtied inode 1515663 (debug) on sda1
[  649.757153] syslogd(4911): dirtied inode 1515663 (debug) on sda1
[  649.757157] syslogd(4911): dirtied inode 1515663 (debug) on sda1
[  649.759031] kjournald(2473): WRITE block 29144 on sda1
[  649.759039] kjournald(2473): WRITE block 29152 on sda1
[  649.759250] kjournald(2473): WRITE block 29160 on sda1
[  674.706988] pdflush(174): WRITE block 48742688 on sda1
[  674.707320] kjournald(2473): WRITE block 48742752 on sda1
[  674.707331] kjournald(2473): WRITE block 48742856 on sda1
[  674.707337] kjournald(2473): WRITE block 48742640 on sda1
[  674.707441] kjournald(2473): WRITE block 48742864 on sda1
[  674.707498] kjournald(2473): WRITE block 48742648 on sda1
[  674.710272] kjournald(2473): WRITE block 29168 on sda1
[  674.710282] kjournald(2473): WRITE block 29176 on sda1
[  674.710288] kjournald(2473): WRITE block 29184 on sda1
[  674.710292] kjournald(2473): WRITE block 29192 on sda1
[  674.710297] kjournald(2473): WRITE block 29200 on sda1
[  674.710817] kjournald(2473): WRITE block 29208 on sda1
[  679.698030] pdflush(174): WRITE block 48742760 on sda1
[  679.698056] pdflush(174): WRITE block 48742864 on sda1
[  679.698073] pdflush(174): dirtied inode 1515663 (debug) on sda1
[  679.698077] kjournald(2473): WRITE block 48742752 on sda1
[  679.698086] kjournald(2473): WRITE block 48742648 on sda1
[  679.698452] syslogd(4911): dirtied inode 1515680 (syslog) on sda1
[  679.698464] syslogd(4911): dirtied inode 1515680 (syslog) on sda1
[  679.698473] syslogd(4911): dirtied inode 1515668 (kern.log) on sda1
[  679.698481] syslogd(4911): dirtied inode 1515668 (kern.log) on sda1
[  679.698489] syslogd(4911): dirtied inode 1515663 (debug) on sda1
[  679.698496] syslogd(4911): dirtied inode 1515663 (debug) on sda1
[  679.700527] kjournald(2473): WRITE block 29216 on sda1
[  679.700537] kjournald(2473): WRITE block 29224 on sda1
[  679.700558] kjournald(2473): WRITE block 29232 on sda1
[  679.700599] kjournald(2473): WRITE block 29240 on sda1
[  679.700640] kjournald(2473): WRITE block 29248 on sda1
[  679.701080] kjournald(2473): WRITE block 29256 on sda1
[  684.687099] pdflush(174): WRITE block 48742760 on sda1
[  684.687663] kjournald(2473): WRITE block 48742648 on sda1
[  684.687669] syslogd(4911): dirtied inode 1515680 (syslog) on sda1
[  684.687675] kjournald(2473): WRITE block 48742864 on sda1
[  684.687678] syslogd(4911): dirtied inode 1515680 (syslog) on sda1
[  684.687683] syslogd(4911): dirtied inode 1515680 (syslog) on sda1
[  684.687695] syslogd(4911): dirtied inode 1515668 (kern.log) on sda1
[  684.687702] syslogd(4911): dirtied inode 1515668 (kern.log) on sda1
[  684.687739] pdflush(174): dirtied inode 1515663 (debug) on sda1
[  684.688124] syslogd(4911): dirtied inode 1515663 (debug) on sda1
[  684.690001] kjournald(2473): WRITE block 29264 on sda1
[  684.690010] kjournald(2473): WRITE block 29272 on sda1
[  684.690325] kjournald(2473): WRITE block 29280 on sda1
[  707.379635] kjournald(2473): WRITE block 48742760 on sda1
[  707.379650] kjournald(2473): WRITE block 48742864 on sda1
[  707.379657] kjournald(2473): WRITE block 48742648 on sda1
[  707.379662] kjournald(2473): WRITE block 48742872 on sda1
[  707.379668] kjournald(2473): WRITE block 48743232 on sda1
[  707.379704] bash(6094): READ block 65253344 on sda1
[  707.382212] kjournald(2473): WRITE block 29288 on sda1
[  707.382221] kjournald(2473): WRITE block 29296 on sda1
[  707.382227] kjournald(2473): WRITE block 29304 on sda1
[  707.382231] kjournald(2473): WRITE block 29312 on sda1
[  707.382235] kjournald(2473): WRITE block 29320 on sda1
[  707.382240] kjournald(2473): WRITE block 29328 on sda1
[  707.382244] kjournald(2473): WRITE block 29336 on sda1
[  707.382248] kjournald(2473): WRITE block 29344 on sda1
[  707.382252] kjournald(2473): WRITE block 29352 on sda1
[  707.382256] kjournald(2473): WRITE block 29360 on sda1
[  707.414192] bash(6094): dirtied inode 2032503 (tail) on sda1
[  707.414384] tail(6094): READ block 65253376 on sda1
[  707.414457] tail(6094): READ block 65253384 on sda1
[  707.414463] tail(6094): READ block 65253392 on sda1
[  707.414470] tail(6094): READ block 65253400 on sda1
[  707.414474] tail(6094): READ block 65253408 on sda1
[  707.414479] tail(6094): READ block 65253416 on sda1
[  707.414483] tail(6094): READ block 65253424 on sda1
[  707.414488] tail(6094): READ block 65253432 on sda1
[  707.418243] kjournald(2473): WRITE block 29368 on sda1
[  709.637376] pdflush(174): WRITE block 48742816 on sda1
[  712.547577] kjournald(2473): WRITE block 48742760 on sda1
[  712.547591] kjournald(2473): WRITE block 48742872 on sda1
[  712.547598] kjournald(2473): WRITE block 48743232 on sda1
[  712.547603] kjournald(2473): WRITE block 48742768 on sda1
[  712.550071] kjournald(2473): WRITE block 29376 on sda1
[  712.550080] kjournald(2473): WRITE block 29384 on sda1
[  712.550085] kjournald(2473): WRITE block 29392 on sda1
[  712.550088] kjournald(2473): WRITE block 29400 on sda1
[  712.550093] kjournald(2473): WRITE block 29408 on sda1
[  712.550097] kjournald(2473): WRITE block 29416 on sda1
[  712.550437] kjournald(2473): WRITE block 29424 on sda1

```

There are a few posts on the same matter in the forums, however nothings seems to help me. As I said, 7.10 was no problem at all with this so something must have changed to the worse. All help is highly appreciated. Thanks.

---

### Post by sdennie on 2008-06-18
While this behavior may be annoying, it shouldn't shorten the life of the disk by an appreciable amount (unless it's causing Load_Cycle_Count problems).  If you really want to disable these disk accesses you can increase the ext3 journal commit time and some kernel parameter.  If the system shuts down unexpectedly you will lose a lot more data than you would with the default but, if the machine is mostly a read only media server, that shouldn't be an issue.

Based on your post I'm going to assume you know how to add mount options but, if that's not correct, I'll be happy to go through it step by step.  Basically, you'll need to add a commit=num_secs mount option to each ext3 filesystem.  num_secs by default is 5 but, setting it to something like 300 or 600 (5 and 10 minutes respectively) should be just fine (I use commit=600 when on battery power and have never had any problem).

To slow down pdflush activity, edit (with sudo) /etc/sysctl.conf and add the following lines:

```

vm.dirty_ratio = 40
vm.dirty_background_ratio = 1
vm.dirty_writeback_centisecs = 30000

```

These are again settings I use while on battery power and it drastically reduces disk activity.

It's possible to get these settings working without rebooting but, in this case, it's probably easiest to just reboot.

Hope that helps.

---

### Post by sebrock on 2008-06-18
Thank you!

I don't know if you are involved with Mythbuntu in any way but I find it strange that 7.10 does not at all have this behaviour? Something must have changed in kernel to make this happen?

Also, as I understand it pdflush is used for:

- When free memory shrinks below a specified threshold, the kernel must write dirty data back to disk to free memory.

- When dirty data grows older than a specific threshold, sufficiently old data is written back to disk, to ensure that dirty data does not remain dirty indefinitely.

Now pdflush starts hitting my HD as soon as I boot. TOP shows that no swap is being used at all and there is plenty of free memory to use. So why is pfdlush in such high activity already, is there any real need for this?

Please explain for me the behaviour and why it starts as soon as I boot and continues on a totally idle system? Thank you!

---

### Post by sdennie on 2008-06-18
I'm not involved in Mythbuntu.  I'm just some guy who has an unhealthy obsession with laptop power savings (which applies in this case).

The big thing about the pdflush change is that you are telling it to wakeup and flush stuff far less often (every 5 minutes).  By default, this, like the journal commit time, is set to 5 seconds.

One caveat that I forgot to mention about these settings is that they decrease disk activity to such a point that your disk may actually completely spin down from time to time.  If you find that to be the case (you may not if you are using a desktop disk) and the spinup time causes glitches in movies, you can disable the spindown with:

```

sudo hdparm -S240 /dev/sda

```

That sets the idle->spindown time to 20 minutes which, based on other settings, means it will never happen.  You'd have to add that to /etc/rc.local or edit /etc/hdparm.conf to make that setting permanent across reboots.

---

### Post by sebrock on 2008-06-18
Ok. Well you are right, I use a 2.5" HD, which I guess is called laptop HD these days. I only have it to boot mythbuntu. All media etc resides on nfs mounts on a backend server. So spindown is no problem for me really. Actually I would be happy if the OS just gets read into memory and stays there, just making smaller writes to HD when it actually needs it. The reason is that this is a frontend and it would look nice if it was as far from a standard computer as possible and more or less like the killer media player I would like it to be ;)

All your advice is highly appreciated, however:

As I stated the WRITES by pdflush and kjournald is 1-2 times every second. This is far from default 5 seconds. So something must be causing this, am I right?

---

### Post by sdennie on 2008-06-18
> **sebrock said:**
> Ok. Well you are right, I use a 2.5" HD, which I guess is called laptop HD these days. I only have it to boot mythbuntu. All media etc resides on nfs mounts on a backend server. So spindown is no problem for me really. 


It may be an issue in that the disk spinup usually makes a high pitched whine as it's spinning up.  If you don't notice it, you should be fine.

> 
Actually I would be happy if the OS just gets read into memory and stays there, just making smaller writes to HD when it actually needs it. The reason is that this is a frontend and it would look nice if it was as far from a standard computer as possible and more or less like the killer media player I would like it to be ;)


This seems more or less possible but, I'm not completely sure how you'd go about it.  I'd see if you can find a howto.

> 
As I stated the WRITES by pdflush and kjournald is 1-2 times every second. This is far from default 5 seconds. So something must be causing this, am I right?

Well, this might be slightly misleading using the block_dump because the syslog writes of the block dump are probably triggering more writes than a truly idle system would generate.

---

### Post by sebrock on 2008-06-19
Ok, I know in my first post the paste included syslogd. However the constant 1-2 times/second blinking occurs even if not enabled block_dump to log. And for the most recent tests I killed syslogd first. And also 7.10 had no problems with this using the same defaults a normal installation would do.

So I still can't rest my head here? I smell something fishy!

---

### Post by sdennie on 2008-06-19
I'm not sure why you'd see a difference between 7.10 and 8.04 on these things unless Mythbuntu is explicitly setting them to lower than default.  The only change to pdflush related stuff I can think of is that by default vm.dirty_ratio and vm.dirty_background_ration were changed from something like 40/10 to 10/5 but, I believe that was done in kernel 2.6.22.  I just checked a clean 7.10 VM and the settings were 10/5 and 500 centisecs (ext3 journal commit was 5 seconds too) which should be identical to 8.04.  I'm not sure why you'd see so much more disk activity in 8.04.

---

### Post by sebrock on 2008-06-26
I tried all the above and more to no avail. But then I opened up my case and disconnected that DVD-RW I recently installed. By some mysterious way the HD LED keeps blinking because of something happening with the DVD-RW. Why i have no idea... anyway I call this SOLVED now.

---

### Post by sdennie on 2008-06-26
You might be able to keep the dvd connected and decrease the HD lights using:

```

sudo hal-disable-polling --device /dev/scd0

```

What that does is prevent the machine from constantly looking to see if there is a CD in the drive.  I'm not sure if it will help in this case but, it may be worth a try.  Also, if you do this, CDs will no longer auto-mount and you'll have to manually mount them (If mythbuntu is built on gnome then it's as easy as starting nautilus and mounting it).

Also, I answered a question similar to yours several times in the last week so, I wrote a more formal tutorial here: [http://ubuntuforums.org/showthread.php?t=839998](http://ubuntuforums.org/showthread.php?t=839998).  Someone pointed out that the sysctl.conf settings probably aren't working in Hardy so, you may want to look through the end of that guide.

---

