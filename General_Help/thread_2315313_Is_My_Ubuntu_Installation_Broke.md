---
title: "Is My Ubuntu Installation Broke?"
date: 2016-02-27
forum: General Help
---

### Post by Rocky_Bennett on 2016-02-27
Howdy All,
I am multi-booting several different operating systems on three different physical drives. On one SSD I have Windows 10 sitting all by itself. On a different SSD I have it divided evenly in two that holds my Linux Mint Cinnamon 17.3 and my Ubuntu 15.10. On an old hdd I have Debian 8.3.0, Kubuntu 15.10 and Linux Mint KDE 17.3. My problem concerns start up time.

All of my operating systems seem to fire right up after I select them from the Grub boot menu. I can go into any of my systems within a few seconds and actually open programs just a couple of seconds later, except Ubuntu. Where my Kubuntu (on the hdd) might take a total of 7 or 8 seconds from selecting it in the boot menu to being fully operational it usually takes Ubuntu over 90 seconds to even get to the log in screen. Besides my Windows installation, the Ubuntu installation has been on my system the longest, for at least a few months now.

Also, I keep all of my systems updated, especially my Ubuntu because I spend a lot of time using that system.

This situation is not new, it has always been this way. I just would like to know if this is normal behavior for Ubuntu or is there something wrong with my Ubuntu installation?

Thank you,

Rocky Bennett

---

### Post by DuckHook on 2016-02-27
Rocky, please hold the <Shift> key down on your next boot into Ubuntu. This will get rid of the boot overlay screen and you can see the commands that are being executed in series. You should be able to see the service that is holding up the boot process.

Usually, it will be something like a disk partition that was there at install, but has since changed UUIDs or been deleted. Correcting /etc/fstab usually solves this. Or it will be something like a missing WIFI SSID that the system is waiting 60 seconds for before it gives up and proceeds to the rest of the boot script. Blacklisting the offending module usually solves this.

You can also examine your various log files in /var/log/ and look for error or warning entries.

...and no, I wouldn't say that your install is "broken". If so, it wouldn't boot at all. But it's also not 100%.

---

### Post by Rocky_Bennett on 2016-02-28
Thank you very much for the info. I will do that and then report back.

Rocky Bennett

---

### Post by v3.xx on 2016-02-28
One other option is to run the command

```
systemd-analyze blame
```

This will also show the boot process.

---

### Post by Rocky_Bennett on 2016-02-28
I tried that shift key trick several times and the only thing I saw was Ubuntu overlay. This is what I saw when I tried that line command;


