---
title: "Lightdm crashes again, this time it hoses my machine HARD"
date: 2019-07-02
forum: General Help
---

### Post by Skaperen on 2019-07-02
*Lightdm* crashed again.  this is the *sixth* time.  the first thing i see is the _screen goes black_. after waiting about 15-20 seconds up pops a little message box saying that the display is in _low graphics mode_.  _nothing works_ for input or at least it does affect the display.  there is _no mouse pointer_.  moving it and clicking it has no effect.  typing on the keyboard has no effect.  but one thing works ... Ctrl+Alt+F1 gets me to _tty1 in text mode_ with characters *too small to read* very easily.  it is _240 columns wide_ by _67 rows high_.  so i can't do much here. i do a graceful _reboot_.  in the previous crashes the system comes back up OK.  *but not this time.*  it brings up X OK and i get the lightdm greeter OK.  but when i try to login, after a few seconds it blanks the display for about 1/4 second and the greeter is back.  every user is hosed and root is not allowed to login directly at all.  wow, _lightdm got its revenge on me_.  i try a couple more reboots and the same thing happens.  i can get to text mode, but i really can't diagnose from here (can't read the tiny text).

i have a 2nd hard drive which is the exact same size as the first and i sometimes duplicate everything from the 1st to the 2nd.  so i boot up the 2nd hard drive to do recovery, and lightdm immediately crashes.  reboot the 2nd drive again and i get that greeter problem, again.  and again. and again.

so i decide to re-install.  i arranged /home in a separate partition so i could do a re-install without losing important data.  and i have triple backups (the 2nd drive, an external USB drive, and AWS S3).  this time i decide to jump forward and i install Xubuntu 18.04 LTS (bionic) instead of 16.04.6 LTS (xenial, plus Xfce) that i had been running.  i install everything from a USB memory stick.  i do the configuration to use /dev/sda4 as /home just as i had before.  the install goes OK.  boot it up and i get the very same greeter failure loop.  and this is a fresh install!  it is sure cleverly hosed!

is there a hardware failure or is the problem in /home ??  have i really been hacked ??

#### to be continued ####

but take note that i am typing this post in from the affected laptop.  i never did need to get my spare laptop out (which has year old stuff on it).

---

### Post by Artim on 2019-07-02
Hi,

When you preserve the /home partition it not only saves your documents, music, photos, and bookmarks, but also whatever *settings* you may have messed up in your first installation.  I know this is a pain, but only save your Documents, Pictures, Music, and Videos, and perhaps your favorite bookmarks and passwords and stuff on a separate USB stick and re-install, this time *formatting* the /home partition, which has obvious preserved whatever setting is messing up.  Then copy your docs, pics, tunes, etc back.

Can you remember what setting you may have changed?

---

### Post by Skaperen on 2019-07-02
there were no settings on [FONT=courier new]/home[/FONT] (sda4).  all settings are in [FONT=courier new]/etc[/FONT] and/or [FONT=courier new]/var[/FONT] (both on sda1).  everything but user home directories are on sda1.  the size of all my [FONT=courier new]/home[/FONT] space is over 700GB.   copying that to a USB memory stick is just not practical, yet.  in a few years it probably will be.  by then, everything will be multi-TB flash drives.

so could my hardware have been hosed?  not really, because i could run the "Try Ubuntu" systems from the ISO-on-memory-stick OK.  and i also have a 3rd storage device on my laptop, a 120GB flash drive on which i installed an Ubuntu 16.04 LTS system totally independent or the other drives.  it is for very low level maintenance, such as my initial sector-by-sector copy of the whole big drive to its twin (boot sector, partition table, and both partitions).  then i can rsync after that.

so clearly it must have been [FONT=courier new]/home[/FONT].  but there are only user home directories there (no system settings).  alas, i do remember having very recently doing something very strange on one of the userids there (all but a couple of them are ones i personally use).  my big problem is that i have already wiped out my system on sda1 by having installed Xubuntu 18.02 over it.  i had a backup tree of the files (not a sector image) from sda1 over on sda4.  i tried to restore just the files to sda1 and reboot.  it hangs with some messages about bad modules. oops, i'm mixing old kernel modules with a newer kernel.  i try again (a reinstall to get the modules i needed and restore old files all over, again).  still, no good, but it gets a little further.  this time it complained about being unable to find a UUID that i didn't have. i have no idea where it got that UUID to look for, since i have nothing with it.  so i try, again, but this time apply everything to my 2nd hard drive (which Linux thinks is the 3rd ... sdc) which has not (yet) had a new system put on it.  this finally boots up and runs, despite being a few months old OS.  so /home is the problem.

now, was what i did on that one user the cause?  what i did ended up creating a massively huge subdirectory with 135000 files in it, each with long file names.  but i didn't need any of it, so i spent the next half hour removing it all.  i even did a timed sync command after it which took 35 seconds (i've seen worse). with all those files gone, i rebooted sda1 which had the Xubuntu 18.04 system back on it (the 3rd re-install).  this time it works.

