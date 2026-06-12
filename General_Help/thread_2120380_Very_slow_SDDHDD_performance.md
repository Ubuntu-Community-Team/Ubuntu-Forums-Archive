---
title: "Very slow SDD/HDD performance"
date: 2013-02-26
forum: General Help
---

### Post by jazzgossen on 2013-02-26
My fresh Kubuntu 12.10 installation often (but not always) "blocks" when doing things like "sudo apt-get update" and often spends several minutes on "Reading package lists". Other things that take unusally long is the linking stage after compiling programs.

My setup and symptoms are similar as the ones in [this thread]("http://ubuntuforums.org/showthread.php?t=2104709").
I have a Dell Precision M4700, with one SSD and one HDD. Root is mounted on the SSD, and /home and /var are mounted on the HDD. I have /tmp mounted as tmpfs. 

Any suggestions?

---

### Post by dabl on 2013-02-26
The lags that happen during "apt-get update" and "apt-get upgrade" are not hardware-related, in all likelihood, they reflect congestion or lags at the repository server.  I'm not sure about the linking issue. What makes you attribute the lag to hdd or ssd performance?  Have you used hdparm to test the speed of your ssd and hdd?

```
sudo hdparm -tT /dev/sda
```

If the speed figures are respectable (google will help you with that), then you can safely turn your attention to some other source of delay in linking.

---

### Post by jazzgossen on 2013-02-27
Thanks for your reply.

Running hdparm -tT gives me reasonable results, I think: cached reads are around 4000 MB/s and buffered reads 100 MB/s for the HDD, and for the SSD I get between 4000 and 11000 MB/s cached reads, and 258 MB/s buffered reads.

However, I don't think that the "Reading package lists" delay is related to network lag. I just tried "time sudo apt-get update", and it fetched all the data in 5 seconds, and while I'm writing this, it is slowly making its way through reading the downloaded package lists (currently at 7%, and I guess it will be done in a few minutes.)

KDE's system load applet shows around 40% CPU time spent in I/O wait. A weird thing is that I don't see that when running htop. The line for "apt-get update" shows zero in the IO column.

I hear a bit of intermittent HDD activity while doing this. I'm not sure which process is doing it though. Since only /home and /var are mounted on the HDD, I would assume that apt-get doesn't need to access the HDD at all.

---

### Post by jazzgossen on 2013-02-27
Update: apt-get update just finished, and the result of "time sudo apt-get update" is 

real    34m36.434s
user    0m28.938s
sys     0m7.140s

---

### Post by jazzgossen on 2013-02-27
I just learned that "time" can output a lot of other information as well. I timed "apt-get update" again, but this time with some more output. I've pasted the output below. I'm not sure what to make of this, though --- whether the volontary and involontary context switches are a problem, for example.

Anyway, the fact that the process only spends seconds in user and kernel mode, while the wall-clock time is 28 minutes, is puzzling to me.