```
rocky@rocky-All-Series:~$ sudo systemd-analyze blame
[sudo] password for rocky: 
           302ms dev-sdc2.device
           271ms plymouth-quit-wait.service
           224ms plymouth-start.service
           220ms gpu-manager.service
           187ms apparmor.service
           124ms ufw.service
           107ms systemd-localed.service
            62ms systemd-udevd.service
            55ms ModemManager.service
            46ms networking.service
            45ms udisks2.service
            43ms accounts-daemon.service
            42ms NetworkManager.service
            38ms systemd-udev-trigger.service
            36ms thermald.service
            33ms systemd-journald.service
            29ms lightdm.service
            29ms console-setup.service
            25ms systemd-tmpfiles-setup-dev.service
            21ms systemd-modules-load.service
            21ms systemd-logind.service
            19ms irqbalance.service
            18ms systemd-tmpfiles-setup.service
lines 1-23...skipping...
           302ms dev-sdc2.device
           271ms plymouth-quit-wait.service
           224ms plymouth-start.service
           220ms gpu-manager.service
           187ms apparmor.service
           124ms ufw.service
           107ms systemd-localed.service
            62ms systemd-udevd.service
            55ms ModemManager.service
            46ms networking.service
            45ms udisks2.service
            43ms accounts-daemon.service
            42ms NetworkManager.service
            38ms systemd-udev-trigger.service
            36ms thermald.service
            33ms systemd-journald.service
            29ms lightdm.service
            29ms console-setup.service
            25ms systemd-tmpfiles-setup-dev.service
            21ms systemd-modules-load.service
            21ms systemd-logind.service
            19ms irqbalance.service
            18ms systemd-tmpfiles-setup.service
            18ms colord.service
lines 1-24...skipping...
           302ms dev-sdc2.device
           271ms plymouth-quit-wait.service
           224ms plymouth-start.service
           220ms gpu-manager.service
           187ms apparmor.service
           124ms ufw.service
           107ms systemd-localed.service
            62ms systemd-udevd.service
            55ms ModemManager.service
            46ms networking.service
            45ms udisks2.service
            43ms accounts-daemon.service
            42ms NetworkManager.service
            38ms systemd-udev-trigger.service
            36ms thermald.service
            33ms systemd-journald.service
            29ms lightdm.service
            29ms console-setup.service
            25ms systemd-tmpfiles-setup-dev.service
            21ms systemd-modules-load.service
            21ms systemd-logind.service
            19ms irqbalance.service
            18ms systemd-tmpfiles-setup.service
            18ms colord.service
            16ms alsa-restore.service
            15ms grub-common.service
            14ms pppd-dns.service
            14ms plymouth-read-write.service
            12ms speech-dispatcher.service
            12ms ondemand.service
            12ms systemd-timesyncd.service
            12ms rsyslog.service
            12ms apport.service
            12ms avahi-daemon.service
            12ms [EMAIL="user@119.servic"]user@119.servic[/EMAIL]e
            12ms upower.service
            12ms dns-clean.service
            12ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
            11ms kerneloops.service
            10ms polkitd.service
            10ms systemd-journal-flush.service
            10ms sys-kernel-debug.mount
             9ms systemd-update-utmp.service
             8ms systemd-setup-dgram-qlen.service
             8ms resolvconf.service
             8ms dev-mqueue.mount
             6ms systemd-random-seed.service
             6ms systemd-sysctl.service
             6ms systemd-vconsole-setup.service
             5ms [EMAIL="systemd-backlight@backlight:acpi_video0.servic"]systemd-backlight@backlight:acpi_video0.servic[/EMAIL]e
             5ms ifup-wait-all-auto.service
             5ms rc-local.service
             4ms kmod-static-nodes.service
             4ms systemd-remount-fs.service
             4ms dev-hugepages.mount
             3ms systemd-user-sessions.service
```



What do you guys see that is hanging up my Ubuntu start up?

Thanks,

Rocky

---

### Post by DuckHook on 2016-02-28
> **Rocky_Bennett said:**
> What do you guys see that is hanging up my Ubuntu start up?Out of my depth here as I am not yet familiar with systemd tools (still running 14.04). So I'm guessing at your output. I don't see any major hangs in this output. 302ms is the longest wait, but that's just 3/10 of a second. Adding up all of your load times does not come close to the 90 second wait that you are experiencing.

Did you look at your logs? Especially check boot.log, although syslog and kern.log are also useful.

---

### Post by v3.xx on 2016-02-29
DuckHook is right.  You have one fast boot according to the above.

@DuckHook
Systemd, I think, is turning out really nice.  Lots of tools :D

---

### Post by Rocky_Bennett on 2016-02-29
Thanks guys. I was also impressed by looking at those logs too, but reality is a completely different beast. I will try to generate other logs, especially a boot log. 

Rocky Bennett

---

### Post by Rocky_Bennett on 2016-03-07
Well I fixed the problem...in a way. I completely removed my installation of Ubuntu 15.10 and I installed Ubuntu 16.04 beta. Man, that thing is fast. From first pushing the restart button to getting to my log in screen is about 2 seconds, and after I enter my password I am in and up and running in another couple of seconds. Ubuntu 16.04 is the fastest Linux installation that I have on my computer, and right now I have 6 different distros running in a multi-boot situation.

---

### Post by goofprog on 2016-03-07
It is very fast if a solid state drive is used too, but a boot up time of less than a minute is just fluff to me.  I would rather have a faster OS that processes faster than faster behavior.  Good luck on your 16.04

---

### Post by Rocky_Bennett on 2016-03-07
Thanks. Yes, this is installed on a little SSD and I am really enjoying the looks and over all feel of Ubuntu 16.04. We'll see how this little beta software behaves for the next few weeks.

---

### Post by v3.xx on 2016-03-07
> **Rocky_Bennett said:**
> I installed Ubuntu 16.04 beta.

Glad it worked, others have not been so lucky.

[http://ubuntuforums.org/showthread.php?t=2312728](http://ubuntuforums.org/showthread.php?t=2312728)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

