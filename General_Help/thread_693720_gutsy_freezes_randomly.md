---
title: "gutsy freezes randomly"
date: 2008-02-11
forum: General Help
---

### Post by xjgnsdof on 2008-02-11
Hi. I notice that Gutsy will occasionally freeze, whether I'm encoding video or doing nothing at all. My computer specs are listed below. My laptop, which is far less powerful than said computer, never freezes in Gutsy, so I'm guessing that there's a hardware or driver issue. If any of you have the hardware below, in whole or in part, please let me know what kind of freeze-up issues (if any) you're experiencing in Gutsy.

---

### Post by LowSky on 2008-02-11
I would run a memory test, use the LiveCD check you BIOS to see how hot the computer is runnning at too... you might need to use more Artic Silver or Add a fan

---

### Post by apetresc on 2008-02-11
Is it a full-system freeze or an X freeze? Does Ctrl+Alt+F2 take you to a terminal?

If it is an X freeze, please paste your /var/log/Xorg.log immediately after a crash.
If it is a system freeze, please paste your /var/log/kernel.log immediately after a crash.

---

### Post by xjgnsdof on 2008-02-11
It is a system freeze. I will try the memory test, and I will post the logs when the system freezes again. Any other suggestions?

---

### Post by xjgnsdof on 2008-02-11
I just got a system freeze. I couldn't go into Terminal; the system responded to nothing but a hard reboot. Thus, I couldn't post any logs.

Furthermore, I see no "kernel.log" files in /var/log. Below are the files that I do see: 

```
acpid            btmp.1              fontconfig.log        samba
acpid.1.gz       cups                fsck                  scrollkeeper.log
acpid.2.gz       daemon.log          gdm                   scrollkeeper.log.1
acpid.3.gz       daemon.log.0        installer             scrollkeeper.log.2
acpid.4.gz       daemon.log.1.gz     kern.log              syslog
apparmor         daemon.log.2.gz     kern.log.0            syslog.0
apport.log       daemon.log.3.gz     kern.log.1.gz         syslog.1.gz
apport.log.1     daemon.log.4.gz     kern.log.2.gz         syslog.2.gz
apport.log.2.gz  debug               kern.log.3.gz         syslog.3.gz
apport.log.3.gz  debug.0             kern.log.4.gz         syslog.4.gz
apport.log.4.gz  debug.1.gz          kern.log.5.gz         syslog.5.gz
apport.log.5.gz  debug.2.gz          lastlog               syslog.6.gz
apport.log.6.gz  debug.3.gz          lpr.log               udev
apport.log.7.gz  dist-upgrade        mail.err              unattended-upgrades
apt              dmesg               mail.info             user.log
aptitude         dmesg.0             mail.log              user.log.0
aptitude.1.gz    dmesg.1.gz          mail.warn             user.log.1.gz
aptitude.2.gz    dmesg.2.gz          messages              user.log.2.gz
aptitude.3.gz    dmesg.3.gz          messages.0            user.log.3.gz
auth.log         dmesg.4.gz          messages.1.gz         wtmp
auth.log.0       dpkg.log            messages.2.gz         wtmp.1
auth.log.1.gz    dpkg.log.1          messages.3.gz         wvdialconf.log
auth.log.2.gz    dpkg.log.2.gz       messages.4.gz         Xorg.0.log
auth.log.3.gz    dpkg.log.3.gz       messages.5.gz         Xorg.0.log.old
bittorrent       dpkg.log.4.gz       news                  Xorg.20.log
boot             envy-installer.log  nvidia-installer.log  Xorg.9.log
btmp             faillog             pycentral.log         Xorg.9.log.old

```

Which one should I post? I'm going to do a memory test while the community gets back to me on this.

---

### Post by apetresc on 2008-02-11
Er, okay, so it's not a kernel.log but rather a kern.log. Although I'm not sure how those logs are rotated, depending on the number of times you've restarted since then it may be kern.0 or kern.1... attach the first two or three.