```
> 'time' -f "%E real, %U user, %S sys, %F faults, %I inputs, %O outputs, %R minor faults, %W swap, %c invol. cntx-switch, %w vol. cntx-switch" sudo apt-get update
[sudo] password for martin: 
Ign http://se.archive.ubuntu.com quantal InRelease
Ign http://deb.opera.com stable InRelease                                                                                                                                                    
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                                               
Hit http://repository.spotify.com stable InRelease                                                                                                                                           
Hit http://deb.opera.com stable Release.gpg                                                                                                                                                  
Hit http://deb.opera.com stable Release                                                                                                                                                      
Ign http://ppa.launchpad.net precise InRelease                                                                                                                                               
Ign http://extras.ubuntu.com quantal InRelease                                                                                                                                               
Hit http://deb.opera.com stable/non-free i386 Packages                                                                                                                                       
Hit http://repository.spotify.com stable/non-free Sources                                                                                                                                    
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                                               
Hit http://extras.ubuntu.com quantal Release.gpg                                                                                                                                             
Ign http://se.archive.ubuntu.com quantal-updates InRelease                                                                                                                                
Hit http://repository.spotify.com stable/non-free i386 Packages                                                                                                     
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                      
Ign http://ppa.launchpad.net quantal InRelease                                                                                                                      
Ign http://se.archive.ubuntu.com quantal-backports InRelease                                                                                                        
Ign http://security.ubuntu.com quantal-security InRelease                                                                              
Hit http://ppa.launchpad.net quantal Release.gpg                                                                                       
Hit http://extras.ubuntu.com quantal Release                                                                                           
Hit http://se.archive.ubuntu.com quantal Release.gpg                                                                                                          
Hit http://ppa.launchpad.net precise Release.gpg                                                                                                              
Hit http://se.archive.ubuntu.com quantal-updates Release.gpg                                                                            
Hit http://ppa.launchpad.net quantal Release.gpg                                                                                       
Hit http://extras.ubuntu.com quantal/main Sources                                                                                      
Get:1 http://security.ubuntu.com quantal-security Release.gpg [933 B]                                                                  
Hit http://ppa.launchpad.net quantal Release.gpg                                                                                                                        
Hit http://se.archive.ubuntu.com quantal-backports Release.gpg                                                                         
Ign http://deb.opera.com stable/non-free Translation-en_US                                                                             
Ign http://linux.dropbox.com precise InRelease                                                                                         
Hit http://extras.ubuntu.com quantal/main i386 Packages                                                                                
Ign http://deb.opera.com stable/non-free Translation-en                                                                                
Hit http://se.archive.ubuntu.com quantal Release                                                                                       
Hit http://ppa.launchpad.net quantal Release.gpg                                                                                                              
Hit http://se.archive.ubuntu.com quantal-updates Release                                                                                                      
Hit http://ppa.launchpad.net quantal Release                                                                                                                  
Get:2 http://security.ubuntu.com quantal-security Release [49.6 kB]                                                                                           
Hit http://se.archive.ubuntu.com quantal-backports Release                                                                                                              
Hit http://ppa.launchpad.net precise Release                                                                                                     
Hit http://ppa.launchpad.net quantal Release                                                                                                                            
Hit http://se.archive.ubuntu.com quantal/main Sources                                                                                                                   
Hit http://ppa.launchpad.net quantal Release                                                                                                                            
Hit http://se.archive.ubuntu.com quantal/restricted Sources                                                                                                             
Get:3 http://linux.dropbox.com precise Release.gpg [489 B]                                                                                                              
Hit http://ppa.launchpad.net quantal Release                                                                                                                
Ign http://repository.spotify.com stable/non-free Translation-en_US                                                                                                     
Hit http://ppa.launchpad.net quantal/main Sources                                                                                                
Ign http://repository.spotify.com stable/non-free Translation-en                                                           
Hit http://se.archive.ubuntu.com quantal/universe Sources                                                                  
Ign http://extras.ubuntu.com quantal/main Translation-en_US                                                          
Hit http://ppa.launchpad.net quantal/main i386 Packages                                     
Hit http://se.archive.ubuntu.com quantal/multiverse Sources                                 
Get:4 http://linux.dropbox.com precise Release [2,603 B]                                    
Ign http://extras.ubuntu.com quantal/main Translation-en                                                                     
Get:5 http://security.ubuntu.com quantal-security/main Sources [33.5 kB]                    
Hit http://se.archive.ubuntu.com quantal/main i386 Packages                                          
Hit http://ppa.launchpad.net precise/main Sources                                                    
Hit http://se.archive.ubuntu.com quantal/restricted i386 Packages              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Hit http://se.archive.ubuntu.com quantal/universe i386 Packages                
Get:6 http://linux.dropbox.com precise/main i386 Packages [1,148 B]                                               
Hit http://ppa.launchpad.net quantal/main Sources                                                                             
Get:7 http://security.ubuntu.com quantal-security/restricted Sources [14 B]                 
Hit http://se.archive.ubuntu.com quantal/multiverse i386 Packages                                                      
Hit http://ppa.launchpad.net quantal/main i386 Packages                                     
Get:8 http://security.ubuntu.com quantal-security/universe Sources [15.5 kB]                                       
Hit http://ppa.launchpad.net quantal/main Sources                                                    
Hit http://ppa.launchpad.net quantal/main i386 Packages                                                           
Hit http://se.archive.ubuntu.com quantal/main Translation-en                                                      
Get:9 http://security.ubuntu.com quantal-security/multiverse Sources [700 B]                
Hit http://se.archive.ubuntu.com quantal/multiverse Translation-en                                                
Hit http://ppa.launchpad.net quantal/main Sources                                           
Hit http://ppa.launchpad.net quantal/main i386 Packages               
Hit http://se.archive.ubuntu.com quantal/restricted Translation-en    
Get:10 http://security.ubuntu.com quantal-security/main i386 Packages [90.5 kB]
Hit http://se.archive.ubuntu.com quantal/universe Translation-en                                      
Hit http://se.archive.ubuntu.com quantal-updates/main Sources                                         
Hit http://se.archive.ubuntu.com quantal-updates/restricted Sources              
Hit http://se.archive.ubuntu.com quantal-updates/universe Sources                
Hit http://se.archive.ubuntu.com quantal-updates/multiverse Sources              
Hit http://se.archive.ubuntu.com quantal-updates/main i386 Packages              
Hit http://se.archive.ubuntu.com quantal-updates/restricted i386 Packages        
Hit http://se.archive.ubuntu.com quantal-updates/universe i386 Packages          
Hit http://se.archive.ubuntu.com quantal-updates/multiverse i386 Packages        
Get:11 http://security.ubuntu.com quantal-security/restricted i386 Packages [14 B]                                  
Hit http://se.archive.ubuntu.com quantal-updates/main Translation-en                                                       
Get:12 http://security.ubuntu.com quantal-security/universe i386 Packages [42.3 kB]           
Hit http://se.archive.ubuntu.com quantal-updates/multiverse Translation-en                                                    
Hit http://se.archive.ubuntu.com quantal-updates/restricted Translation-en                                                    
Hit http://se.archive.ubuntu.com quantal-updates/universe Translation-en                                            
Hit http://se.archive.ubuntu.com quantal-backports/main Sources                               
Get:13 http://security.ubuntu.com quantal-security/multiverse i386 Packages [1,397 B]         
Hit http://se.archive.ubuntu.com quantal-backports/restricted Sources                                                            
Hit http://se.archive.ubuntu.com quantal-backports/universe Sources                           
Hit http://se.archive.ubuntu.com quantal-backports/multiverse Sources                         
Hit http://se.archive.ubuntu.com quantal-backports/main i386 Packages                         
Hit http://se.archive.ubuntu.com quantal-backports/restricted i386 Packages                                         
Hit http://se.archive.ubuntu.com quantal-backports/universe i386 Packages                                           
Hit http://se.archive.ubuntu.com quantal-backports/multiverse i386 Packages                   
Hit http://security.ubuntu.com quantal-security/main Translation-en                           
Hit http://se.archive.ubuntu.com quantal-backports/main Translation-en                        
Hit http://se.archive.ubuntu.com quantal-backports/multiverse Translation-en                                        
Hit http://se.archive.ubuntu.com quantal-backports/restricted Translation-en                
Hit http://se.archive.ubuntu.com quantal-backports/universe Translation-en
Hit http://security.ubuntu.com quantal-security/multiverse Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US                                 
Ign http://ppa.launchpad.net quantal/main Translation-en                                    
Ign http://linux.dropbox.com precise/main Translation-en_US           
Ign http://ppa.launchpad.net precise/main Translation-en_US           
Ign http://ppa.launchpad.net precise/main Translation-en              
Ign http://ppa.launchpad.net quantal/main Translation-en_US           
Ign http://linux.dropbox.com precise/main Translation-en              
Ign http://ppa.launchpad.net quantal/main Translation-en              
Hit http://security.ubuntu.com quantal-security/restricted Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en_US           
Hit http://security.ubuntu.com quantal-security/universe Translation-en
Ign http://ppa.launchpad.net quantal/main Translation-en
Ign http://se.archive.ubuntu.com quantal/main Translation-en_US
Ign http://se.archive.ubuntu.com quantal/multiverse Translation-en_US
Ign http://se.archive.ubuntu.com quantal/restricted Translation-en_US
Ign http://se.archive.ubuntu.com quantal/universe Translation-en_US
Ign http://se.archive.ubuntu.com quantal-updates/main Translation-en_US
Ign http://se.archive.ubuntu.com quantal-updates/multiverse Translation-en_US
Ign http://se.archive.ubuntu.com quantal-updates/restricted Translation-en_US
Ign http://se.archive.ubuntu.com quantal-updates/universe Translation-en_US
Ign http://se.archive.ubuntu.com quantal-backports/main Translation-en_US
Ign http://se.archive.ubuntu.com quantal-backports/multiverse Translation-en_US
Ign http://se.archive.ubuntu.com quantal-backports/restricted Translation-en_US
Ign http://se.archive.ubuntu.com quantal-backports/universe Translation-en_US
Ign http://security.ubuntu.com quantal-security/main Translation-en_US
Ign http://security.ubuntu.com quantal-security/multiverse Translation-en_US
Ign http://security.ubuntu.com quantal-security/restricted Translation-en_US
Ign http://security.ubuntu.com quantal-security/universe Translation-en_US
Fetched 239 kB in 4s (49.3 kB/s)
Reading package lists... Done
28:53.26 real, 24.37 user, 5.55 sys, 20 faults, 2728 inputs, 3851424 outputs, 495023 minor faults, 0 swap, 1695 invol. cntx-switch, 394480 vol. cntx-switch


```