so something was keeping *every* user from being able to finish logging in under lightdm (a few of them were tried in text mode and everything works fine that way) just because one user had a massively huge subdirectory.  i have no idea what it was and [FONT=courier new]/var/log/syslog[/FONT] has no clue other than really weird messages from updated and lightdm.

so now i have obliterated my 16.04 system.  if i had known the cause up front, i could have fixed it first and avoided that.  i'm pretty much stuck on 18.04 unless i want to go back to the dark ages (with regular lightdm crashes).  so i have decided to stay on Xubuntu 18.04 LTS.  maybe i'll skip 20.04 and go to 22.04.  maybe.

mostly, 18.04 works but i do have some issues ... fewer than i thought there would be.

---

### Post by Skaperen on 2019-07-02
> **Artim said:**
> When you preserve the /home partition it not only saves your documents, music, photos, and bookmarks, but also whatever *settings* you may have messed up in your first installation.

this is a common problem for people who install everything in one partition.  i split things up way back when i ran IBM mainframes.  this was the default when i did SunOS and NeXT.  then on Windows i put the system on [FONT=courier new]C:[/FONT] and the "data" on [FONT=courier new]D:[/FONT].  originally on Linux i had things split up among 5 or 6 partitions.  then i went down to 3+swap ([FONT=courier new]/boot[/FONT] was separate and had the boot loader and kernel).  now i do 2+swap ([FONT=courier new]/home[/FONT] is separate). i make sure all data is there.  in some servers i have an additional partition for databases.

system settings are not used in [FONT=courier new]/home[/FONT] except for per-user settings which now days are typically found in [FONT=courier new]~/.config[/FONT].  system level settings are usually found in [FONT=courier new]/etc[/FONT] but sometimes bulky settings (like DNS zone files) are found in [FONT=courier new]/var[/FONT].

no settings were messed up.  at first i thought something did when lightdm crashed.  now i know something that is involved when a user logs in through lightdm, not necessarily lightdm itself, is sensitive to directory sizes in user homes,other than the user being logged in.  that should not be.  nothing should be looking around unless it is hardened code.  this lets a non-root user do a host-wide denial of service.

*edit*:

now in AWS EC2, instances typically have just one partition.  managing persistent data there involves a whole different way of thinking and a whole different set of best practices.  if settings get messed up, a proper design lets you just terminate the bad instance and launch a new one.  and this can even be automated.  it is easy to have separate devices attached to potentially very large drive space (1GB to 16TB).  and you can easily have up to 16 attached drives (one of them for the system, typically 8 GB but you can make it larger).  you can even set up multiple instances of 65536 EB (Exa Byte) NFS file space and have available a virtually infinite object storage space (objects as large as 5TB, as many as you want).

---

### Post by Artim on 2019-07-03
I was referring to your home *partition*, not your home *directory*.  Faulty settings from one installation followed to the next,in whatever *partition * you didn't format for the second install (whether /data or /home or whatever you called it).

---

### Post by Skaperen on 2019-07-03
there were 3 partitions in a standard DOS partition table.  partition 4 is mounted as /home and just has home directories plus an additional temp space accessed as /home/tmp.  partition 2 is swap space.  partition 1 is the system space that was formatted,installed over, and gets mounted at /.  the only partition that system settings is stored on, and should be the only place all system programs look at for settings, is partition 1 and it was erased and installed over.

which do you mean by "home *partition*"?

---

### Post by Artim on 2019-07-04
My Xubuntu HDD has three partitions.  **/** , **linux-swap**, and **/home**.  All of my desktop settings are preserved in the **/home** partition.  This is *not Windows*, *not* a DOS partition table.

---

### Post by Skaperen on 2019-07-05
whar kind of partition table did you use?

