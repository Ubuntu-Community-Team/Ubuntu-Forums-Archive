---
title: "Problems OpenVPN,updates,dependencies"
date: 2016-01-12
forum: General Help
---

### Post by nicholas18 on 2016-01-12
Hi, I am getting an error message with OpenVPN and when I try to update/upgrade (both using sudo and as root). Here is the error message from installing OpenVPN:

```
gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-43-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-43-generic (--configure):
subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic-lts-vivid:
linux-image-generic-lts-vivid depends on linux-image-extra-3.19.0-43-generic; however:
Package linux-image-extra-3.19.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic-lts-vivid (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-vivid:No apport report written because the error message indicates its a followup error from a previous failure.

linux-generic-lts-vivid depends on linux-image-generic-lts-vivid (= [3.19.0.43]("http://hackforums.net/ipcheck.php?action=iplookup&ipaddress=3.19.0.43").28); however:
Package linux-image-generic-lts-vivid is not configured yet.

dpkg: error processing package linux-generic-lts-vivid (--configure):
dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


So there it is, I do have a cell phone charger hooked up to my computer, but I chose "charge only" not storage on the phone when hooking up. I will also post what I get when I update/upgrade (I have always had to do that as root due to a lock on /usr/bin/ I believe (I think that is where the lock is). I will try update && upgrade and post that message as well and have disconnected the charger although I think it has nothing to do with it

Ok, here is trying to apt-get update && apt-get upgrade as root:

```
update-initramfs: Generating /boot/initrd.img-3.19.0-43-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-43-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic-lts-vivid:
 linux-image-generic-lts-vivid depends on linux-image-extra-3.19.0-43-generic; however:
  Package linux-image-extra-3.19.0-43-generic is not configured yet.

dpkg: error processing package linux-image-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-vivid:
 linux-generic-lts-vivid depends on linux-image-generic-lts-vivid (= [3.19.0.43]("http://hackforums.net/ipcheck.php?action=iplookup&ipaddress=3.19.0.43").28); however:
  Package linux-image-generic-lts-vivid is not configured yet.

dpkg: error processing package linux-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
Setting up libgcc1:i386 (1:4.9.3-0ubuntu4) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Setting up libgcc1:amd64 (1:4.9.3-0ubuntu4) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


If anyone can help me figure this out it would be greatly appreciated.  Also everything except my mouse was disconnected on that last one.

Thank you in advance for your time,
nicholas

P.S. wasn't sure if I should have just put this in updates/upgrades but it has problems with dependencies/OpenVPN...,so I wasn't sure.  I can actually get the lock to appear for the VPN but when I go to sites like "whatismyIP.com" it still says my IP

---

### Post by SeijiSensei on 2016-01-12
You probably have a separate partition for /boot that isn't large enough to store another kernel.  Start by running "sudo apt-get autoremove" and see if that gets rid of some stale kernels.  Otherwise you'll need to remove some manually.  Search this forum for other postings about "/boot" to see how.

---

### Post by nicholas18 on 2016-01-12
Thank you, will run that command and let you know how it works out.

---