---

### Post by dabl on 2013-02-27
Hmmmmm -- yes, there is something off on that system.  I just ran the same command (thanks for that!) on a fully-updated Kubuntu 12.10 system, and got this result:

```
0:09.01 real, 1.22 user, 0.51 sys, 43 faults, 206672 inputs, 161104 outputs, 22915 minor faults, 0 swap, 501 invol. cntx-switch, 864 vol. cntx-switch
```

The dpkg system does its caching and logging in /var.  It's not obvious to me, with what you've described about your system, why that would be relevant, but it is an unusual configuration to have /var mounted separately from the rest of the root filesystem.  I still don't believe that hard drive performance is at the root of your issue, but possibly a caching function is not working correctly.  As an experiment, could you mount /var on the SSD with the rest of the root filesystem?  It might or might not reveal something about the source of the sluggishness.

---

### Post by pqwoerituytrueiwoq on 2013-02-27
this is your config right (this is how i do it with a ssd/hdd)
/dev/sda is your ssd
/dev/sdb is your hdd
/ is mounted to /dev/sda1
/var is mounted to /dev/sdb1
/home is mount to /dev/sdb2
/tmp is mounted to the ram
swap is mount to /dev/sdb3

what is the free space in /var (/dev/sdb1) and / (/dev/sda1)

