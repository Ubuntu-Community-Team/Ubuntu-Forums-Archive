---
title: "Unable to Boot: Crash Immediately After GRUB"
date: 2012-12-10
forum: General Help
---

### Post by Martom on 2012-12-10
Hey all,

I recently installed Xubuntu 12.10 on an older laptop and while it mostly works fine, I've been having some boot issues.

Maybe a week or so ago, I suddenly couldn't boot into Xubuntu anymore. Immediately after the GRUB menu, it would crash and power down my laptop abruptly, as if I pulled out the power cord. I was still able to boot into Windows and into recovery mode. From recovery mode I tried fsck-ing things, which gave me an error about not being able to mount my /home partition. After some googling I came across this post:

[http://ubuntuforums.org/showpost.php?p=8740520&postcount=21](http://ubuntuforums.org/showpost.php?p=8740520&postcount=21)

Following these instructions, I managed to fix that issue.

The thing is, just now I tried to boot into Xubuntu and I got the same thing: immediate shutdown after GRUB. The first thing I tried, of course, was to go into my fstab again. The changes I made are still there, though, so obviously it's not the same issue. I tried fsck, but it doesn't appear to be doing anything. It tells me it finds /dev/sda6 and /dev/sda7 with some information about them, then nothing.

I don't really know how to go from here. Also, I'd like to find out why this is happening, since it wasn't a one-off glitch. I don't know what's causing these issues; everything was working just fine this morning.

Thanks.

---

### Post by Martom on 2012-12-10
In an interesting new development, Xubuntu decided to boot again. It's not crashing. However, something still seems to be off because now it has me stare at a blank screen for around ten seconds before it actually boots, which was not the case before.

Does anyone have any idea what I could do to figure out what's going on?

---

### Post by Martom on 2012-12-12
Again, Xubuntu fails to boot. Now, however, I am also unable to boot into Recovery Mode; when I try to, the laptop similarly powers down abruptly after a few dozen lines of command line output have flashed by. Windows is still booting normally.

I'm starting to suspect it's just a hardware failure. Does anyone have any insights?

---

### Post by dannyboy79 on 2012-12-12
sounds like the cpu is overheating and the computer is shutting itself off to protect itself from self frying. can you run a livecd even? run memtest if you can run a live cd. try to run a livecd and get some temperatures. oh wait, you said windows still works? if that's the case them I am not sure. can you boot into an older kernel? if you can boot into windows, use the fs-driver to mount the ext3 partition so you can access the kern.log and syslog to see if there are any errors in there to point you in an error direction. if you can't even run a livecd I would go ahead and try to re-seat the cpu's heat sink fan with new thermal paste.

---

### Post by Martom on 2012-12-12
It does sound like that, but I'd be surprised to see it overheating within seconds of me pressing the power button.

Also, indeed, Windows is booting up just fine. I can mount my Linux filesystem from Windows and it looks okay, I can access files on both partitions. I also checked the CPU temperature and it's reporting 60-65 C, which is probably not ideal and the fan might need a clean, but I don't think it could be causing my issues.

---

### Post by dannyboy79 on 2012-12-12
since windows works it's not a heating issue. are you sure it's powering off or is it just that the screen is going black or blank? have you noticed a new kernel was installed recently, can you boot into an older kernel? since you said you can access your partition from within windows, have you checked /var/log/syslog /var/log/kern.log files for errors?

---

### Post by Martom on 2012-12-13
I cleaned my fan just to be sure and, perhaps uncorrelatedly, Xubuntu booted up afterwards. The temperatures are a bit lower now, but I still don't think that was the problem.

I had a look in the syslog file and I find this on repeat:

```
Dec 11 22:41:01 MAR kernel: [22782.986989] iwl3945 0000:04:00.0: Microcode SW error detected. Restarting 0x82000008.
Dec 11 22:41:01 MAR kernel: [22782.987012] iwl3945 0000:04:00.0: Loaded firmware version: 15.32.2.9
Dec 11 22:41:01 MAR kernel: [22782.987051] iwl3945 0000:04:00.0: Start IWL Error Log Dump:
Dec 11 22:41:01 MAR kernel: [22782.987059] iwl3945 0000:04:00.0: Status: 0x000202E4, count: 1
Dec 11 22:41:01 MAR kernel: [22782.987066] iwl3945 0000:04:00.0: Desc       Time       asrtPC  blink2 ilink1  nmiPC   Line
Dec 11 22:41:01 MAR kernel: [22782.987304] iwl3945 0000:04:00.0: SYSASSERT     (0x5) 0000202693 0x008B6 0x00274 0x00320 0x04EBE 116
Dec 11 22:41:01 MAR kernel: [22782.987304]
Dec 11 22:41:01 MAR kernel: [22782.987341] iwl3945 0000:04:00.0: Error Reply type 0x00000005 cmd C_TX (0x1C) seq 0x0255 ser 0x00740000
Dec 11 22:41:01 MAR kernel: [22783.484096] iwl3945 0000:04:00.0: Error sending C_RATE_SCALE: time out after 500ms.
Dec 11 22:41:01 MAR kernel: [22783.484110] iwl3945 0000:04:00.0: Error setting HW rate table: FFFFFF92
Dec 11 22:41:01 MAR kernel: [22783.488142] iwl3945 0000:04:00.0: Can't stop Rx DMA.
Dec 11 22:41:01 MAR kernel: [22783.489965] ieee80211 phy0: Hardware restart was requested

```

The kern.log file contains the same lines. I really have no idea what this means.

---

### Post by dannyboy79 on 2012-12-13
looks like a module (windows speak, a driver) is failing to work correctly. Do you have a wifi card in this computer? DO you use wifi or are you hard wired?

As an FYI, normally when you see any error, you can google the string, "iwl3945 0000:04:00.0: Microcode SW error detected. Restarting 0x82000008" and normally you'll find other users who have had the same issue and normally find a solution.

From what I am reading this problem is related to a bug in the firmware and the iwl3945 module.  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=461924](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=461924)

