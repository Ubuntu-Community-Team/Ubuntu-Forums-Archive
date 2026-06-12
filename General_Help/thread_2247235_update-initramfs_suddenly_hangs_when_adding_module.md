---
title: "update-initramfs suddenly hangs when adding module"
date: 2014-10-06
forum: General Help
---

### Post by BearT on 2014-10-06
Hi, 

I'm running my Ubuntu (currently 12.04) on encrypted disks (LVM/LUKS) for years now without any problems. Recently I saw that update-initramfs didn't finish and hang for even days. I'm now really hesitating to reboot my machine fearing it won't come up again and I'd have to setup my system again and restore all data from backups which would take some time I really don't want to spend. After searching around I found the -v option for update-initramfs and manually started it again and it got stuck as before but I know now it's always stopping at [FONT=Courier New]Adding module /lib/modules/3.2.0-69-generic/kernel/crypto/deflate.ko[/FONT]. But apart from knowing there's some trouble with the deflate module I'm not really any wiser now. I did not find any troubles (reported via google) particularly connected to the deflate module. I monitored about everything that seemed to made sense in /var/log but there I couldn't find anything when update-initramfs was called. At the moment I don't have a clue how to debug this further and keep my system alive as is without reinstalling a new system.

I'd be really grateful if you could provide some tips and hints for where to look for problems.

thanks,
BearT

---

### Post by TheFu on 2014-10-06
This is a shot in the dark, but is the /boot partition full?  
df -i
df -h
if either of those show 100% - don't reboot yet.

---

### Post by BearT on 2014-10-07
No unfortunately not. I've just recently removed old kernels. 
df -h
[FONT=Courier New]/dev/sda1                                   228M   62M  154M  29% /boot[/FONT]
df -i
[FONT=Courier New]/dev/sda1                                     124496    237    124259    1% /boot[/FONT]

---

### Post by TheFu on 2014-10-07
Yeah, it was a shot in the dark. 
I'd verify that my backups were solid, then pick a less-bad time to do the reboot when I could spend the necessary time to rebuild the machine. Perhaps Saturday morning?  Then, hope for the best from the reboot.

---

### Post by matt_symes on 2014-10-07
Hi

If you have an older kernel in /boot as well as the one you are currently using, can you not boot into the older kernel ?

It should have a valid initramfs file and so rebooting should not be a problem ?

The above are questions and not statements.

Kind regards

---

### Post by BearT on 2014-10-07
> **matt_symes said:**
> 
If you have an older kernel in /boot as well as the one you are currently using, can you not boot into the older kernel ?

It should have a valid initramfs file and so rebooting should not be a problem ?


Yeah, the -67 version of the Kernel *should* be bootable, but I didn't dare trying that yet. I wanted to figure out if I could maybe update-initramfs successfully *before* actually rebooting. If booting an older kernel really works I'd probably be fine until the holidays and then setup a new 14.04 system but if it fails I'll be staring at a black screen so trying that out is really my last resort when I had to reboot anyway.

---

### Post by matt_symes on 2014-10-07
Hi 

> **BearT said:**
> Yeah, the -67 version of the Kernel *should* be bootable, but I didn't dare trying that yet. I wanted to figure out if I could maybe update-initramfs successfully *before* actually rebooting. If booting an older kernel really works I'd probably be fine until the holidays and then setup a new 14.04 system but if it fails I'll be staring at a black screen so trying that out is really my last resort when I had to reboot anyway.

Understood about rebooting.

What i was going to suggest is boot into an older kernel, purge the newest kernel, clean all cached dkpg packages and then reinstall the newest kernel and see if that helps as it should recreate the new initramfs when it installs the new kernel.

Anyway, rebooting aside, as the new initramfs is not being created, you could try deleting it and recreating it.

```
sudo update-initramfs -k $(uname -r) -d
```

```
sudo apt-get clean
```

```
sudo update-initramfs -u
```

If that works.

```
sudo update-grub
```

That may or may not help but there is less of a risk as no rebooting is required. 

I don't know if it will work as it's not a problem i have ever had so i am not talking from experience.

EDIT:

Should probably be calling dpkg to reconfigure the kernel here as well.

Kind regards

---

### Post by BearT on 2014-10-07
Also removing the old image does not help. update-initramfs gets stuck regardless of the kernel version when adding deflate.ko. I'm starting to think there's something wrong with that. Maybe I'll try to figure out which package installed deflate.ko and reinstalling that. Otherwise it seems I'll have to install a new system.

Thanks for all your help so far.

---

### Post by matt_symes on 2014-10-07
Hi

> **BearT said:**
> Also removing the old image does not help. update-initramfs gets stuck regardless of the kernel version when adding deflate.ko. I'm starting to think there's something wrong with that. Maybe I'll try to figure out which package installed deflate.ko and reinstalling that. Otherwise it seems I'll have to install a new system.

Thanks for all your help so far.

I'm not sure i've really helped you :)

Kind regards

---

### Post by BearT on 2014-10-08
Actually I don't have any idea what just happend. But some magic(TM) happened and it worked. I did a normal apt-get upgrade call and it installed updates to linux-firmware and man-db and tried to configure the 3.2.0-69-generic kernel package (of course, it couldn't finish installation until now) and initramfs-tools (which hadn't been only partially installed before but it was now). Anyway, it installed all of this and somehow finished within a minute. I really don't know why that happend, and I'm afraid no one reading this thread will ever have any chance to learn from it, but I'm happy for now. I'll recheck my backup twice and then reboot, but I'm pretty sure there won't be any problem.

Thanks again for your advices and I'll set this thread to solved (just because there is no 'it magically works now' tag)

regards,
BearT

---

### Post by matt_symes on 2014-10-08
Hi

> **BearT said:**
> Actually I don't have any idea what just happend. But some magic(TM) happened and it worked. I did a normal apt-get upgrade call and it installed updates to linux-firmware and man-db and tried to configure the 3.2.0-69-generic kernel package (of course, it couldn't finish installation until now) and initramfs-tools (which hadn't been only partially installed before but it was now). Anyway, it installed all of this and somehow finished within a minute. I really don't know why that happend, and I'm afraid no one reading this thread will ever have any chance to learn from it, but I'm happy for now. I'll recheck my backup twice and then reboot, but I'm pretty sure there won't be any problem.

Thanks again for your advices and I'll set this thread to solved (just because there is no 'it magically works now' tag)

regards,
BearT

LOL&#8482; :D

Kind regards

---