i assume you have trim enabled (discard in /etc/fstab on /dev/sda1)
your sata controller need to be in AHCI more for that to work BTW (set this in your BIOS)

---

### Post by jazzgossen on 2013-02-28
Actually, sda is my HDD and sdb is my SSD. I also have a few partitions that came with the computer, so to speak: a Dell recovery partition and a Windows partition.
Following is the relevant output from "mount":

```

dev/sdb5 on / type ext4 (rw,noatime,nodiratime,errors=remount-ro,discard)
/dev/sda8 on /home type ext4 (rw,relatime)
/dev/sda6 on /var type ext4 (rw,relatime)
tmpfs on /tmp type tmpfs (rw,mode=1777)

```

And free space:

```

> df /var
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       4.6G  2.0G  2.4G  46% /var

> df /
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb5        55G  9.1G   43G  18% /

```

I also have a 16-GB swap partition on /dev/sda5. And yes, I have set ACPI mode in BIOS.


I will try mounting /var with the rest of the root file system on the SSD. But I don't know if I dare to do that while running? I think I'll try it next time I reboot.

---

### Post by dabl on 2013-02-28
I would change the mount line in /etc/fstab to reflect the new mount point, and then shutdown and reboot, to avoid disturbing the system logging processes.

How about the dpkg cache --- has it been cleared lately?

```
sudo apt-get clean
```

---

### Post by dabl on 2013-02-28
Question:  Did you explicitly mount /tmp in /etc/fstab, or is that a default configuration?  The reason I ask, my 12.10 system (a VM) does not show a separate mount or filesystem for /tmp.

---

### Post by jazzgossen on 2013-03-01
Now I have moved /var to the SSD, and at the moment things are blazing. However, as I mentioned in my original post, the problem with slow IO performance only happened sometimes, not all the time. So I don't dare to consider the problem solved just yet.

Regarding the /tmp mount point: yes, that was done manually. I wanted to move both /var and /tmp away from the SSD, to reduce the amount of writes to it. I hope putting /var back on the SSD won't kill it prematurely.

---

### Post by dabl on 2013-03-01
My main OS (debian sid) has been running on a SSD (OCZ RevoDrive) for over 2 years, including /var, and there are no signs of SSD wear issues -- this desktop runs 24/7 and only gets rebooted for new kernels.  I also mount /tmp on a tmpfs, as well as /var/spool.  You can mount /var/log on a tmpfs, but you'll lose your logs every reboot, so ......

---

### Post by Impavidus on 2013-03-01
It seems it's actually allowed to put /var on a different partition: [http://refspecs.linuxfoundation.org/FHS_2.3/fhs-2.3.html#THEROOTFILESYSTEM](http://refspecs.linuxfoundation.org/FHS_2.3/fhs-2.3.html#THEROOTFILESYSTEM)

If I'm not mistaken SSD wear depends on the number of erase cycles, not the number of writes. Only once in every so many lines written to a log (depending on the physical block size of the drive) one block is erased, whilst normal updates erase many blocks simultaniously.

---

### Post by dabl on 2013-03-01
Yes it's perfectly "legal" to mount /var on its own partition, however for home/single user PCs that is not a commonly-needed configuration.  There is some issue with the OP's system in which it appears to get into a thrashing or cache-reading mode for ridiculous periods of time, so we may learn something by going back to a simpler and more conventional configuration. (Or we may not ....).

---

### Post by jazzgossen on 2013-03-01
Now I have suspended and resumed the laptop once, and I'm back to the old behaviour again. So it might be something with suspend/hibernate rather than the partitioning? Though I don't understand how. 

I know that SSD partitions also must be aligned the right way. Just to double-check, here's the output of fdisk
```

> sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9409c39e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63       80324       40131   de  Dell Utility
/dev/sdb2   *       81920    21676031    10797056    7  HPFS/NTFS/exFAT
/dev/sdb3        21676032   134957281    56640625    7  HPFS/NTFS/exFAT
/dev/sdb4       134959102   250068991    57554945    5  Extended
/dev/sdb5       134959104   250068991    57554944   83  Linux


```
The root partition is on /dev/sdb5, and that partition starts on a number that is divisible by 2048, which is as it should, as far as I know. Some of the other (default Dell) partitions are not aligned that way, but that shouldn't matter, should it?

