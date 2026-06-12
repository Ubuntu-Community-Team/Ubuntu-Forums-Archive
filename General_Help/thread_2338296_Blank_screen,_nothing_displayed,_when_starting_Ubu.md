---
title: "Blank screen, nothing displayed, when starting Ubuntu"
date: 2016-09-26
forum: General Help
---

### Post by aajax on 2016-09-26
Just installed Ubuntu 16.04.1 on a computer with a new solid state drive (SSD) along with conventional hard disk drive (HDD).  Everything looks good but the SSD is of modest size and I want to use this computer to install and run several different instances of Linux (presumably Ubuntu).  I want to continue to use the HDD and have done some research regarding configuration options for computers using SSDs.  A good bit of this is based on the idea that SSDs are great for reading data but not so great for writing data.  This leads immediately to the idea of moving the /var, /tmp, and /home directories to secondary file systems on the HDD.

With some difficulty, as discussed in [this]("https://ubuntuforums.org/showthread.php?t=2337790") post, I've now been able to relocate those directories.  However, this seems to be preventing Ubuntu from starting up correctly.  When I start Ubuntu the Ubuntu (graphic) logo (with the progress indicators) flashes briefly and then goes blank without displaying anything.  I can however press CTL+ALT+F1 and get a console to display and prompt for login.

An experiment was conducted where /var on the SSD partition being booted was emptied in preparation for mounting /var to the HDD.  Likewise, the /var/log sub-directory on the secondary HDD was emptied of all log files.  Then the system was booted and shutdown without doing anything else.    The system was then booted with System Rescue Disk to inspect the results of the experiment.  The /var directory on the SSD (which was empty prior to the experiment) now contains a single sub-directory named cache which has a single sub-directory named fontconfig.  The files found in /var/cache/fontconfig (on the booted SSD) are attached in one archive.  The /var/log directory on the HDD contains the files in another attached archive.  Note:  All of the files in both archives were therefore created by this one trivial instance of booting the computer.

I'm no expert when it comes to interpreting these log files but based on the syslog it seems pretty apparent that graphics related services failed to start.  My simple minded supposition is that the files placed in /var/cache/fontconfig needed to be subsequently read but couldn't be found after /var was relocated to the HDD.  It seems plausible that this is but another problem associated with the adoption of systemd for handling startup tasks in a more parallel manner.  You might expect that good design would involve getting the file system mounts completed before trying to do things that depend on information written to the file system during startup but I'm guessing that this is what is causing this particular problem.

As I said I'm no expert.  Does anyone have a better idea of what is causing the problem?

---

### Post by kc1di on 2016-09-26
Hi aajax, 

In order to be of much help we need to know what your video card is 
Blank screen are usually a video problem.  
could you go to a terminal and type this command and post the output here.```
inxi -F
```

---

### Post by aajax on 2016-09-27
I tried executing the referenced command but receive a message saying that "the program inxi is not installed ...".  I tried it from the console that I can get to on the target computer booted with the problem ubuntu installation.  I also tried it with the Live CD used to install the problem ubuntu installation  but received the same result.  I also tried it using the System Rescue CD but there is no such command on it either.

The computer is a Dell Vostro 220 which is a 2009 vintage machine with an Intel Dual Core (32 bit) CPU and an integrated Intel graphics adapter.

I should point out that the computer and graphics card work fine for running the Live CD.  It also worked prior to mounting /var on a secondary drive.  However, at the beginning of the ubuntu startup there is a message displayed which says "No ACPI video bus found".  For whatever that might be worth.

The syslog also reveals problems initializing the graphics.

---

### Post by aajax on 2016-09-28
Further findings:

When using function keys CTL+ALT plus one of F1, F3-6 will result in display of console (tty) sessions but using CTL+ALT+F2 displays a graphical screen with a dialogue box which contains the following message:

"The system is running in low-graphics mode.  Your screen, graphics card, and input device settings could not be detected correctly.  You will need to reconfigure these yourself."

Insofar as the computer & motherboard with integrated graphics works fine with the Live CD that was used to install the problem system this is perplexing.  Before trying to reconfigure anything myself it makes more sense to figure how to determine what settings are presently being used which might then help to figure out if it looks like there is something wrong.  Therefore, can anyone explain how to do that?

---

### Post by kc1di on 2016-09-29
you may have to install inxi  you can do that in the terminal this way:
```
sudo apt-get update
sudo apt-get install inxi 
```

There is some problems in 16.04 with the intel integrated Graphics cards.
this page may be of help - But I haven't been able to find much on this issue yet. 
[http://askubuntu.com/questions/136593/how-can-i-fix-broken-i915-drivers-for-intel-gpus]("http://askubuntu.com/questions/136593/how-can-i-fix-broken-i915-drivers-for-intel-gpus")

---

### Post by aajax on 2016-09-30
The output from running inxi -F follows:

System:    Host: Jupiter Kernel: 4.4.0-31-generic i686 (32 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: Vostro 220 Series
           Mobo: Dell model: 0P301D v: A02
           Bios: Dell v: 1.3.0 date: 06/22/2010
CPU:       Dual core Intel Core2 Duo E7500 (-MCP-) cache: 3072 KB 
           clock speeds: max: 2928 MHz 1: 2128 MHz 2: 2662 MHz
Graphics:  Card: Intel 4 Series Integrated Graphics Controller
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1280x1024@60.02hz
           GLX Renderer: Mesa DRI Intel G45/G43 x86/MMX/SSE2
           GLX Version: 2.1 Mesa 11.2.0
Audio:     Card Intel 82801JI (ICH10 Family) HD Audio Controller
           driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-31-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp2s0 state: up speed: 1000 Mbps duplex: full
           mac: 00:24:e8:25:b3:1b
Drives:    HDD Total Size: 570.1GB (0.9% used)
           ID-1: /dev/sda model: Samsung_SSD_850 size: 250.1GB
           ID-2: /dev/sdb model: WDC_WD3200AAKS size: 320.1GB
Partition: ID-1: / size: 77G used: 4.4G (6%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 0.01GB used: 0.01GB (85%) fs: swap dev: /dev/sdb5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 203 Uptime: 53 min Memory: 588.5/1979.3MB
           Client: Shell (bash) inxi: 2.2.35

---

### Post by aajax on 2016-09-30
Finally success but with some doubt about precisely what went wrong.

As described above the problem seemed to be caused by the relocation of /var.  Given the observation that starting the system caused a few files to be written into an empty /var on the systems root partition/drive prior to completing the mounts it was determined that using a configuration that did not attempt to relocate those files might be a good idea.  Therefore, a directory named /var2 was created with a path of /var2/cache/fontconfig into which the files from /var/cache/fontconfig were copied.  Then the path /var/cache/fontconfig was changed to be a symbolic link referencing /var2/cache/fontconfig and the new contents of /var copied to the secondary (hard) drive where it was desired to locate /var.  In that effectively moving /var from the SSD used to boot the system to a secondary HDD which was preferred for files that are frequently written.  This works but curiously the files thought to be problematic that are now contained within the /var2/cache/fontconfig directory appear not to have been altered during the most recent boot.  As result it now appears as though this problem may only arise when the system is in certain states when those files are created.

To be sure this is a very convoluted solution to a problem that ought not exist.  It would seem to me that /var is used for data that ought to be relocatable and thus when the system starts the mounts required to do so ought to be completed prior to the system becoming dependent on files that have been written to it.  Possibly someone should factor this into future system design.

---

