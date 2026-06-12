---
title: "Ubuntu won't load"
date: 2007-09-01
forum: General Help
---

### Post by avantgardaclue on 2007-09-01
Strange thing this morning. Went to check my emails, clicked the thunderbird icon... didn't load, clicked the firefox icon didn't load, clicked the update icon and just the outer shape of the update window opened. Had to do a hard reboot and then it wouldn't and tons of code kept appearing. Kept having to do hard reboots, tried safe mode, again loads of code until eventually it came to a place where i was clearly expected to type something in but what?

Good job i still have a windows drive (hangs head in shame!) that enables me to get on to the internet, but in my defence i do use it blackboxed with BBLean.

Call me a conspiracy theorist but this did happen on September 1st

All help gratefully appreciated... Simon
Hants England

---

### Post by loell on 2007-09-01
i am posting this from windoze, as i can't load it, after the kernel update.

i just did not  listen to my gut instinct , kernel security updates should never be trusted.

sorry but thats how i feel, that's what i've observed even in the past. sadly one of the weakneases of ubuntu dekstop :(

---

### Post by por100pre1 on 2007-09-01
Hey guys! Have you linux-image-2.6.20-15-generic installed? If so, have you tried? No problems here, but agree, theres a serious bug in this update.

EDIT: Try if this other kernel installs ok:

```
sudo aptitude install linux-lowlatency
```

---

### Post by be4truth on 2007-09-01
You should be able to load the old kernel. I had no problems with the last kernel update. I think the more customize and hacked an Ubuntu installation is, the more trouble one has with everything. That is my experience. It is not Ubuntu but the freedom to change and customize almost everything around it.
Do you do that with your Windows?

---

### Post by loell on 2007-09-01
> **be4truth said:**
> You should be able to load the old kernel. I had no problems with the last kernel update. I think the more customize and hacked an Ubuntu installation is, the more trouble one has with everything. That is my experience. It is not Ubuntu but the freedom to change and customize almost everything around it.
Do you do that with your Windows?

that's not the issue here, the issue of releasing a solid kernel update is very  important.

---

### Post by buzzmandt on 2007-09-01
kernel update this morning to .16
Now won't load
loaded kernel .15 and it works just fine

what happened?

Should i remove the .16 kernel option from grub and only run the .15?

---

### Post by por100pre1 on 2007-09-01
I think both are kind of right. Loell do yo have the previous kernel?

---

### Post by por100pre1 on 2007-09-01
> **buzzmandt said:**
> kernel update this morning to .16
Now won't load
loaded kernel .15 and it works just fine

what happened?

Should i remove the .16 kernel option from grub and only run the .15?

Try reinstalling it. Try using the kernel I previously posted.

---

### Post by loell on 2007-09-01
> **por100pre1 said:**
> I think both are kind of right. Loell do yo have the previous kernel?

yes i have, and it won't load. i did a remedy by guessing the hd number ie **hd(0,1)** to **hd(0,0)**
this problem is entirely the update itself, the thing is it modify's your menu.lst

if you can see the previous threads from the past hours, the porblems are raning from menu.lst ,alsa issue, and some are xorg issues.

going back to what i've said, this happened in the past , where kernel updates do prove to be not smooth.

---

### Post by por100pre1 on 2007-09-01
> **loell said:**
> yes i have, and it won't load. i did a remedy by guessing the hd number ie **hd(0,1)** to **hd(0,0)**
this problem is entirely the update itself, the thing is it modify's your menu.lst

if you can see the previous threads from the past hours, the porblems are raning from menu.lst ,alsa issue, and some are xorg issues.

going back to what i've said, this happened in the past , where kernel updates do prove to be not smooth.

I have seen threads about xorg-conf issues. This is really serious! :mad:

---

### Post by loell on 2007-09-01
yeah, i could imagine, that this is huge. more of this will come from all around the globe.

---

### Post by buzzmandt on 2007-09-01
Mine seemed to go smooth until it got to X
said something about a resume image not found

then X failed to load screen came up and it said something along the lines of
screens were found but none were usable

when i rebooted and chose the previous .15 option, it loaded just fine and i'm running again.

I editied /boot/grub/menu.lst and commented out the new .16 kernel so it will auto boot the previous.15 that works until I can find a better fix or am brave enough to try some suggestions

---

### Post by kostkon on 2007-09-01
> **buzzmandt said:**
> Mine seemed to go smooth until it got to X
said something about a resume image not found

then X failed to load screen came up and it said something along the lines of
screens were found but none were usable

when i rebooted and chose the previous .15 option, it loaded just fine and i'm running again.

I editied /boot/grub/menu.lst and commented out the new .16 kernel so it will auto boot the previous.15 that works until I can find a better fix or am brave enough to try some suggestions

Do you have an *Nvidia* or *ATI* graphics card? Did you use *Automatix* or *Envy* to install the driver for your graphics card?

Many people after a kernel update will have problems with their X server. They don't know that by using these tools, their X server will likely be broken after such an update.

The same will happen for people that changed their Grub menu list manually.

Thus, in other words, it is not kernel fault necessarily for any problems that people will face. The kernel is stable enough, I believe.

---

### Post by buzzmandt on 2007-09-01
> **kostkon said:**
> Do you have an *Nvidia* or *ATI* graphics card? Did you use *Automatix* or *Envy* to install the driver for your graphics card?

Many people after a kernel update will have problems with their X server. They don't know that by using these tools, their X server will likely be broken after such an update.

The same will happen for people that changed their Grub menu list manually.

Thus, in other words, it is not kernel fault necessarily for any problems that people will face. The kernel is stable enough, I believe.

I have Nvidia card
did not use automatix or envy
did not manually edit grub until after the kernel update
did, however, manually edit X for nvidia driver

after the kernel update wouldn't load X, I checked it and it didn't seem to have any changes, nvidia was still the driver and such

could i boot to .16 and do a dpkg reconfigure X or something like that?

---

### Post by por100pre1 on 2007-09-01
> **buzzmandt said:**
> I have Nvidia card
did not use automatix or envy
did not manually edit grub until after the kernel update
did, however, manually edit X for nvidia driver

after the kernel update wouldn't load X, I checked it and it didn't seem to have any changes, nvidia was still the driver and such

could i boot to .16 and do a dpkg reconfigure X or something like that?

If you can login give it a try. :-k

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

(so other readers can benefit...)

---

### Post by st33med on 2007-09-01
There was a reason for the update:
[http://www.ubuntu.com/usn/usn-510-1]("http://www.ubuntu.com/usn/usn-510-1")

I'm using the .22-10 kernel on feisty, so I don't have to worry.

And, sorry for that long code :)

---

### Post by avantgardaclue on 2007-09-01
>>=========================================================== Ubuntu Security Notice USN-510-1 August 31, 2007 linux-source-2.6.20 vulnerabilities CVE-2007-2525, CVE-2007-2875, CVE-2007-2876, CVE-2007-2878, CVE-2007-3104, CVE-2007-3105, CVE-2007-3513, CVE-2007-3642, CVE-2007-3843, CVE-2007-3848, CVE-2007-3851, CVE-2007-4308 =========================================================== A security issue affects the following Ubuntu releases: Ubuntu 7.04 This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu. The problem can be corrected by upgrading your system to the following package versions: Ubuntu 7.04: linux-image-2.6.20-16-386 2.6.20-16.31 linux-image-2.6.20-16-generic 2.6.20-16.31 linux-image-2.6.20-16-hppa32 2.6.20-16.31 linux-image-2.6.20-16-hppa64 2.6.20-16.31 linux-image-2.6.20-16-itanium 2.6.20-16.31 linux-image-2.6.20-16-lowlatency 2.6.20-16.31 linux-image-2.6.20-16-mckinley 2.6.20-16.31 linux-image-2.6.20-16-powerpc 2.6.20-16.31 linux-image-2.6.20-16-powerpc-smp 2.6.20-16.31 linux-image-2.6.20-16-powerpc64-smp 2.6.20-16.31 linux-image-2.6.20-16-server 2.6.20-16.31 linux-image-2.6.20-16-server-bigiron 2.6.20-16.31 linux-image-2.6.20-16-sparc64 2.6.20-16.31 linux-image-2.6.20-16-sparc64-smp 2.6.20-16.31 After a standard system upgrade you need to reboot your computer to affect the necessary changes. Details follow: A flaw was discovered in the PPP over Ethernet implementation. Local attackers could manipulate ioctls and cause kernel memory consumption leading to a denial of service. (CVE-2007-2525) An integer underflow was discovered in the cpuset filesystem. If mounted, local attackers could obtain kernel memory using large file offsets while reading the tasks file. This could disclose sensitive data. (CVE-2007-2875) Vilmos Nebehaj discovered that the SCTP netfilter code did not correctly validate certain states. A remote attacker could send a specially crafted packet causing a denial of service. (CVE-2007-2876) Luca Tettamanti discovered a flaw in the VFAT compat ioctls on 64-bit systems. A local attacker could corrupt a kernel_dirent struct and cause a denial of service. (CVE-2007-2878) A flaw in the sysfs_readdir function allowed a local user to cause a denial of service by dereferencing a NULL pointer. (CVE-2007-3104) A buffer overflow was discovered in the random number generator. In environments with granular assignment of root privileges, a local attacker could gain additional privileges. (CVE-2007-3105) A flaw was discovered in the usblcd driver. A local attacker could cause large amounts of kernel memory consumption, leading to a denial of service. (CVE-2007-3513) Zhongling Wen discovered that the h323 conntrack handler did not correctly handle certain bitfields. A remote attacker could send a specially crafted packet and cause a denial of service. (CVE-2007-3642) A flaw was discovered in the CIFS mount security checking. Remote attackers could spoof CIFS network traffic, which could lead a client to trust the connection. (CVE-2007-3843) It was discovered that certain setuid-root processes did not correctly reset process death signal handlers. A local user could manipulate this to send signals to processes they would not normally have access to. (CVE-2007-3848) The Direct Rendering Manager for the i915 driver could be made to write to arbitrary memory locations. An attacker with access to a running X11 session could send a specially crafted buffer and gain root privileges. (CVE-2007-3851) It was discovered that the aacraid SCSI driver did not correctly check permissions on certain ioctls. A local attacker could cause a denial of service or gain privileges. (CVE-2007-4308)<<

" The problem can be corrected by upgrading your system to the following package versions: Ubuntu 7.04: linux-image-2.6.20-16-386 2.6.20-16.31"

How do you do this if you can't reboot?

---

### Post by st33med on 2007-09-01
> **avantgardaclue said:**
> 

How do you do this if you can't reboot?

No, no. That was the reason for upgrading the kernel.

And, if it doesn't reboot after clicking the restart button, do Ctrl-Alt-Backspace. It kills all processes and restarts it if you have already hit the restart button.

---

### Post by john8791 on 2007-09-01
> **be4truth said:**
> You should be able to load the old kernel. I had no problems with the last kernel update. I think the more customize and hacked an Ubuntu installation is, the more trouble one has with everything. That is my experience. It is not Ubuntu but the freedom to change and customize almost everything around it.
Do you do that with your Windows?

Isn't choice and freedom the whole point of Linux?  I used Automatix to get the PROPER Nvidia drivers loaded.  Sounds like the kernel update will break this.  It's a shame the Ubuntu and Automatix folks can't get along.  I think I will skip this update for a whle.

---

### Post by avantgardaclue on 2007-09-03
Hi Guys, whilst i'm sure what has been said has helped some people but no me i'm afraid!:confused:

I still cannot get my ubuntu to start, i have no ideas left as to what i need to do:confused:

I have some valuable pictures on the hard drive. I have used my copy of damn small linux to navigate my way to the relevant directories but evidently i do not have the necessary permissions to read or copy to a flash drive.:confused:](*,)

I just don't understand what is going on, Sept 1st update has right royally screwed up my system, what is Michael Dell gonna be thinking if all his linux systems start failing like this? #-o#-o

Simon

---

### Post by JeffreyRatcliffe on 2007-09-03
I can boot, but not print to my HP OfficeJet 5510.

---

### Post by JeffreyRatcliffe on 2007-09-03
> **JeffreyRatcliffe said:**
> I can boot, but not print to my HP OfficeJet 5510.

Scratch that. User error.

---

### Post by Schugy on 2007-10-14
After leaving alone my spare PC for a few weeks I've tried a few things yesterday.

My problem was that 2.6.20-16-generic and 2.6.20-16-386 didn't boot.

I've tried a lot of things like reinstalling nvidia-glx-new-drivers (for my old GF2MX200) for conole-modes e.g..

But then I've noticed that my 50MB-bott partition ran out of diskspace.

After wiping off the unusable initrd's from the boot-partition to get some disk space, installing the linux-restricted-modules-2.6.20-16-386 and doing a dpkg-reconfigure linux-image-2.6.20-16-386 everything is fine now.

Even the PATA-mode increased from 6MB/sec to 38MB/sec because the 2.6.20-15-generic doesn't support my SIS735-chipset very well.

---