---

### Post by dabl on 2013-03-01
Right -- that first partition is not aligned, but I don't see why that would have any influence on the Linux system's performance, and the first partition should rarely if ever experience an erase operation, so ......

Hmmmm.  I wonder if the tmpfs filesystems survive a suspend/resume cycle with all data intact?  Or if the suspend operation interferes with the tmpfs filesystems which are also in memory?  I don't use suspend on my desktop system so I don't know whether that could cause an issue with the filesystems that are mounted as tmpfs.  It would interesting to know whether you have the thrashing problem at any time during an extended uptime, or whether it **only** crops up after resuming from suspend.

---

### Post by jazzgossen on 2013-03-04
It's definitely related to suspend. I did a reboot this morning, this time with also /tmp monted on the SSD.  Everything worked fine for 2.5 hours until I suspended. Now that I have resumed, the slowness problem is back. 

Another observation is that also kwin is slower after suspend/resume. Slower as in high latency. There is a lag of about one second; for example, between me pressing alt-tab and the window list appearing. Similarly, when hovering the mouse over an entry in the task bar, it takes a second or two until the thumbnail image of that window is displayed.

My problem seems to be trickier than I thought...

---

### Post by jazzgossen on 2013-03-06
I'm going through the log files, trying to see if there's any indication there of what is happening when suspending and resuming. One error that always comes up is in kern.log

PM: Device 00:0a failed to resume: error -19

There's a post in the LinuxQuestions forum about this error message [here]("http://www.linuxquestions.org/questions/linux-newbie-8/device-00-0a-failed-to-resume-error-19-a-906404/"). I tried the suggestion of listing the PCI devices with "lspci -vt", but  the output does not mention a device 00:0a.

---

### Post by jazzgossen on 2013-03-07
I'll keep using this thread to document my trouble shooting, in the hope that it will be helpful in the future.

Regarding the 00:0a device, that seems to be a PS/2 controller. "dmesg | grep 00:0a" outputs
```
> dmesg |grep 00:0a
[    0.572736] pnp 00:0a: [io  0x0060]
[    0.572738] pnp 00:0a: [io  0x0064]
[    0.572742] pnp 00:0a: [irq 1]
[    0.572776] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[ 3798.386502] PM: Device 00:0a failed to restore: error -19

```
and looking for that PNP0303, I get
```
> dmesg |grep PNP0303
[    0.572776] pnp 00:0a: Plug and Play ACPI device, IDs PNP0303 (active)
[    1.064892] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12

```
I've looked around a little to see if I can just disable the i8042 module, but i8042 is not included when I run "lsmod"; however, there is a directory for it in /sys/module/i8042/. Not sure how or if I can disable it, but then again, I'm not at all sure that it is this module that causes my slowness problems.

A more relevant note is that I have tried hibernate also (once), and when resuming from hibernate, the system is still OK. It seems to be only when resuming from suspend that the problem pops up. Also, just closing the laptops lid and blanking the screen (no suspend or hibernate) does not cause a problem.

I will post again when I have gathered more data.

---

### Post by dabl on 2013-03-07
Good job of troubleshooting!

I'm still suspicious that something is being lost from the tmpfs filesystems during suspend.  Note that in a hibernate, they get written to disk, but in suspend, the entire running system gets written to memory.  That might explain why hibernate works but suspend does not.

---

### Post by jazzgossen on 2013-03-10
Just a new note:
Now the problem has occured again. Currently I have 4 days uptime with no suspend, but a few hibernates. Up until tonight things were working as they should, but not now after the latest resume from hibernate. So it's not only suspend-to-RAM that causes it.

Next thing I should try is probably to disable Optimus. That could probably be causing all kinds of weirdness.

---

### Post by dabl on 2013-03-10
Once in four days is painfully random -- makes it forever to troubleshoot.  But yes, try it with Optimus disabled -- that can't hurt and might help.  If you didn't already check, it would be worth looking at dmesg and the syslog around the timeframe that it slowed down.

---

### Post by jazzgossen on 2013-03-17
I tried disabling optimus, but then I couldn't get full resolution on my screen. I didn't want to struggle more with that, so I reenabled it (together with bumblebee and bumblebee-nvidia). 

Anyway, the symptoms just occured again, and dmesg shows nothing. (The last entry is 8000 seconds ago, when I inserted a USB keyboard).

The only entries in syslog over the past two hours are a few cron jobs that don't look suspicious.

