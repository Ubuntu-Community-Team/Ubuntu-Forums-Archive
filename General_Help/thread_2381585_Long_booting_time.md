---
title: "Long booting time"
date: 2018-01-02
forum: General Help
---

### Post by lymphor on 2018-01-02
Hello,
the booting time of my Ubuntu 16.04 has become incredibly long. I'm running it on an SSD drive in dual boot with Windows 10. My current **fstab** file looks like this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=c6278bc5-5494-40d8-8ee0-54a6801842d8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd2 during installation
UUID=f5b4f0c6-cdfd-4376-adb6-685b549cac01 none            swap    sw              0       0

```

 Could anyone please help me fix this? Here is some hardware info about of my system: AMD Ryzen 1500X, 8GB RAM, 240GB SSD system drive, other 2 SATA drives for storage.
Thank you in advance to all those that will help me! :D

---

### Post by raleigh3 on 2018-01-02
Run ```
systemd-analyze blame
``` to show event times for bootup.

It will show you how much time each event is taking.

---

### Post by lymphor on 2018-01-03
**systemd-analyze blame**
         ```

        17.966s apt-daily.service
          7.318s NetworkManager-wait-online.service
          3.289s apt-daily-upgrade.service
          2.227s snapd.service
           963ms dev-sda5.device
           514ms plymouth-read-write.service
           398ms networking.service
           239ms apparmor.service
           145ms console-setup.service
           137ms lightdm.service
           136ms grub-common.service
           134ms NetworkManager.service
            98ms keyboard-setup.service
            73ms binfmt-support.service
            70ms systemd-tmpfiles-setup-dev.service
            69ms systemd-tmpfiles-setup.service
            60ms ModemManager.service
            59ms thermald.service
            58ms accounts-daemon.service
            58ms systemd-udev-trigger.service
            56ms systemd-journald.service
            55ms snap-core-3604.mount
            45ms systemd-modules-load.service
            44ms virtualbox.service
            43ms upower.service
            40ms dev-hugepages.mount
            39ms systemd-udevd.service
            39ms sys-kernel-debug.mount
            37ms irqbalance.service
            36ms udisks2.service
            34ms dev-mqueue.mount
            33ms snap-core-3748.mount
            33ms snap-vlc-65.mount
            33ms plymouth-start.service
            30ms snap-xnviewmp-2.mount
            30ms systemd-journal-flush.service
            28ms gpu-manager.service
            27ms snap-filebot-9.mount
            25ms iio-sensor-proxy.service
            25ms systemd-logind.service
            24ms apport.service
            22ms systemd-user-sessions.service
            21ms pppd-dns.service
            19ms systemd-tmpfiles-clean.service
            19ms rsyslog.service
            17ms ondemand.service
            17ms ufw.service
            17ms systemd-sysctl.service
            15ms polkitd.service
            15ms user@1000.service
            14ms dns-clean.service
            14ms colord.service
            13ms resolvconf.service
            12ms speech-dispatcher.service
            10ms avahi-daemon.service
             8ms kmod-static-nodes.service
             8ms alsa-restore.service
             6ms proc-sys-fs-binfmt_misc.mount
             6ms systemd-timesyncd.service
             6ms dev-loop1.device
             3ms systemd-remount-fs.service
             2ms dev-loop0.device
             2ms rtkit-daemon.service
             2ms systemd-update-utmp.service
             2ms dev-loop4.device
             2ms ureadahead-stop.service
             2ms systemd-update-utmp-runlevel.service
             1ms setvtrgb.service
             1ms dev-loop3.device
             1ms sys-fs-fuse-connections.mount
             1ms snapd.socket
             1ms rc-local.service
             1ms plymouth-quit-wait.service
             1ms systemd-random-seed.service
           687us dev-loop2.device
```

I don't know hot to read it, can you spot anything suspicious?

---

### Post by Autodave on 2018-01-03
What exactly do you call a long boot up?  How long?  Keep in mind that Windows doesn't really boot up any more: it just "suspends" when you turn it off.

Your list seems pretty normal to me.

You could also "suspend" the Ubuntu session instead of closing it.

---

### Post by lymphor on 2018-01-03
Windows 10 boots in about 5-7 seconds. Ubuntu was the same immediately after a fresh install, but I had to reinstall it and I also put a lot of software on it, resulting in a 1-2 minutes boot. I thought maybe my Ubuntu installation  is compromised because I noticed some suspicious messages at the end of **sudo apt-get update**:

```

