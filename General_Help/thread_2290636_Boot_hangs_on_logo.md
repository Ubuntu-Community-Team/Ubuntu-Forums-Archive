---
title: "Boot hangs on logo"
date: 2015-08-13
forum: General Help
---

### Post by ObsequiousNewt on 2015-08-13
I'm running Kubuntu 14.10, and every time I try to boot my computer, it hangs at the logo: that is, the image pulses forever, or the dots beneath the text cycle forever, depending on whether the system decided to load the necessary graphics drivers. "Forever" here means "at least an hour so it's probably not something I can wait out".

If I boot into recovery mode, the screen that allows me to e.g. drop to root shell, fix dpkg, etc. appears. If I hit "resume" I eventually reach the point where it hangs, but now the last line is visible on the screen:
```
 * Starting  enable remaining boot-time encrypted block devices [OK]
```

If I boot normally, but edit the grub command to remove "quiet splash" (leaving "ro nomodeset nomodeset $vt_handoff" as the options), I don't quite get the same thing. The screen becomes
```
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done.
Begin: Running /scripts/local-premount ... done.
[    3.759415] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts:
(null)
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
[    4.272219] random: nonblocking pool is initialized
```

In any of these cases it is possible to modify the screen by pressing any button not in the tilde-to-control block of the keyboard (that is, escape, function keys, home/delete/stuff, prtscn/pause/scroll lock, arrows, number pad). In the first case (normal boot), it toggles between the logo and a blank screen with a blinking cursor; in the second case (recovery mode) it toggles between the log output and the logo; in the last case (no "quiet splash") it also toggles between the log output and the logo, however toggling back to the log output removes the lines beginning with numbers.

Pressing control-alt-delete will reboot the system. No other keys I have tried have any apparent effect. Shutting down the system (whether by pressing C-M-delete or holding down the power button) has no observable affect.

I cannot think of anything I would have done in my last successful boot to precipitate this occurrence.

Research has turned up things like:
[LIST]
[*]"your /etc/fstab/ is messed up": My /etc/fstab has not been modified since 2012, nor does it contain any obvious errors. 
[*]"you need to run fsck": I booted onto a livecd and ran fsck -fy /dev/sda2 (the root partition), to no result. 
[*]"you have too many items in your /tmp/ folder and it's taking a long time to remove them all": There's nothing in my /tmp/ folder. 
[*]"the file system is checking your drives": Doubtful, as what I read suggested that this could be skipped by pressing "s" or something; moreover, I tried setting the PASS argument in /etc/fstab to 0 and it didn't solve anything. 
[/LIST]
Here is my /etc/fstab (sans comment lines), before I changed the PASS argument:
```
UUID=d179208c-c5cc-4a65-bbf8-3facb631a32d /                 ext4    errors=remount-ro 0       1
UUID=5772e95f-253d-43da-b29d-68a028c3b74c none                  swap    sw             0              0
UUID=21abf3cb-028f-4781-b07a-cb01ee814caf /data/              ext4    auto         0          0
```
(/data/ is an extra partition that I made.)

I'd post my hardware information, but I tried taking the hard drive out of the computer and putting it in a very old laptop, with identical results. So it is obviously a software/firmware problem (or a drive failure.)

Is there any way to fix this?

---