here is my system info:
```

System:    Host: lt2a Kernel: 4.18.0-25-generic x86_64 bits: 64 gcc: 7.4.0 Desktop: Xfce 4.12.3 (Gtk 2.24.31)
           Distro: Ubuntu 18.04.2 LTS
Machine:   Device: laptop System: System76 product: Kudu Professional v: kudp1b serial: N/A
           Mobo: System76 model: Kudu Professional v: kudp1b serial: N/A
           BIOS: American Megatrends v: 1.03.05RS762 date: 06/23/2014
Battery    BAT0: charge: 60.1 Wh 100.0% condition: 60.1/62.2 Wh (97%) model: Notebook BAT status: Full
           hidpp__0: charge: 100% condition: NA/NA Wh model: Logitech Anywhere MX status: Discharging
CPU:       Quad core Intel Core i7-4710MQ (-MT-MCP-) arch: Haswell rev.3 cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 19953
           clock speeds: max: 3500 MHz 1: 1712 MHz 2: 1583 MHz 3: 1681 MHz 4: 1620 MHz 5: 1658 MHz 6: 1748 MHz
           7: 1664 MHz 8: 1610 MHz
Graphics:  Card: Intel 4th Gen Core Processor Integrated Graphics Controller bus-ID: 00:02.0
           Display Server: x11 (X.Org 1.20.1 ) drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile version: 4.5 Mesa 18.2.8 Direct Render: Yes
Audio:     Card-1 Intel 8 Series/C220 Series High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.18.0-25-generic
Network:   Card-1: Intel Wireless 7260 driver: iwlwifi bus-ID: 04:00.0
           IF: wlp4s0 state: up mac: <filter>
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 05:00.2
           IF: enp5s0f2 state: down mac: <filter>
Drives:    HDD Total Size: 2120.4GB (36.7% used)
           ID-1: /dev/sda model: HGST_HTS721010A9 size: 1000.2GB
           ID-2: /dev/sdb model: Samsung_SSD_840 size: 120.0GB
           ID-3: /dev/sdc model: HGST_HTS721010A9 size: 1000.2GB
Partition: ID-1: / size: 16G used: 7.3G (49%) fs: ext4 dev: /dev/sda1
           ID-2: /home size: 886G used: 703G (84%) fs: ext4 dev: /dev/sda4
           ID-3: swap-1 size: 17.18GB used: 0.00GB (0%) fs: swap dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 59.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 1156 Uptime: 1 day Memory: 10527.5/15960.5MB Init: systemd runlevel: 5 Gcc sys: 7.4.0
           Client: Shell (bash 4.4.191) inxi: 2.3.56 

```

---

### Post by Artim on 2019-07-05
I chose "Something Else" during the installation and made three HDD partitions:

[COLOR=#0000cd]**swap**[/COLOR] (6 GB, twice my computer's RAM),
[COLOR=#0000ff]**/ **[/COLOR](root, 40 GB), and
[COLOR=#0000ff]**/home **[/COLOR](the rest of the HDD)All of my settings are preserved in the /home partition as well as my docs, pics, tunes, bookmarks, etc. 

If I install another Linux and do not format the** [COLOR=#0000ff]/home[/COLOR]** partition, those Xubuntu settings carry over to whatever I am installing fresh.

---

### Post by Skaperen on 2019-07-05
i did the "Something Else", too.  but my sizes are different.

by "All of my settings are preserved in the /home partition" how did you go about doing that?  or do you mean "preserved" as in making a backup or copy of the settings?

---

### Post by Artim on 2019-07-06
All of *anyone's* settings are in their **/home** partition.  It's a Linux thing.  You preserved your /home partition and brought bad settings along to your new install.

---

### Post by Skaperen on 2019-07-07
personal setting are in [FONT=courier new]~/.config[/FONT] or similar places for legacy programs that don't do the dot config thing.  the system settings are mostly in [FONT=courier new]/etc[/FONT] but a few can be found in [FONT=courier new]/var[/FONT] (or other stuff like cached .deb files).  personal settings issues are generally based on major incompatible upgrades of applications.  most of them generally work (and worked for me in 16.04 -> 18.04).  it's the system settings i am concerned with most going to a major upgrade. a fresh install gets a working default system that i then modify in the way i usually do.  i've automated a lot of it. i even managed to save a copy of everything from 16.04 and might drop it into a container.  [FONT=courier new]chroot[/FONT] works on a dup of it.[FONT=courier new][/FONT]

---

### Post by Artim on 2019-07-07
You are conflating directories with partitions.

---

### Post by Skaperen on 2019-07-07
directories are important, too, to understand where, in a filesystem (residing in a partition) something is.  all these files are in directories.  that's how they have names.  we could, otherwise, have files with just numbers.  go read file 45307.

and, it matters where you mount things, too.

---