There's a new kern.log started just recently (at 23:02), and kern.log.1 ends a few hours ago (at 20:49). I first noticed the symptoms about half an hour ago. I don't see anything obviously wrong in the kernel logs, but that gap is a bit suprising to me.

---

### Post by jazzgossen on 2013-03-19
At the moment I'm trying to run with acpi=off as a boot option. I've been seeing several ACPI-related error messages in the logs, so I'm starting to suspect it has something to do with that. 

So far so good (but with only a couple of hours uptime). Of course, suspend to RAM no longer works, but hibernate does. If I can run this way for a few days, than I'll start to selectively disable some ACPI settings. 

One unexpected thing that also doesn't work with acpi=off is the touchpad and the mid-keyboard joystick. However, attaching a USB mouse works fine.

---

### Post by jazzgossen on 2013-03-20
Here are my latest findings. 

I have tried a few ACPI-related boot options.
[LIST]
[*]With acpi=off, I can't suspend at all, the fan is constantly storming, and I can't use the touchpad. Other than that, I didn't notice the slowness problem. Then again, since I can't suspend, it's not so strange. And the fan noise was a bit too much to bear for testing several days in a row.
[*]With pci=noacpi, I can suspend but can't use the laptop keyboard; only an external USB keyboard. But after suspending, the slowness problem comes back.
[*]With acpi=noirq, I also have no laptop keyboard
[*]With pnpacpi=off, I can use the keyboard and touchpad, but the problem comes back after suspend
[*]With noapic, it's the same; and that's what I currently run
[*]
[/LIST]

Something that I suspect is related to my problem is the following output from dmesg. After a fresh boot (with the noapic boot option), I have the following: 
```
 
> dmesg |grep -i acpi | grep -i error
[    0.526161]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d


> dmesg |grep -i acpi | grep -i warning
[    8.815574] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    8.815586] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[    8.815592] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[    8.815596] ACPI Warning: 0x00000500-0x0000053f SystemIO conflicts with Region \_SB_.PCI0.PEG0.VID_.GPSP 2 (20120320/utaddress-251)


```

Not sure if that's alarming or not. However, when I do the same after a suspend/resume cycle, I get the following
```

> dmesg |grep -i acpi | grep -i error
[    0.526161]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[  311.459051] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV.ECR1] (Node f742fd50), AE_TIME (20120320/psparse-536)
[  311.459069] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV.ECR2] (Node f742fd68), AE_TIME (20120320/psparse-536)
[  311.459077] ACPI Error: Method parse/execution failed [\ECRW] (Node f742fe40), AE_TIME (20120320/psparse-536)
[  311.459086] ACPI Error: Method parse/execution failed [\ECG1] (Node f742fe70), AE_TIME (20120320/psparse-536)
[  311.459094] ACPI Error: Method parse/execution failed [\NEVT] (Node f74300f0), AE_TIME (20120320/psparse-536)
[  311.459102] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV._Q66] (Node f742fd38), AE_TIME (20120320/psparse-536)
[  312.979329] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV.ECR1] (Node f742fd50), AE_TIME (20120320/psparse-536)
[  312.979349] ACPI Error: Method parse/execution failed [\ECBT] (Node f742fdf8), AE_TIME (20120320/psparse-536)
[  312.979369] ACPI Error: Method parse/execution failed [\ECG2] (Node f742fea0), AE_TIME (20120320/psparse-536)
[  312.979378] ACPI Error: Method parse/execution failed [\ECG6] (Node f742ff48), AE_TIME (20120320/psparse-536)
[  312.979439] ACPI Error: Method parse/execution failed [\_SB_.BAT0._BST] (Node f7430408), AE_TIME (20120320/psparse-536)
[  313.486137] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV.ECR1] (Node f742fd50), AE_TIME (20120320/psparse-536)
[  313.486155] ACPI Error: Method parse/execution failed [\ECBT] (Node f742fdf8), AE_TIME (20120320/psparse-536)
[  313.486166] ACPI Error: Method parse/execution failed [\ECG2] (Node f742fea0), AE_TIME (20120320/psparse-536)
[  313.486175] ACPI Error: Method parse/execution failed [\ECG6] (Node f742ff48), AE_TIME (20120320/psparse-536)
[  313.486185] ACPI Error: Method parse/execution failed [\_SB_.BAT0._BST] (Node f7430408), AE_TIME (20120320/psparse-536)


```

So a bunch of new ACPI errors. 

Googling hasn't given me much input on these. Maybe my best bet is to wait for the next kernel update in Kubuntu 13.04, and hope that any funky ACPI features of my Dell BIOS has been incorporated in the kernel by then?

---

### Post by dabl on 2013-03-20
The error reported by dmesg is not a good thing, and may in fact be relevant to the problematic behavior.  AFAIK, the warnings are not significant -- I see the same things on my desktop, which happens to be an Asus P6X58D-e board:

