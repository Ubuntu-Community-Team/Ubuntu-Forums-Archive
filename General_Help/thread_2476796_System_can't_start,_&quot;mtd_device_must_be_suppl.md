---
title: "System can't start, &quot;mtd device must be supplied&quot;"
date: 2022-07-07
forum: General Help
---

### Post by frost692 on 2022-07-07
Hi. Two days ago I installed Ubuntu 22.04 on my brand new computer, and today when starting it up I found that the system does not start.

The console says:
"[160.236589] mtd device must be supplied (device name is empty)"
And it only works in emergency mode. When I choose continue, it repeats the same message.

Yesterday, I was formatting my external HDD, and it seemed like I did not have permission to modify anything on it, even though it was formatted. After that I shutdown the computer and that was the last thing I was doing.

---

### Post by #&amp;thj^% on 2022-07-07
> **frost692 said:**
> Hi. Two days ago I installed Ubuntu 22.04 on my brand new computer, and today when starting it up I found that the system does not start.

The console says:
"[160.236589] mtd device must be supplied (device name is empty)"
And it only works in emergency mode. When I choose continue, it repeats the same message.

Yesterday, I was formatting my external HDD, and it seemed like I did not have permission to modify anything on it, even though it was formatted. After that I shutdown the computer and that was the last thing I was doing.

Sounds very likely your format did not work.
What tool used for formatting the drive?
And what are the specs for your  brand new computer.
Until the needed info is shown here, we are just chasing our tails.

---

### Post by frost692 on 2022-07-07
Thing is. I had two drives on my PC. An SSD, on which the system was installed, and an almost empty HDD that I just plugged in later, and used the default Ubuntu Disk Manager to format.

I'm not too sure what specs you need to know, but I'm running an Intel i7 12700KF, 16GB of RAM and an ASUS TUF Gaming Z690-PLUS motherboard

---

### Post by #&amp;thj^% on 2022-07-07
> **frost692 said:**
> Thing is. I had two drives on my PC. An SSD, on which the system was installed, and an almost empty HDD that I just plugged in later, and used the default Ubuntu Disk Manager to format.

If it had two drives, the non-main drive is probably not bootable.
I have one like that it has a nvme ssd and spinning  2.5 drive, so the  spinning  2.5 drive in my case here is non-bootable. (Back-ups only and such)
But this still has me lacking info>>>" **An SSD, on which the system was installed**"
What system was installed on the SSD?? Ubuntu or Windows?
> **frost692 said:**
>  I'm running an Intel i7 12700KF, 16GB of RAM and an ASUS TUF Gaming Z690-PLUS motherboard 

Well that is probably enough info for me

---

### Post by frost692 on 2022-07-07
Ubuntu was installed on the SSD. The HDD drive was just a storage drive I plugged in to keep some important files. Like I said, I tried formatting it but I don't know what happened with it honestly

---

### Post by #&amp;thj^% on 2022-07-07
I'd try again installing with secure boot disabled in the Bios.
Yours is Supported:
> 
TUF GAMING X570-PLUS (WI-FI) Fedora 29 OpenSUSE 15.0 RedHat 7.6 Ubuntu 18.10
Secure Boot will stop/block needed  drivers for the OS.
And you are installing in UEFI mode right?
BTW While your using the Live Installer dose everything function? (Hardware Audio WiFi)

---

### Post by frost692 on 2022-07-07
Just to clarify, you're saying I should reinstall Ubuntu?

---

### Post by #&amp;thj^% on 2022-07-07
Try the Live Installer to make sure all is good>>>(Hardware Audio WiFi)  first, and if all is good, then try the install again.
IMPORTANT: Secure Boot needs to be Disabled!!!

---

### Post by grahammechanical on 2022-07-07
What is an mtd device?

