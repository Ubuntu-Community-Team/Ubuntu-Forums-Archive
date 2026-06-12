---
title: "Ubuntu booting into grub, help"
date: 2015-09-04
forum: General Help
---

### Post by s0c0 on 2015-09-04
Was just checking my email and doing some work and then my laptop rebooted out of nowhere. When I attempted booting into Ubuntu 15 it went to the grub command line, so I loaded up a live usb and ran boot-repair. Still cannot access Ubuntu. Here is the output from boot-repair:

[http://paste.ubuntu.com/12274870/](http://paste.ubuntu.com/12274870/)

Any ideas here?

---

### Post by s0c0 on 2015-09-04
There might be something else going on here. When I boot into a live disk and take a look at gparted it says /dev/sda3 (which is where I installed the OS on) has an unknown file system. So its likely corrupted. My setup is:

/dev/sda1 ntfs recovery (pretty sure this is an acer recovery partition)
/dev/sda2/ fat32 boot
/dev/sda3/ unknown
/dev/sda4/ ntfs (windows)
/dev/sda5 ntfs
/dev/sda6 ext4 (/home, /var and others)

---

### Post by oldfred on 2015-09-04
Your sda3 is the Microsoft reserved. It is unformatted space required by Microsoft and since unformatted always gives an error in gparted.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

But it also seems to have issues with sda4, you cannot dual boot and have Windows always on hibernation or fast startup on. 
      
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

And any abnormal shutdown when system is working almost always needs chkdsk for Windows or fsck if Linux.

       
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

---

### Post by Bashing-om on 2015-09-04
s0c0; Hey !

Ninja'd by oldfred ^^

---

### Post by s0c0 on 2015-09-05
Okay something bad came down in an update recently for those of us on 15. And its affecting others as well: [http://ubuntuforums.org/showthread.php?t=2293406&p=13350417#post13350417](http://ubuntuforums.org/showthread.php?t=2293406&p=13350417#post13350417) 

This happened to me again. When you run an update, something freaks out and it auto reboots you into grub. I saw something about EFI flash in my terminal before being thrown into the abyss. The second go around when I do an apt-get update, followed by an apt-get upgrade it asks me to do a dpkgconfigure -a, at this point you're toast. So don't do it until someone smarter than me comes up with a solution. I'm going to post steps to fix this. Then hopefully look through logs and be able to submit a bug report to Ubuntu. Never venturing outside of LTS again grrr....

---

### Post by s0c0 on 2015-09-05
Okay this is a double-whammy as this bug corrupts your ext4 file system and the grub bootloader. Luckily its a pretty easy fix:

1. In your BIOS make sure secure boot is off.
2. Load Ubuntu Live (I did mine via USB Stick)
3. Repair your main partition that Ubuntu is installed on. If you are confused as to what is what open up gparted while in your Live OS and take a look at whats on there, in my case since I am dual boot Ubuntu is installed on /dev/sda6. This is the command to run to repair your file system:

sudo e2fsck -C0 -p -f -v /dev/sda6

4. Follow the steps here to repair grub: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) (I used option 2). Note this is where turning secure boot off is necessary I think.

You should be good now. There is some stuff I did with the windows boot manager as well, but I'm not sure it was necessary. If you are on a dual boot system and still having problems getting in post a reply in here and I'll hop into windows and see what I did.

---

### Post by s0c0 on 2015-09-05
Some interesting things in logs.


**/var/log/syslog:**
> 
Sep  4 23:07:56 localhost chromium-browser.desktop[2538]: [2538:2579:0904/230755:ERROR:simple_backend_impl.cc(574)] Simple Cache Backend: wrong file structure on disk: /home/chris/.config/chromium/Default/Service Worker/CacheStorage/28da9c56fde4021055a681112c092453f74d8dd8/8f25589a075bbe91b2d0db80adac56f7bf66d17c
Sep  4 23:07:56 localhost chromium-browser.desktop[2538]: [2538:2580:0904/230755:ERROR:cache_creator.cc(132)] Unable to create cache
Sep  4 23:08:33 localhost chromium-browser.desktop[2538]: [3:2:0904/230833:ERROR:channel.cc(300)] RawChannel read error (connection broken)
Sep  4 23:08:35 localhost chromium-browser.desktop[2538]: [3:2:0904/230835:ERROR:channel.cc(300)] RawChannel read error (connection broken)
Sep  4 23:09:01 localhost CRON[22237]: (root) CMD (  [ -x /usr/lib/php5/sessionclean ] && /usr/lib/php5/sessionclean)


After this I see a whole bunch of NUL character blocks.

**/var/log/apt/term.log**
> 
Log started: 2015-09-01  13:53:01
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 276512 files and directories currently installed.)
Preparing to unpack .../libexpat1_2.1.0-6ubuntu1.1_i386.deb ...
De-configuring libexpat1:amd64 (2.1.0-6ubuntu1) ...
Unpacking libexpat1:i386 (2.1.0-6ubuntu1.1) over (2.1.0-6ubuntu1) ...
Preparing to unpack .../libexpat1_2.1.0-6ubuntu1.1_amd64.deb ...
Unpacking libexpat1:amd64 (2.1.0-6ubuntu1.1) over (2.1.0-6ubuntu1) ...
Preparing to unpack .../libgnutls-openssl27_3.3.8-3ubuntu3.1_amd64.deb ...
Unpacking libgnutls-openssl27:amd64 (3.3.8-3ubuntu3.1) over (3.3.8-3ubuntu3) ...
Preparing to unpack .../libgnutls-deb0-28_3.3.8-3ubuntu3.1_i386.deb ...
De-configuring libgnutls-deb0-28:amd64 (3.3.8-3ubuntu3) ...
Unpacking libgnutls-deb0-28:i386 (3.3.8-3ubuntu3.1) over (3.3.8-3ubuntu3) ...
Preparing to unpack .../libgnutls-deb0-28_3.3.8-3ubuntu3.1_amd64.deb ...
Unpacking libgnutls-deb0-28:amd64 (3.3.8-3ubuntu3.1) over (3.3.8-3ubuntu3) ...
Setting up libexpat1:amd64 (2.1.0-6ubuntu1.1) ...
Setting up libexpat1:i386 (2.1.0-6ubuntu1.1) ...
Setting up libgnutls-deb0-28:amd64 (3.3.8-3ubuntu3.1) ...
Setting up libgnutls-deb0-28:i386 (3.3.8-3ubuntu3.1) ...
Setting up libgnutls-openssl27:amd64 (3.3.8-3ubuntu3.1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
Log ended: 2015-09-01  13:53:02


After this I see a whole bunch of NUL character blocks.

**In /var/log/dpkg.log**
> 
2015-09-01 13:53:01 startup archives unpack
2015-09-01 13:53:01 upgrade libexpat1:i386 2.1.0-6ubuntu1 2.1.0-6ubuntu1.1
2015-09-01 13:53:01 status half-configured libexpat1:i386 2.1.0-6ubuntu1
2015-09-01 13:53:01 status unpacked libexpat1:i386 2.1.0-6ubuntu1
2015-09-01 13:53:01 status half-configured libexpat1:amd64 2.1.0-6ubuntu1
2015-09-01 13:53:01 status half-installed libexpat1:i386 2.1.0-6ubuntu1
2015-09-01 13:53:01 status half-installed libexpat1:i386 2.1.0-6ubuntu1
2015-09-01 13:53:01 status unpacked libexpat1:i386 2.1.0-6ubuntu1.1
2015-09-01 13:53:01 status unpacked libexpat1:i386 2.1.0-6ubuntu1.1
2015-09-01 13:53:01 upgrade libexpat1:amd64 2.1.0-6ubuntu1 2.1.0-6ubuntu1.1
2015-09-01 13:53:01 status half-configured libexpat1:amd64 2.1.0-6ubuntu1
2015-09-01 13:53:01 status unpacked libexpat1:amd64 2.1.0-6ubuntu1
2015-09-01 13:53:01 status half-installed libexpat1:amd64 2.1.0-6ubuntu1
2015-09-01 13:53:01 status half-installed libexpat1:amd64 2.1.0-6ubuntu1
2015-09-01 13:53:01 status unpacked libexpat1:amd64 2.1.0-6ubuntu1.1
2015-09-01 13:53:01 status unpacked libexpat1:amd64 2.1.0-6ubuntu1.1
2015-09-01 13:53:01 upgrade libgnutls-openssl27:amd64 3.3.8-3ubuntu3 3.3.8-3ubuntu3.1
2015-09-01 13:53:01 status half-configured libgnutls-openssl27:amd64 3.3.8-3ubuntu3
2015-09-01 13:53:01 status unpacked libgnutls-openssl27:amd64 3.3.8-3ubuntu3
2015-09-01 13:53:01 status half-installed libgnutls-openssl27:amd64 3.3.8-3ubuntu3
2015-09-01 13:53:01 status half-installed libgnutls-openssl27:amd64 3.3.8-3ubuntu3
2015-09-01 13:53:01 status unpacked libgnutls-openssl27:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:01 status unpacked libgnutls-openssl27:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:01 upgrade libgnutls-deb0-28:i386 3.3.8-3ubuntu3 3.3.8-3ubuntu3.1
2015-09-01 13:53:01 status half-configured libgnutls-deb0-28:i386 3.3.8-3ubuntu3
2015-09-01 13:53:01 status unpacked libgnutls-deb0-28:i386 3.3.8-3ubuntu3
2015-09-01 13:53:01 status half-configured libgnutls-deb0-28:amd64 3.3.8-3ubuntu3
2015-09-01 13:53:01 status half-installed libgnutls-deb0-28:i386 3.3.8-3ubuntu3
2015-09-01 13:53:01 status half-installed libgnutls-deb0-28:i386 3.3.8-3ubuntu3
2015-09-01 13:53:01 status unpacked libgnutls-deb0-28:i386 3.3.8-3ubuntu3.1
2015-09-01 13:53:01 status unpacked libgnutls-deb0-28:i386 3.3.8-3ubuntu3.1
2015-09-01 13:53:01 upgrade libgnutls-deb0-28:amd64 3.3.8-3ubuntu3 3.3.8-3ubuntu3.1
2015-09-01 13:53:01 status half-configured libgnutls-deb0-28:amd64 3.3.8-3ubuntu3
2015-09-01 13:53:01 status unpacked libgnutls-deb0-28:amd64 3.3.8-3ubuntu3
2015-09-01 13:53:01 status half-installed libgnutls-deb0-28:amd64 3.3.8-3ubuntu3
2015-09-01 13:53:02 status half-installed libgnutls-deb0-28:amd64 3.3.8-3ubuntu3
2015-09-01 13:53:02 status unpacked libgnutls-deb0-28:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 status unpacked libgnutls-deb0-28:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 startup packages configure
2015-09-01 13:53:02 configure libexpat1:amd64 2.1.0-6ubuntu1.1 <none>
2015-09-01 13:53:02 status unpacked libexpat1:amd64 2.1.0-6ubuntu1.1
2015-09-01 13:53:02 status half-configured libexpat1:amd64 2.1.0-6ubuntu1.1
2015-09-01 13:53:02 status installed libexpat1:amd64 2.1.0-6ubuntu1.1
2015-09-01 13:53:02 status triggers-pending libc-bin:amd64 2.21-0ubuntu4
2015-09-01 13:53:02 configure libexpat1:i386 2.1.0-6ubuntu1.1 <none>
2015-09-01 13:53:02 status unpacked libexpat1:i386 2.1.0-6ubuntu1.1
2015-09-01 13:53:02 status half-configured libexpat1:i386 2.1.0-6ubuntu1.1
2015-09-01 13:53:02 status installed libexpat1:i386 2.1.0-6ubuntu1.1
2015-09-01 13:53:02 configure libgnutls-deb0-28:amd64 3.3.8-3ubuntu3.1 <none>
2015-09-01 13:53:02 status unpacked libgnutls-deb0-28:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 status half-configured libgnutls-deb0-28:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 status installed libgnutls-deb0-28:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 configure libgnutls-deb0-28:i386 3.3.8-3ubuntu3.1 <none>
2015-09-01 13:53:02 status unpacked libgnutls-deb0-28:i386 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 status half-configured libgnutls-deb0-28:i386 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 status installed libgnutls-deb0-28:i386 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 configure libgnutls-openssl27:amd64 3.3.8-3ubuntu3.1 <none>
2015-09-01 13:53:02 status unpacked libgnutls-openssl27:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 status half-configured libgnutls-openssl27:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 status installed libgnutls-openssl27:amd64 3.3.8-3ubuntu3.1
2015-09-01 13:53:02 trigproc libc-bin:amd64 2.21-0ubuntu4 <none>
2015-09-01 13:53:02 status half-configured libc-bin:amd64 2.21-0ubuntu4
2015-09-01 13:53:02 status installed libc-bin:amd64 2.21-0ubuntu4
2015-09-01 13:53:02 startup packages configure


Followed by a bunch of NUL character blocks.

Now running sudo apt-get upgrade outputs this:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

Which I am of course not going to do now. Any ideas on this are appreciated.

---

### Post by s0c0 on 2015-09-06
Bumping this. Any ideas on what I can do to fix this? I can't run an apt-get upgrade without getting this erorr:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

And if I do that my system shuts down and loads into grub command line cause grub and ext4 get corrupted.

---

### Post by Bashing-om on 2015-09-06
s0c0; Well ....

Anytime I see read and write errors I get concerned about 2 things; file system integrity and the health of the hard drive.
I would - if it were me - run a file system check/repair ( from a liveDVD) and  run a SMART check on the hard drive to check its status. You can do this from a LiveDVD using disk utility or from the command line using smartctl.

If these pass, I would next inquire of the package manager the status of the installed packages.
```

sudo apt-get -f install
sudo dpkg -C

```

Depending on what is, is what do.

[INDENT][INDENT][INDENT]just my thought
[/INDENT][/INDENT][/INDENT]

---