```
don@imerabox:~$ dmesg | grep -i acpi | grep -i error
don@imerabox:~$ dmesg |grep -i acpi | grep -i warning
[   11.447063] ACPI Warning: 0x0000000000001000-0x000000000000101f SystemIO conflicts with Region \SMRG 1 (20121018/utaddress-251)
[   11.448388] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPS0 1 (20121018/utaddress-251)
[   11.448393] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPS0 1 (20121018/utaddress-251)
```

Here is a relevant post from a couple years ago:  [http://ubuntuforums.org/showthread.php?t=1882050&page=2](http://ubuntuforums.org/showthread.php?t=1882050&page=2)

---

### Post by jazzgossen on 2013-03-21
Thanks for the info and the link, dibl!

I'm currently running with the "nolapic" boot option, and this setting seems to be good. I have done three suspends and have a total uptime of 10:58, and things are still working as they should. 

The ACPI error messages in dmesg are similar to what I had when running with "noapic", but there are a some differences. 

```

> dmesg |grep -i acpi | grep -i error
[    0.073397]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[   11.325322] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV.ECR1] (Node f742fd50), AE_TIME (20120320/psparse-536)
[   11.325328] ACPI Error: Method parse/execution failed [\ECRB] (Node f742fe28), AE_TIME (20120320/psparse-536)
[   11.325331] ACPI Error: Method parse/execution failed [\ECG5] (Node f742ff00), AE_TIME (20120320/psparse-536)
[   11.325334] ACPI Error: Method parse/execution failed [\_SB_.AC__._PSR] (Node f7430330), AE_TIME (20120320/psparse-536)
[   11.325340] ACPI Exception: AE_TIME, Error reading AC Adapter state (20120320/ac-118)
[ 1067.618169] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV.ECR1] (Node f742fd50), AE_TIME (20120320/psparse-536)
[ 1067.618176] ACPI Error: Method parse/execution failed [\ECBT] (Node f742fdf8), AE_TIME (20120320/psparse-536)
[ 1067.618179] ACPI Error: Method parse/execution failed [\ECG2] (Node f742fea0), AE_TIME (20120320/psparse-536)
[ 1067.618182] ACPI Error: Method parse/execution failed [\ECG6] (Node f742ff48), AE_TIME (20120320/psparse-536)
[ 1067.618185] ACPI Error: Method parse/execution failed [\_SB_.BAT0._BST] (Node f7430408), AE_TIME (20120320/psparse-536)
[ 1068.452021] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.ECDV.ECR1] (Node f742fd50), AE_TIME (20120320/psparse-536)
[ 1068.452028] ACPI Error: Method parse/execution failed [\ECBT] (Node f742fdf8), AE_TIME (20120320/psparse-536)
[ 1068.452031] ACPI Error: Method parse/execution failed [\ECG2] (Node f742fea0), AE_TIME (20120320/psparse-536)
[ 1068.452046] ACPI Error: Method parse/execution failed [\ECG6] (Node f742ff48), AE_TIME (20120320/psparse-536)
[ 1068.452049] ACPI Error: Method parse/execution failed [\_SB_.BAT0._BST] (Node f7430408), AE_TIME (20120320/psparse-536)

```

So the first one is still there (ACPI _OSC request failed), but the system has been running fine with that error message before too. 

A few new ones have appeared, at 11.3 seconds.

At suspend/resume there are now five ACPI errors (Method parse/execution failed), whereas with "noapic" there were ten. The ones that do not appear with "nolapic" are [\_SB_.PCI0.LPCB.ECDV.ECR2], [\ECRW], [\ECG1], and [\NEVT].

---

### Post by jazzgossen on 2013-03-21
I found [this thread]("http://permalink.gmane.org/gmane.linux.acpi.devel/47972"), which describes a problem with the very same error messages that appeared with "noapic" but not with "nolapic". In that case, it had to do with an AC adapter, and apparently the problem was fixed in kernel 2.6.37. 

I tried unplugging and replugging my AC adapter, and there are no new errors in dmesg. However, the system is *a bit* slower now than before. Kwin is generally responsive, but apt-get update takes around two minutes. That's not too bad, and I can certainly live with it; but it is definitely slower than the 10-20 seconds it took before removing the AC adapter, and still very much faster than the 30 minutes it has taken before (and then kwin was lagging also).

So I should be monitoring what happens with and without the AC adapter, and not just what happens at suspend and resume.

---

### Post by jazzgossen on 2013-03-21
Now I booted with nolapic, and the AC adapter unplugged. Things going OK. Then I plugged in the AC, and now "apt-get update" is slow again. Go figure.

There are no "parse/execution failed" ACPI error messages (they would only occur when I suspend). I don't see anything obviously wrong in the logs, but I'll paste tail of kern.log here anyway.

```

Mar 21 11:50:17 anis kernel: [  513.852178] bbswitch: enabling discrete graphics
Mar 21 11:50:18 anis kernel: [  514.566259] pci 0000:01:00.0: power state changed by ACPI to D0
Mar 21 11:50:18 anis kernel: [  514.566273] pci 0000:01:00.0: power state changed by ACPI to D0
Mar 21 11:50:18 anis kernel: [  514.566341] pci 0000:01:00.0: power state changed by ACPI to D0
Mar 21 11:50:18 anis kernel: [  514.566347] pci 0000:01:00.0: power state changed by ACPI to D0
Mar 21 11:50:18 anis kernel: [  514.566354] pci 0000:01:00.0: enabling device (0004 -> 0007)
Mar 21 11:50:18 anis kernel: [  514.620093] nvidia: module license 'NVIDIA' taints kernel.
Mar 21 11:50:18 anis kernel: [  514.620095] Disabling lock debugging due to kernel taint
Mar 21 11:50:18 anis kernel: [  514.627352] nvidia 0000:01:00.0: power state changed by ACPI to D0
Mar 21 11:50:18 anis kernel: [  514.627356] nvidia 0000:01:00.0: power state changed by ACPI to D0
Mar 21 11:50:18 anis kernel: [  514.627359] nvidia 0000:01:00.0: enabling device (0004 -> 0007)
Mar 21 11:50:18 anis kernel: [  514.627370] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
Mar 21 11:50:18 anis kernel: [  514.627714] NVRM: loading NVIDIA UNIX x86 Kernel Module  304.51  Tue Sep 18 17:36:24 PDT 2012
Mar 21 11:50:19 anis kernel: [  515.815378] NVRM: GPU at 0000:01:00: GPU-21148771-abf9-5d8e-f9a3-6997c8be31c3
Mar 21 11:50:23 anis kernel: [  519.781681] bbswitch: disabling discrete graphics
Mar 21 11:50:23 anis kernel: [  519.797232] pci_raw_set_power_state: 46 callbacks suppressed
Mar 21 11:50:23 anis kernel: [  519.797235] pci 0000:01:00.0: Refused to change power state, currently in D0
Mar 21 11:50:23 anis kernel: [  520.097342] pci 0000:01:00.0: power state changed by ACPI to D3
Mar 21 12:02:54 anis kernel: [ 1268.613609] cfg80211: Found new beacon on frequency: 5220 MHz (Ch 44) on phy0
Mar 21 12:04:53 anis kernel: [ 1387.926244] cfg80211: Found new beacon on frequency: 5180 MHz (Ch 36) on phy0

```

The pci_raw_set_power_state message seems to lead in the direction of bumblebee. So maybe my next step would be to try to disable bumblebee/Optimus again.

---

### Post by dabl on 2013-03-21
I can't see how using the AC adapter would be relevant to a software operation like apt-get, unless somehow the wifi chip's performance is being compromised.  Doesn't make much sense to me.  Might be a design bug in the hardware.

---

### Post by jazzgossen on 2013-03-22
Yes. Strange, isn't it?

Anyway, here are my conclusions.
[LIST]
[*]With "noapic", I get lag both after suspend/resume, and after (un)plugging the AC adapter
[*]With "nolapic", I can suspend, but still get lag when (un)plugging the AC
[*]With "nolapic" I only see 1 of 4 CPU cores
[*]With "noapic nolapic", I have the same behaviour as with only "nolapic"
[*]
[/LIST]

I think I will take it to Launchpad from here.

Thanks a lot for your discussion, dabl.

---

### Post by jazzgossen on 2013-04-03
I started to think this was related to bumblebee (or bbswitch), but maybe not. 

I have a new, clean, Kubuntu 12.10 installation on a separate partition on the HDD. Everything is on the same partition on that installation. The only modification is that I have disabled the swap partition, not to overwrite the hibernate file of my other Kubuntu installation. On that installation, things work as they should.

From my main installation, I purged everything related to nvidia and bumblebee, and cleaned the boot command line to have no extra options. But the problem remains: I get lots of lag after I unplug the AC or do suspend.

So I don't know which package I could file a bug report to on Launchpad either.

I should try to check what other differences there are between my problematic Kubuntu installation and the clean, working, one.

---

### Post by jazzgossen on 2013-04-30
I have now upgraded to Kubuntu 13.04 (first an upgrade, but now a clean install), and I still see the same problem. After a bit of more troubleshooting, I see that I get the slowness problem also on the HDD installation. 

However, a workaround seems to be to hibernate and resume. After resuming from hibernate, things are as fast as from a reboot, until I unplug the AC cord or suspend again.

This workaround is a bit cumbersome, but it works for me.

---