Ign:1 http://dl.google.com/linux/chrome/deb stable InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Hit:3 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu xenial InRelease
Hit:4 http://download.virtualbox.org/virtualbox/debian xenial InRelease        
Hit:5 http://ro.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:6 http://ppa.launchpad.net/rebuntu16/avidemux+unofficial/ubuntu xenial InRelease
Hit:7 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:9 http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu xenial InRelease  
Get:10 http://ro.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]   
Hit:11 https://deb.opera.com/opera-stable stable InRelease                     
Hit:8 http://screenshots.getdeb.net xenial-getdeb InRelease                    
Get:12 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [62,4 kB]
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [57,6 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [51,3 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [80,2 kB]
Get:17 http://ro.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB] 
Get:18 http://ro.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [689 kB]
Get:19 http://ro.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [647 kB]
Get:20 http://ro.archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [287 kB]
Get:21 http://ro.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Get:22 http://ro.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [232 kB]
Get:23 http://ro.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [568 kB]
Get:24 http://ro.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [533 kB]
Get:25 http://ro.archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [230 kB]
Get:26 http://ro.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [185 kB]
Get:27 http://ro.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [269 kB]
Get:28 http://ro.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5.892 B]
Get:29 http://ro.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3.324 B]
Get:30 http://ro.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4.712 B]
Fetched 4.518 kB in 12s (370 kB/s)                                             
Reading package lists... Done
W:  Target Packages (apps/binary-amd64/Packages) is configured multiple  times in /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages  (apps/binary-i386/Packages) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages  (apps/binary-all/Packages) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations  (apps/i18n/Translation-en_US) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations  (apps/i18n/Translation-en) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11  (apps/dep11/Components-amd64.yml) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11-icons  (apps/dep11/icons-64x64.tar) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages  (apps/binary-amd64/Packages) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages  (apps/binary-i386/Packages) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target Packages  (apps/binary-all/Packages) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations  (apps/i18n/Translation-en_US) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target Translations  (apps/i18n/Translation-en) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11  (apps/dep11/Components-amd64.yml) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
W: Target DEP-11-icons  (apps/dep11/icons-64x64.tar) is configured multiple times in  /etc/apt/sources.list.d/getdeb.list:1 and  /etc/apt/sources.list.d/getdeb.list:2
```

---

### Post by raleigh3 on 2018-01-03
I forgot how I did it, but I was able to eliminate apt-daily.service for a time savings.

I may have found a way to delay it's starting until after bootup.

I think this is what I used.

[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

But make sure you make backups of any files you change in case it does not work !

---

### Post by lymphor on 2018-01-04
Thank you, but when I run **sudo systemctl edit apt-daily.timer** I get the image in the screenshot and I don't exactly know what to do.
[ATTACH=CONFIG]278044[/ATTACH]
 I was also not able to locate the file I would be editing. Sorry for my  lack of knowledge, maybe you could help me with some more hints? :)

---

### Post by ian-weisser on 2018-01-04
What you need to copy-and-paste is in [https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

It doesn't *disable* apt-daily.service. It works around a bug. The bug is that apt-daily.service is part of boot at all - it shouldn't be.

You should fix your apt sources. All those (W)arnings about duplicate source entries - clean those up. They are simply duplicates - delete one.

Someday, when the time comes to release-upgrade to your next release of Ubuntu, remember that you must disable all those PPAs and non-Ubuntu sources, and uninstall all the packages they provided. Return your Ubuntu system to as close to stock as possible...else you may break your system quite badly. Backup your data before starting.

---

### Post by lymphor on 2018-01-04
> **ian-weisser said:**
> What you need to copy-and-paste is in [https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

Which brings me to this other screen where I don't know how to proceed:
[ATTACH=CONFIG]278046[/ATTACH]


> **ian-weisser said:**
> 
You should fix your apt sources. All those (W)arnings about duplicate source entries - clean those up. They are simply duplicates - delete one.

Done, thank you :)

> **ian-weisser said:**
> 
Someday, when the time comes to release-upgrade to your next release of Ubuntu, remember that you must disable all those PPAs and non-Ubuntu sources, and uninstall all the packages they provided. Return your Ubuntu system to as close to stock as possible...else you may break your system quite badly. Backup your data before starting.
Thank you for the advice, I'll try to do that!

---

### Post by ian-weisser on 2018-01-04
> **lymphor said:**
> Which brings me to this other screen where I don't know how to proceed:

Look at the highlighted line on the bottom. It's prompting you for a filename to save as. If you are happy with the current name, hit <Enter>.

You will use the 'nano' editor many times as an Ubuntu user, so you may as well learn to use it. It's very easy.
There are many nano tutorials, just a search engine away. [Here's one]("https://www.youtube.com/watch?v=45KO4KO2DTo").

---

### Post by lymphor on 2018-01-04
Thank you very much, looks like it worked, even if the current booting time is not much faster :D

current **systemd-analyze blame**
```
7.256s NetworkManager-wait-online.service
          1.021s dev-sda5.device
           952ms snapd.service
           315ms media-FENICE.mount
           162ms grub-common.service
           135ms NetworkManager.service
           116ms lightdm.service
            87ms keyboard-setup.service
            77ms systemd-udev-trigger.service
            67ms accounts-daemon.service
            65ms systemd-tmpfiles-setup-dev.service
            63ms console-setup.service
            59ms apparmor.service
            57ms virtualbox.service
            56ms ModemManager.service
            56ms systemd-journald.service
            52ms systemd-journal-flush.service
            52ms thermald.service
            44ms snap-xnviewmp-2.mount
            43ms systemd-random-seed.service
            43ms systemd-logind.service
            42ms snap-core-3748.mount
            41ms upower.service
```

Thank you again for your help and your patience, you have my gratitude ):P

---