### Post by nicholas18 on 2016-01-12
here is what happened:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-extra-3.19.0-43-generic (3.19.0-43.49~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-43-generic /boot/vmlinuz-3.19.0-43-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-43-generic /boot/vmlinuz-3.19.0-43-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-43-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.19.0-43-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-3.19.0-43-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic-lts-vivid:
 linux-image-generic-lts-vivid depends on linux-image-extra-3.19.0-43-generic; however:
  Package linux-image-extra-3.19.0-43-generic is not configured yet.


dpkg: error processing package linux-image-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-vivid:
 linux-generic-lts-vivid depends on linux-image-generic-lts-vivid (= 3.19.0.43.28); however:
  Package linux-image-generic-lts-vivid is not configured yet.


dpkg: error processing package linux-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by nicholas18 on 2016-01-12
can I enlarge the partition for /boot?  Should I try as root?

---

### Post by SeijiSensei on 2016-01-12
You can only expand /boot if there's enough contiguous free space on the disk.  That's usually not very likely.

Run "ls /boot" and see how many different kernels there are.  They'll probably be called vmlinuz-something-generic.  My current kernel is 3.13.0-58.  If you have more than one kernel lying around, start with the oldest one and run
```
sudo apt-get remove linux-image-3.x.x-x-generic
```
and work your way forward.

Most of the time this isn't an issue unless you chose to encrypt your disk at installation.  On normal unencrypted systems, /boot is part of the basic filesystem tree so it usually has lots of space to work in.

If none of this works, you may have to apply brute force.  Simply delete (with sudo) the oldest set of files with identical version numbers and see if that helps.

---

### Post by nicholas18 on 2016-01-12
here is what I get when I look at the list of kernals:

```
>dpkg -l linux-*   <-command
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  linux-firmware 1.127.19     all          Firmware for Linux kernel drivers
iU  linux-generic- 3.19.0.43.28 amd64        Complete Generic Linux kernel and
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 3.19.0-31.36 all          Header files related to Linux ker
ii  linux-headers- 3.19.0-31.36 amd64        Linux kernel headers for version 
ii  linux-headers- 3.19.0-33.38 all          Header files related to Linux ker
ii  linux-headers- 3.19.0-33.38 amd64        Linux kernel headers for version 
ii  linux-headers- 3.19.0-39.44 all          Header files related to Linux ker
ii  linux-headers- 3.19.0-39.44 amd64        Linux kernel headers for version 
ii  linux-headers- 3.19.0-42.48 all          Header files related to Linux ker
ii  linux-headers- 3.19.0-42.48 amd64        Linux kernel headers for version 
ii  linux-headers- 3.19.0-43.49 all          Header files related to Linux ker
ii  linux-headers- 3.19.0-43.49 amd64        Linux kernel headers for version 
ii  linux-headers- 3.19.0.43.28 amd64        Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
un  linux-image-3. <none>       <none>       (no description available)
rc  linux-image-3. 3.19.0-25.26 amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.19.0-31.36 amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.19.0-33.38 amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.19.0-39.44 amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.19.0-42.48 amd64        Linux kernel image for version 3.
ii  linux-image-3. 3.19.0-43.49 amd64        Linux kernel image for version 3.
rc  linux-image-ex 3.19.0-25.26 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 3.19.0-31.36 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 3.19.0-33.38 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 3.19.0-39.44 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 3.19.0-42.48 amd64        Linux kernel extra modules for ve
iF  linux-image-ex 3.19.0-43.49 amd64        Linux kernel extra modules for ve
iU  linux-image-ge 3.19.0.43.28 amd64        Generic Linux kernel image
un  linux-initramf <none>       <none>       (no description available)
un  linux-initramf <none>       <none>       (no description available)
un  linux-kernel-h <none>       <none>       (no description available)
un  linux-kernel-l <none>       <none>       (no description available)
ii  linux-libc-dev 3.13.0-74.11 amd64        Linux Kernel Headers for developm
un  linux-lts-vivi <none>       <none>       (no description available)
un  linux-restrict <none>       <none>       (no description available)
ii  linux-sound-ba 1.0.25+dfsg- all          base package for ALSA and OSS sou
```

---

### Post by nicholas18 on 2016-01-12
And when I use uname -r I get:

3.19.0-43-generic

Sorry for all the posts.  does that mean I can delete everything not 3.19.0-43 and how?

If this is the list can I get rid of what is starred?

[COLOR=#000000][FONT=Verdana]Desired=Unknown/Install/Remove/Purge/Hold[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]||/ Name Version Architecture Description[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]+++-==============-============-============-=================================[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-firmware 1.127.19 all Firmware for Linux kernel drivers[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]iU linux-generic- 3.19.0.43.28 amd64 Complete Generic Linux kernel and[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-headers <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-headers- <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-headers- <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-31.36 all Header files related to Linux ker *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-31.36 amd64 Linux kernel headers for version * [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-33.38 all Header files related to Linux ker * [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-33.38 amd64 Linux kernel headers for version *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-39.44 all Header files related to Linux ker *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-39.44 amd64 Linux kernel headers for version *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-42.48 all Header files related to Linux ker * [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-42.48 amd64 Linux kernel headers for version *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-43.49 all Header files related to Linux ker[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0-43.49 amd64 Linux kernel headers for version [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-headers- 3.19.0.43.28 amd64 Generic Linux kernel headers[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-image <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-image-3. <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rc linux-image-3. 3.19.0-25.26 amd64 Linux kernel image for version 3. *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-image-3. 3.19.0-31.36 amd64 Linux kernel image for version 3. * [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-image-3. 3.19.0-33.38 amd64 Linux kernel image for version 3. * [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-image-3. 3.19.0-39.44 amd64 Linux kernel image for version 3. *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-image-3. 3.19.0-42.48 amd64 Linux kernel image for version 3. *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-image-3. 3.19.0-43.49 amd64 Linux kernel image for version 3.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]rc linux-image-ex 3.19.0-25.26 amd64 Linux kernel extra modules for ve *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-image-ex 3.19.0-31.36 amd64 Linux kernel extra modules for ve *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-image-ex 3.19.0-33.38 amd64 Linux kernel extra modules for ve * [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-image-ex 3.19.0-39.44 amd64 Linux kernel extra modules for ve * [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-image-ex 3.19.0-42.48 amd64 Linux kernel extra modules for ve *[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]iF linux-image-ex 3.19.0-43.49 amd64 Linux kernel extra modules for ve[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]iU linux-image-ge 3.19.0.43.28 amd64 Generic Linux kernel image[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-initramf <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-initramf <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-kernel-h <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-kernel-l <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-libc-dev 3.13.0-74.11 amd64 Linux Kernel Headers for developm[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-lts-vivi <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]un linux-restrict <none> <none> (no description available)[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ii linux-sound-ba 1.0.25+dfsg- all base package for ALSA and OSS sou[/FONT][/COLOR]

---

### Post by nicholas18 on 2016-01-12
I found this, made a list of what it is using and am now purging.  Here is the site:

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by nicholas18 on 2016-01-12
Ok, all I got now when update/upgrading is:

Fetched 3,806 kB in 12s (311 kB/s)                                             
Reading package lists... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@nick-Satellite-L505D:~# apt-get install OpenVPN
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openvpn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by nerdtron on 2016-01-12
> **nicholas18 said:**
> Ok, all I got now when update/upgrading is:

Fetched 3,806 kB in 12s (311 kB/s)                                             
Reading package lists... Done
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@nick-Satellite-L505D:~# apt-get install OpenVPN
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openvpn is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Output looks OK to me, except for the duplicate entries, which are not big deal. Just to be sure the opevpn is upgraded, you can try to run again:
```
 sudo apt-get update
sudo apt-get upgrade openvpn 
```

I used "upgrade" since openvpn is already installed on your system.

---

### Post by ian-weisser on 2016-01-12
You will need to run autoremove periodically to keep your /boot from filling up again.
Autoremove, which only works *before* the partition is full, is much easier and safer than fixing the problem after a full /boot has broken apt.
And, using a setting in unattended-upgrades, prevention can be completely automatic.

By the way, this issue is a known bug in process of fix: [LP# 1357093]("https://bugs.launchpad.net/bugs/1357093")

---

### Post by nicholas18 on 2016-01-12
I had a big long response written here and then I had an error and didn't even get to copy it!  Well now sudo apt-get update and upgrade seem to work, where as before there was a lock on /var/lib/ or /usr/bin/ (not coming up now).  I think we pretty much can consider this one solved other than the VPN still doesn't say a different IP but maybe now that I have the latest version of OpenVPN and no dependency problems with it that is the VPN provider's problem?  Also, they said to try the command (even though I set up VPN connections in the menu) sudo OpenVPN --config config.ovpn and it says that isn't a command.

I'm actually studying right now compTIA A+ (would be doing "learn linux the hard way" but I figure if I pump out A+, network+, server+, security+ that I will definitely get a help desk job (actually maybe just with A+ or A+ and network or server+)- I plan on either getting linux+ and/or going further into security after as EVENTUALLY I'd like to get into penetration testing/malware analysis or as a second choice linux systems administration).  I also want to start learning a programming language (a first one- I'm thinking python).  These events show me how much I have to learn....then again the help desk person for my local cable company didn't even know what ubuntu or linux was so maybe I can at least get a basic job with a couple months of studying to get A+ and another cert then work on more and move up.

Thank you to everyone that responded- and yeah they really should fix this so kernals that are no longer needed are deleted when replaced.

---

### Post by ian-weisser on 2016-01-12
> **nicholas18 said:**
> before there was a lock on /var/lib/ 
Most likely you were trying to run two package manager actions at the same time, or simply had two open. You mustn't do that.

> **nicholas18 said:**
> they really should fix this so kernals that are no longer needed are deleted when replaced.
Developers gnash their teeth when people say 'the system should...' while there are very good use cases why the system certainly shouldn't.
Happily, this is open source. You are now 'they,' and you are welcome to help the developers tease out those use cases and code appropriately.

---