this page makes it seem like you can use another module called ipw3945 for that wifi chipset. [http://forums.debian.net/viewtopic.php?p=127214](http://forums.debian.net/viewtopic.php?p=127214)

We could blacklist the problem module to make the error go away as it will fill up your log files IF it's repeating and may be what was causing your crashes.

---

### Post by Martom on 2012-12-13
Thanks for the input, danny. Yes, there's a wifi card; I hardly ever use a cable. I had a look and it seems most people just have problems connecting due to this issue, not a total failure. Also, I am not 100% sure these errors actually occur during boot, I only have an approximate idea of the times I had these issues.

I looked for more errors in the logs and found this:

```

Dec 10 09:39:20 MAR kernel: [   16.040035] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Dec 10 09:39:20 MAR kernel: [   16.058582] cfg80211: Calling CRDA to update world regulatory domain
Dec 10 09:39:20 MAR kernel: [   16.066180] acpi device:04: registered as cooling_device2
Dec 10 09:39:20 MAR kernel: [   16.066203] ACPI: Can't attach device
Dec 10 09:39:20 MAR kernel: [   16.066211] video: probe of LNXVIDEO:00 failed with error -2
Dec 10 09:39:20 MAR kernel: [   16.074684] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
Dec 10 09:39:20 MAR kernel: [   16.074690] iwl3945: Copyright(c) 2003-2011 Intel Corporation
Dec 10 09:39:20 MAR kernel: [   16.126772] ACPI Warning: 0x0000000000001060-0x000000000000107f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
```

Again, I am not sure whether these occurred during boot or not.

I just came home to find the same problems again, so I booted into Windows and had a look at the logs. Interestingly enough, there's nothing in there. I mean, nothing from just now, with the right time stamps. It seems like the logs are not even being written to before things crash.

---

### Post by Martom on 2012-12-21
I decided to just reinstall Xubuntu. I didn't have any issues for a few days, but as of just now, the problem is back. If anyone has any insight, I'd greatly appreciate it.

---

### Post by dannyboy79 on 2012-12-21
i see this EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro which can sometimes point to a dieing hard drive. Can you spot any bad sector messages in kern.log or syslog or dmesg? Also, what is the exact symptoms now after you reinstalled Xubuntu? Have you run a memtest to check that your memory is ok. Does windows still work fine with this same hardware?

---

### Post by Martom on 2012-12-21
Hey danny,

The issues are exactly as before; Windows still works fine. I also noticed a seeming pattern (not verified, just an impression): the boot failure usually appears during a cold boot, i.e. when I just turn on the machine. If I boot into Windows and then reboot into Xubuntu a few minutes later, it tends to work.

I did not see anything about bad sectors in any of the logs.

I am running a memory check right now. It looks terrible; it has checked 190 MB out of my 2 GB of RAM and it has found nearly 16 million errors, all during "Test #7 [Random number sequence]". I really don't know what this means and as it stands, it would take probably more than a day to complete this test; it's taking forever. I'll have to cancel it.

How do I find out more about these memory errors? The memory test program doesn't give much detail other than that some address is failing.

---

### Post by dannyboy79 on 2012-12-22
id say your ram is bad, not sure why windows works though.

---

### Post by Martom on 2012-12-22
It is strange. I do imagine it is a hardware problem at this point, but it is perplexing that first of all, indeed, Windows works just fine and, secondly, when Xubuntu does boot up, I have no further issues.

Well, I don't suppose there will be much more to find out about this, nor will there likely be a way to fix this, right? Apart from replacing parts.

---

### Post by dannyboy79 on 2012-12-22
yeah, if it's truely bad ram the only way to fix would be to replace them. you could try to take a stick out and run with 1 stick and run a mem test on that 1 to see if maybe theres only 1 bad stick

---

### Post by Martom on 2013-01-14
I got my hands on some RAM from another laptop, of the same model, which was broken in other ways. I stuck it into my laptop and it passes the memtests, and it has made my machine a bit snappier, but my problems persist. The machine still crashes and powers down during boot. It has started to happen - though rarely - for Windows as well.

I suppose this means that it's really not a Xubuntu issue but a hardware failure, so this is not the right forum, but since this thread is here, I will ask: does anyone know what might be failing, if not my RAM?

---

