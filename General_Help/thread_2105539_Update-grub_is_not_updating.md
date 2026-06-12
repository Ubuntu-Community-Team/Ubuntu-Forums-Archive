---
title: "Update-grub is not updating?"
date: 2013-01-16
forum: General Help
---

### Post by oxf on 2013-01-16
Hi,

I removed some older kernels from my system and afterwards ran update-grub but when I boot up they are still listed in the grub spalsh menu. How do I get rid of them?

I've searched around and everything tells me to "sudo update-grub" which I've already done"

thanks

---

### Post by mcduck on 2013-01-16
Are you sure you removed _all_ packages related to those old kernel versions? Including headers etc? Doing that should automatically remove them from Grub (without you even having to run *sudo update-grub* manually)

---

### Post by ammofreak on 2013-01-16
Hi ):P:
Please use the following at the terminal (Cntl+Alt+t): *sudo apt-get autoremove*

I hope this works for you. One can also configure **Unattended Upgrades** but I have heard the kernels persist for awhile with this option. Since I have never used this option, I cannot personally say for sure.

---

### Post by oxf on 2013-01-16
):P ha!

Uhm I ran "sudo apt-get purge linux-image............" 
and then "grub-update"

I'll try the auto remove and report back in a few mins

Thanks
Caitlin

---

### Post by oxf on 2013-01-16
Nope that didn't do it.  I know the kernel is gone because if I select it to boot it tel me it cant find it. Sooo?

Caitlin

---

### Post by mcduck on 2013-01-16
> **oxf said:**
> Nope that didn't do it.  I know the kernel is gone because if I select it to boot it tel me it cant find it. Sooo?

Caitlin

Like I said, you need to remove the linux-image and all related packages headers etc. It's unclear from your previous answer if you only removed the kernel image or everything else as well...

---

### Post by oxf on 2013-01-16
> **mcduck said:**
> Like I said, you need to remove the linux-image and all related packages headers etc. It's unclear from your previous answer if you only removed the kernel image or everything else as well...

OK so the purge just removes the kernel and not the headers. I guess I need to go and remove them in Synaptic then.

Thanks

---

### Post by mcduck on 2013-01-16
> **oxf said:**
> OK so the purge just removes the kernel and not the headers. I guess I need to go and remove them in Synaptic then.

Thanks

yeah, the purge option in apt-get simply means that it should remove any (system-wide) configuration files related to the package while uninstalling it.

---

### Post by oxf on 2013-01-16
Well this is quite bizarre. I've gone through Synaptic, searching by the kernel number and removed the headers. I've tried a couple of times and I can't find anythig else relating to it. However, that kernel is -still- showing up in grub!

The only other thing I should mention is the other OS I have on the second partiton is Lubuntu 12.04. Could that be confusing the grub file? i wouldn't have thought so but....


Caitlin

---

### Post by mcduck on 2013-01-16
You should have a package called "linux-headers-*someversionnumber*-generic" for each kernel version.

Anyway, since you do have a separate Lubuntu install, are you sure the Ubuntu install is the one in control of Grub? If you installed Lubuntu after Ubuntu, and didn't specifically tell it to not install a bootloader, Grub would actually be controlled by the config files in your Lubuntu partition instead... That's definitely something worth checking.

---

### Post by oxf on 2013-01-16
Ah I think thats the problem then. 
Ubuntu's been on the laptop for a couple of months now and earlier this week I added Lubuntu and yes I did add the bootloader when I created the startup USB drive.

The removed kernal in question was in the Ubuntu partition but I suppose the bootloader controled by Lubuntu has not been updated. I'm not at home now so will play with it later

Thanks

---

### Post by mcduck on 2013-01-16
> **oxf said:**
> Ah I think thats the problem then. 
Ubuntu's been on the laptop for a couple of months now and earlier this week I added Lubuntu and yes I did add the bootloader when I created the startup USB drive.

The removed kernal in question was in the Ubuntu partition but I suppose the bootloader controled by Lubuntu has not been updated. I'm not at home now so will play with it later

Thanks

No problem, I hope running update-grub in the Lubuntu system solves the issue. :)

---

### Post by grahammechanical on 2013-01-16
If you want to put the Ubuntu version of Grub back in control then boot into Ubuntu and run

```
sudo update-grub
```

```
sudo grub-install /dev/sda
```

if sda is the only hard disk and where you want Grub to be. That will overwrite the Lubuntu Grub files in the MBR.

Regards.

---

### Post by oxf on 2013-01-16
> **grahammechanical said:**
> If you want to put the Ubuntu version of Grub back in control then boot into Ubuntu and run

```
sudo update-grub
``````
sudo grub-install /dev/sda
```if sda is the only hard disk and where you want Grub to be. That will overwrite the Lubuntu Grub files in the MBR.

Regards.

Problem solved thanks!

Ok this might seem like a silly question but where exasctly is the MBR? Iis it seperate from the partitions the OS's are on? What I mean is if I install OS1 and than later OS2 is installed on a new partition and its bootloader then overwrites and takes control of the first one it would have to be on sda but not actually within sda1 or sda2. Am I understanding this correctly?

Caitlin

---

### Post by mcduck on 2013-01-17
> **oxf said:**
> Problem solved thanks!

Ok this might seem like a silly question but where exasctly is the MBR? Iis it seperate from the partitions the OS's are on? What I mean is if I install OS1 and than later OS2 is installed on a new partition and its bootloader then overwrites and takes control of the first one it would have to be on sda but not actually within sda1 or sda2. Am I understanding this correctly?

Caitlin

Yeah, you got it right. The master boot record is in the beginning of the hard drive, before any partitions. It contains the partition table describing the disk's layout, and instructions for the computer to find the correct partition to boot from. Grub installs it's first stage into MBR, while the other stages and all the configuration files are in your root partition.

---

### Post by oxf on 2013-01-17
> **mcduck said:**
> Yeah, you got it right. The master boot record is in the beginning of the hard drive, before any partitions. It contains the partition table describing the disk's layout, and instructions for the computer to find the correct partition to boot from. Grub installs it's first stage into MBR, while the other stages and all the configuration files are in your root partition.

ok thanks, now I understand how it all works!

---