[https://en.wikipedia.org/wiki/Memory_Technology_Device](https://en.wikipedia.org/wiki/Memory_Technology_Device)

Not much enlightenment in that text. To get a working system I would install Ubuntu on the hard drive and then use the Disks utility to check how healthy the SSD is.

Regards

---

### Post by frost692 on 2022-07-08
So uhm. I still have a USB Stick with the Ubuntu installer left from the original installation, but it's not visible to the computer for some reason. UEFI only sees the SSD and some kind of internal UEFI drive (I took the HDD out for now)

EDIT: One more thing. I managed to get into Recovery mode, and system log shows that it doesn't detect any RAID memory. Is it supposed to be like that?

---

### Post by Claus7 on 2022-07-08
Hello,

not direct help to the OP, yet I came across the same message today in my system. It is printed during boot thrice and then boots normally, so compared to the OP, up to now, I do not have to go to recovery mode. Boot time also is not affected with this message.

Either both of us have hdd problems or some packages are affecting it. I would like to add that this happened almost simultaneously with an upgrade to systemd package that bothers me for some time: 
[https://ubuntuforums.org/showthread.php?t=2476471&p=14102181&highlight=#post14102181](https://ubuntuforums.org/showthread.php?t=2476471&p=14102181&highlight=#post14102181)

and it happened once more compared to that thread, which I did not pay much attention.
Until this message popped up and I came across this thread.

Regards!

---

### Post by #&amp;thj^% on 2022-07-08
Thanks Claus7, For adding your findings, I'm having a rough time wrapping my head around this one.
We will get to bottom of it.
Just to be sure, do both of you have current firmware && Bios?

---

### Post by Claus7 on 2022-07-08
Hello,

thank you for your input *1fallen*! 
My system is fully updated/upgraded and if I may judge for the OP it should be the same (since we are talking about a fresh install): it has some time until firmware update took place. Synaptic informs me taking place more than a month ago.

The rest is unknown words to me. I have never tampered with BIOS upgrade. It has been serving me well for so many years, so I do not know if actually something like that exists for my machine. 

In case I notice something new I will report, taking a look on this thread of new inputs.

Regards!

---

### Post by #&amp;thj^% on 2022-07-08
I would have guessed that your on top it, just a friendly check is all.
OP's machine is somewhat newish, and I know that Bios should be checked for any new versions.
Mine:
```
inxi -M
Machine:
  Type: Laptop System: LENOVO product: 82B5 v: Lenovo Legion 5 15ARH05
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN
    serial: <superuser required> **_[COLOR="#FF0000"]UEFI: LENOVO v: EUCN37WW date: 04/14/2022[/COLOR]_**
```
Text in red is my latest Bios and version.

---

### Post by roy-ot on 2022-07-09
I have the same message recently on my Ubuntu 22.04 LTS without any issues so far.  Just leave it for now.

kern.log:Jul  9 13:14:58 h55m-p33 kernel: [    3.977696] mtd device must be supplied (device name is empty)

---

### Post by allkhor on 2022-07-09
Same here, fresh install, Xubuntu 22.04, kernel 5.15.0-40-generic
 user@LinuxPC:~$ sudo dmesg | grep mtd

 ```
[    8.663210] systemd[1]: Starting Load Kernel Module mtdpstore...
[    9.349244] mtd device must be supplied (device name is empty)
[   16.754162] mtd device must be supplied (device name is empty)
[   18.636338] mtd device must be supplied (device name is empty)
```

As workaround blacklisted mtdpstore module. Modify /etc/default/grub
```

GRUB_CMDLINE_LINUX_DEFAULT="modprobe.blacklist=mtdpstore quiet splash"
```
And after changes update grub: ```
sudo update-grub
```
Who know any disadvantage of blacklist this module?

As i can see i have no mtd devices in system. Anybody has create bug report to launchpad.net?

---

### Post by ajgreeny on 2022-07-09
I am also seeing this message on screen just after the Xubuntu Jammy system tells me that the system is clean (the quick fsck check at boot) but like **roy-ot **and **allkhor** my system then boots with no problems.

This is on a laptop with a single spinning disk also running Focal in dual boot. 
My 22.04 was installed April 29th 2022 so is not a very recent installation, and has been and still is running very well.

I generally only reboot when a new kernel is installed so I'm not sure when this might have appeared on my laptop system but I know that systemd was upgraded June 24th.

I am currently on a desktop machine also with dual boot of Xubuntu 20.04 and 22.04 which has an uptime of 9 days but I will shortly reboot to see if the same message appears on this as well.

[COLOR="#FF0000"]UPDATE:[/COLOR]

No, I'm not getting this on my desktop machine, only the laptop.

[COLOR="#FF0000"]UPDATE #2:[/COLOR]
I have just updated everything and rebooted a second time and I am now seeing this message on the desktop machine as well, though it still boots and seems to perform without a problem.

Here's the list of upgraded packages which you will note does include many systemd items
```
upgrade libnss-**systemd**:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade **libsystemd0**:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade **systemd**-timesyncd:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade **systemd**-sysv:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade libnss-mymachines:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade **systemd**-container:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade libpam-**systemd**:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade **systemd**:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade udev:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade libudev1:amd64 249.11-0ubuntu3.3 249.11-0ubuntu3.4
upgrade isc-dhcp-client:amd64 4.4.1-2.3ubuntu2 4.4.1-2.3ubuntu2.1
upgrade isc-dhcp-common:amd64 4.4.1-2.3ubuntu2 4.4.1-2.3ubuntu2.1
upgrade evince-common:all 42.3-0ubuntu1 42.3-0ubuntu2
upgrade evince:amd64 42.3-0ubuntu1 42.3-0ubuntu2
upgrade libevdocument3-4:amd64 42.3-0ubuntu1 42.3-0ubuntu2
upgrade libevview3-3:amd64 42.3-0ubuntu1 42.3-0ubuntu2
upgrade evolution-data-server-common:all 3.44.1-0ubuntu2 3.44.2-0ubuntu1
upgrade libnss3:amd64 2:3.68.2-0ubuntu1 2:3.68.2-0ubuntu1.1
upgrade libcamel-1.2-63:amd64 3.44.1-0ubuntu2 3.44.2-0ubuntu1
upgrade libebook-contacts-1.2-3:amd64 3.44.1-0ubuntu2 3.44.2-0ubuntu1
upgrade libedataserver-1.2-26:amd64 3.44.1-0ubuntu2 3.44.2-0ubuntu1
upgrade skypeforlinux:amd64 8.86.76.403 8.86.76.407

```
So perhaps that is why I am now seeing this warning/error.

No doubt another upgrade will follow if that is the reason behind this.

---

### Post by patrickcee on 2022-07-10
I have also just seen this on reboot today (7/10), after an uptime of 12 days. It seems likely it is related to one of the system updates during that period. I had not ever seen this message before=, and it is not in any kern.log* file until appearing 4 times during this last reboot. The reboot went normally otherwise. I'm running 22.04 (Kubuntu) on a desktop system, with no recent hardware changes, and have rebooted 22.04 more than once before this last time.
[FONT=monospace]
[/FONT]

---

### Post by ajgreeny on 2022-07-10
You will find the full details of this error in the current ***/var/log/syslog*** file.

However, to the unskilled in reading and understanding log files such as me, that is not much help.

---

### Post by ajgreeny on 2022-07-13
I today created a virtual installation of Xubuntu-22.10 as a KVM/QEMU and when booted immediately after installing I saw this message, though as with my 22.04 version, the OS still boots and runs without a problem.

The iso file I used was  downloaded from [https://cdimage.ubuntu.com/xubuntu/daily-live/current/kinetic-desktop-amd64.iso](https://cdimage.ubuntu.com/xubuntu/daily-live/current/kinetic-desktop-amd64.iso) so whatever is causing this problem is affecting not only 22.04, but also the as yet to be released 22.10

---

### Post by VMC on 2022-07-13
```
$ sudo dmesg -T|grep mtd
[Wed Jul 13 14:03:56 2022] systemd[1]: Starting Load Kernel Module mtdpstore...
[Wed Jul 13 14:03:56 2022] mtd device must be supplied (device name is empty)
```
Ubuntu Kinetic Kudu (development branch)

This just started for me a few updates ago. Just figured out what it is, since the bootup screen just flashed the error.

---

### Post by #&amp;thj^% on 2022-07-13
You poor folks sure seem have your fair share of issues with Ubuntu>>>I've not seen any of this on my end with a different OS of course.
Suse has pushed some fix's such as  the below:
```
 mtd: Support kmsg dumper based on pstore/blk (jsc#SLE-16304).
+- Update config files.
+- supported.conf: add mtdpstore
+- commit ffec888
+
+- pstore/blk: Introduce "best_effort" mode (jsc#SLE-16304).
+- pstore/blk: Support non-block storage devices (jsc#SLE-16304).
+- pstore/blk: Provide way to query pstore configuration
+  (jsc#SLE-16304).
+- pstore/zone: Provide way to skip "broken" zone for MTD devices
+  (jsc#SLE-16304).
+- commit 278b9b6
+
+- Documentation: Add details for pstore/blk (jsc#SLE-16304).
+- commit f35da88
```
Let's see how long it takes Ubuntu now.

---

### Post by VMC on 2022-07-13
> **1fallen said:**
> You poor folks sure seem have your fair share of issues with Ubuntu>>>I've not seen any of this on my end with a different OS of course.
....

My Arch installs don't have the issue either.

---

### Post by ajgreeny on 2022-07-14
> **1fallen said:**
> You poor folks sure seem have your fair share of issues with Ubuntu>>>

Not really too much of an issue for me as the warning/error message simply flashes on screen and then disappears as the computer continues to boot as normal.

---

### Post by yetimon_64 on 2022-07-14
> **allkhor said:**
> ... Anybody has create bug report to launchpad.net?
Yes someone has done so now ... [URL="https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622"]https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1981622
[/URL]
Like a couple of replies above regarding Xubuntu (I'm on 22.04) I am also getting the message but am able to boot up fine otherwise. For some weird reason my error message usually repeats 3 times but then moves on.
Anyone affected by this bug can click the "This bug affects me" link (when logged in to launchpad) to add a bit of "heat" to the bug report.

---

### Post by #&amp;thj^% on 2022-07-14
Glad to hear someone has finally...](*,)
It has to be Ubuntu only effected, Debian Rolling UN-effected. 
A big thanks to yetimon_64 for providing a bug link. ;)

---

### Post by Farenheit on 2022-07-27
I was running Ubuntu Desktop 20.04 and upgraded to 22.04 in a VMware Workstation VM.  After the upgrade, I began receiving the "mtd device must be supplied error."  As far as I can tell, I'm not using any MTD devices: ```
ls -d /dev/mt*
``` says "no such directory."  I'm probably solving the problem with a hammer, but disabling the "systemd-pstore" service stops the error for me: 

```
sudo systemctl disable systemd-pstore.service
```  It can be re-enabled if they fix the issue down the road: ```
sudo systemctl enable systemd-pstore.service
```

---

### Post by VMC on 2022-08-01
Fixed with today's updates. yay.

---

### Post by #&amp;thj^% on 2022-08-01
> **VMC said:**
> Fixed with today's updates. yay.
Not here though :( today's actually broke my KVM install on jammy, but i fixed it...

---

### Post by Claus7 on 2022-08-01
Hello,

not here as well. I'm having lots of updates as posted here: [https://ubuntuforums.org/showthread.php?t=2477582&p=14106496#post14106496](https://ubuntuforums.org/showthread.php?t=2477582&p=14106496#post14106496), yet they are pending (phased or whatever) updates. Among them there is no systemd package.

Regards!

---

### Post by VMC on 2022-08-01
These are the three updates that fixed it for me:
```
libmtp-common:amd64 (1.1.19-1build1, 1.1.20-1),
libmtp9:amd64 (1.1.19-1build1, 1.1.20-1),
libmtp-runtime:amd64 (1.1.19-1build1, 1.1.20-1)
```
See if you received those.

---

### Post by #&amp;thj^% on 2022-08-01
> **VMC said:**
> These are the three updates that fixed it for me:
```
libmtp-common:amd64 (1.1.19-1build1, 1.1.20-1),
libmtp9:amd64 (1.1.19-1build1, 1.1.20-1),
libmtp-runtime:amd64 (1.1.19-1build1, 1.1.20-1)
```
See if you received those.
That's how I get to my session, I had to reinstall:
```
me@me-Standard-PC-Q35-ICH9-2009:~$ apt-cache depends libmtp-runtime:amd64
libmtp-runtime
  Depends: libmtp-common
  Depends: libmtp9
  Depends: libc6
  Enhances: libmtp9
me@me-Standard-PC-Q35-ICH9-2009:~$ apt policy libmtp-runtime:amd64
libmtp-runtime:
  Installed: 1.1.19-1build1
  Candidate: 1.1.19-1build1
  Version table:
 *** 1.1.19-1build1 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```
Thanks for reminding me VMC , I said I fixed mine, in my previous post, but did not show how.

---

### Post by 0x41414141 on 2022-08-07
Installing the proprietary Nvidia drivers fixed it for me. The ```
mtd device must be supplied (device name is empty)
``` message has nothing to do with the problem, it's just that you get stuck on this screen showing kernel log errors and a blinking cursor when the rest of the graphical display doesn't start. I could use Ctrl+Alt+F2 to get a shell and examine the system. I couldn't figure out the problem with dmesg or journalctl so here were my steps to isolate and solve the problem.


[LIST]
[*]Do a fresh install of Ubuntu 22.04 
[*]Reboot, removing installation media 
[*]Verify I can adjust my display settings (portrait mode, 165 Hz, etc.) 
[*]Verify the Apply button saves the settings 
[*]Reboot, verifying display settings are still the same 
[*]Do an apt update && apt -y --purge full-upgrade && apt -y --purge autoremove 
[*]Reboot 
[*]The problem begins here 
[*]Reboot 
[*]At Grub prompt choose Advanced options and boot into previous kernel 
[*]Now I have a graphical display again but it's limited to one monitor, a low refresh rate, and you can't rotate it (changing any settings and hitting Apply immediately reverts them) 
[*]I hit the Windows key, type Software Updates, and go to Additional Drivers 
[*]It shows that I'm using the Noveau drivers so I changed them to the nvidia-driver-515 (proprietary, tested) drivers at the top 
[*]Rebooting into the older kernel still gives the limited graphical display 
[*]Trying to launch any of the Nvidia settings programs gives errors that nvidia.ko is not loaded 
[*]Rebooting into the newer kernel gives the full-featured graphical display and nvidia.ko is loaded 
[/LIST]

Alternatively you should be able to accomplish the same result by doing an ```
apt install nvidia-driver-515
``` from the Ctrl+Alt+F2 tty. I have two kernels:


[LIST]
[*]5.15.0-43-generic 
[*]5.15.0-25-generic 
[/LIST]

The reason it now only works in the newer 5.15.0-43-generic kernel is that the Nvidia drivers only built the module for that kernel. The reason I couldn't find nvidia.ko for a long time was because I forgot to add an -L flag to find because /lib is a symbolic link.```
find -L /lib -type f -name "*nvidia*.ko"
```

Something about doing a full system upgrade after fresh install must've removed the Nvidia drivers or reverted Ubuntu settings to prefer Noveau.

---