---

### Post by xjgnsdof on 2008-02-11
The kern.log file is blank, and kern.log.0 is dated November 7. I don't see anything that refers to the freeze-up today. I have, however, attached some Xorg.log.9 files. (I had to create an archive for one of them to meet the filesize cutoff).

I will have to do a memory test tonight and let it run while I'm at school tomorrow; I didn't know it would take so long. I doubt that the CPU temps are too high, as I get freeze-ups even at idle, and it's really cold in this room.

I've got more RAM than Ubuntu 32-bit Gutsy can handle. Does that have something to do with this?

---

### Post by xjgnsdof on 2008-02-11
up

---

### Post by apetresc on 2008-02-11
Doesn't look like X was the problem.

How about your /var/log/syslog file? Anything suspicious there?

---

### Post by xjgnsdof on 2008-02-11
The following is the data from my "syslog" file:

```
Feb 11 09:46:24 Gavel1 syslogd 1.4.1#21ubuntu3: restart.
Feb 11 09:46:24 Gavel1 anacron[5541]: Job `cron.daily' terminated
Feb 11 09:46:24 Gavel1 anacron[5541]: Normal exit (1 job run)
Feb 11 10:06:24 Gavel1 -- MARK --
Feb 11 10:08:55 Gavel1 NetworkManager: <debug> [1202742535.024589] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1291_aad32d3ee081bee07318b1c06e8c63a51568ef20'). 
Feb 11 10:08:55 Gavel1 NetworkManager: <debug> [1202742535.058424] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1291_aad32d3ee081bee07318b1c06e8c63a51568ef20_if0'). 
Feb 11 10:08:55 Gavel1 NetworkManager: <debug> [1202742535.059182] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5ac_1291_aad32d3ee081bee07318b1c06e8c63a51568ef20_usbraw'). 
Feb 11 10:17:01 Gavel1 /USR/SBIN/CRON[6519]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 11 10:46:24 Gavel1 -- MARK --
Feb 11 11:06:24 Gavel1 -- MARK --
Feb 11 11:17:01 Gavel1 /USR/SBIN/CRON[7184]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb 11 11:46:24 Gavel1 -- MARK --
```

---

### Post by xjgnsdof on 2008-02-11
up

---

### Post by xjgnsdof on 2008-02-12
up

---

### Post by xjgnsdof on 2008-02-12
I think that my overclocked settings have something to do with this. I've had games crash a lot in my Windows partition. Before I restore my BIOS settings to stock and re-overclock, though, I'd like a solution with less drastic effects.

---

### Post by xjgnsdof on 2008-02-15
Anybody?

---

### Post by Holonet on 2008-02-15
I haven't got a clue what the solution is, but I have had similar problems, and I have similar hardware to you.  I have an AMD X2 4200+, Gigabyte SLI board, 2GB DDR2 RAM, GeForce e-VGA 7600 GS, 250GB Maxtor SATA hard drive (7200), and it should be noted that I have NOT overclocked my processor.  I'm thinking perhaps Gutsy is having trouble with dual core?

The problem is similar...I have had complete system crashes, in which the mouse pointer will not even move.  I have also had a sort of crash that seems like an X crash where it will move, but anything I click on does nothing...  I have not tried going to a prompt like I should have :-P.  I have also had nautilus crash in a way, such that if I open a folder, it says "contents cannot be displayed," and if I kill nautilus, a window with my home folder pops up for no apparent reason, and then I can browse files again.  I have another thread on this with more detail called "Files in Gutsy "disappear."

Anyway, I'll see if I can get any of those logs now that I have a clue where to start.

I also do video encoding, and it does suck when this happens in the middle of it...especially with a slow deinterlacing filter...](*,)...  However with me as well, it does not only happen when encoding (w/ Avidemux).

---

### Post by Holonet on 2008-02-15
Ok I got a crash, system crash it is, and here is the corresponding kern.log file:

[http://www.mediafire.com/?8txenjw1yyd](http://www.mediafire.com/?8txenjw1yyd)

---

### Post by megamaced on 2008-02-16
There is a problem with the current Nvidia driver and Geforce 6 - 8 cards.

---

### Post by roaldz on 2008-02-16
Hangs are not always as bad as you think - you can reboot safely if you´re crashed: SYSRQ (near Printscr, use with ALT)+ R+E+I+S+U+B. This way it terminates all processes, syncs, umounts and reboots. No file system errors:)

---

### Post by Holonet on 2008-02-17
Hmm so Nvidia's company driver is causing the crash, or Gutsy has an issue with it (I ask because it seems prevalent in Gutsy from the threads here)?  Should I formally report a bug with this kern.log file?

---

### Post by xjgnsdof on 2008-02-20
I actually have not experienced a system crash for a good week. I attribute this to my tweaking the BIOS settings, because that's the only significant thing I can think of to happen to my rig. I'll post again if anything goes wrong...

---

### Post by xjgnsdof on 2008-02-21
Of course, the day after I post that I haven't gotten any problems, I get a problem. I guess I just have to wait for a compatible driver. Of all the luck...

---

### Post by Holonet on 2008-02-26
Phew, this is really getting on my nerves...  It's getting so I can only finish encoding a video half the time or so without it freezing.  Feels like 98, first edition.  The important question here still remains...at least in my mind.  Is this Gutsy's fault or Nvidia's fault?  And should a bug report be filed, or if one has been, should a confirmation be added with my kern.log file?  I'd really hate to see this most irritating problem in the next distro if it is something that needs to be fixed.

---

### Post by xjgnsdof on 2008-02-26
I'm getting the impression that it's Ubuntu's fault, because of driver inadequacies. The best thing we can do now is suck it up and just wait for the problem to go away. I'll report this soon, as should you (if you haven't already).

---

### Post by xjgnsdof on 2008-02-26
There's a new NVIDIA driver for Linux which, for my video card (see signature), is at the following address: [http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

I installed it by pressing Ctrl+Alt+F1, entering my username and pasword, and inputting the following commands:
```
sudo /etc/init.d/gdm stop
```

```
sudo sh /NVIDIA-Linux-x86-xxxx.run
```

Accept the license and let the driver compile the module into your kernel and reconfigure your xorg.conf file if prompted. Finally, input

```
sudo /etc/init.d/gdm start
```

I will post if this driver is any better. It was released today, so I'm definitely on my own for now.

---

### Post by Holonet on 2008-02-27
I'll lend a hand, I've just installed the new driver as well.  I'll report pleasantly should I be able to encode a day's worth of video without crashage :)

---

### Post by xjgnsdof on 2008-02-27
The NVIDIA 169.12 driver seems to be just as bad. While I haven't gotten any random freezing (yet), I get random logouts. A logout isn't quite as annoying, because I don't have to restart my PC, but that also means I can't expect anything to continue running (say, my Bittorrent client, or a video encoder). These drivers aren't getting much better...

---

### Post by Holonet on 2008-02-27
Grr, yep, add me to the pile, I can confirm the crash again.  Haven't had any random logouts, but the day is young.  Shape up, Nvidia! ](*,)

---

### Post by xjgnsdof on 2008-02-29
Just got my first random system freeze-up. As far as my other problem, I notice that if I disable my screensaver ("XAnalogTV"), the encoding finishes, though. A workaround I'm willing to accept...

---

### Post by xjgnsdof on 2008-05-09
I read on another thread that overclocking the CPU (which, in turn, overclocks the RAM) can lead to memory errors, which then causes freezing.

I downclocked my CPU slightly, and I haven't had a freeze in two days (normally, Gutsy froze every day or so). To overclockers experiencing this problem in Gutsy or Hardy, try underclocking a bit.

---

