---
title: "Simplify Dual Boot Please"
date: 2012-10-29
forum: General Help
---

### Post by Jcpayne on 2012-10-29
Currently I have Ubuntu 12.04 64 bit installed.  Today I purchased Windows 8 Pro, and I'd like to dual boot them.  I understand this is easier done to install windows first and then install linux afterwards, but I'd like to do the opposite, seeing as I already have ubuntu installed.

Can someone give me a very dumb downed explanation as to how to accomplish this?  I would like to retain the settings I have in Ubuntu, which is why I don't want to reinstall it.  It took me a while to get my screens and Wine set up properly.  

Step by step would be extremely appreciated.  I would like to be given the option at startup whether I boot into Linux or Windows.

Thanks

---

### Post by BlueBinary on 2012-10-29
> **Jcpayne said:**
> Currently I have Ubuntu 12.04 64 bit installed.  Today I purchased Windows 8 Pro, and I'd like to dual boot them.  I understand this is easier done to install windows first and then install linux afterwards, but I'd like to do the opposite, seeing as I already have ubuntu installed.

Can someone give me a very dumb downed explanation as to how to accomplish this?  I would like to retain the settings I have in Ubuntu, which is why I don't want to reinstall it.  It took me a while to get my screens and Wine set up properly.  

Step by step would be extremely appreciated.  I would like to be given the option at startup whether I boot into Linux or Windows.

Thanks
When Installing Windows 8, there should be a "Create Partition" Option. This "Splits" the hard drive drive. Create a Partition and install Windows 8 onto that. Then when booting, access your BIOS and under boot options load it from that partition.
If I'm wrong I'm sorry, I haven't used the Windows 8 Installer. This is how it worked on Windows 7.

---

### Post by Jcpayne on 2012-10-29
After accessing my bios, will it give me the option to choose which OS i boot in to?

---

### Post by BlueBinary on 2012-10-29
> **Jcpayne said:**
> After accessing my bios, will it give me the option to choose which OS i boot in to?
With my BIOS, yours may be different, If I go to Boot Options there is a hard drive option. Inside of there is a drop down menu with each partition on my Hard Drive. Sorry, It's hard for me to explain.

---

### Post by oldfred on 2012-10-29
Windows prefers either an empty drive or a preformatted NTFS primary partition with the boot flag. This is if you have a BIOS/MBR system.

If you have a new UEFI system drive is partitioned with gpt and all partitions are primary.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Windows normally installs to two partitions. One is a small hidden boot/repair of about 100MB and the main install. But if one NTFS partition has boot flag it will fully install to that. Either way make a repairCD right away.

Windows will overwrite MBR (again in BIOS systems) and you have to reinstall grub2's boot loader to the MBR. Have a current version Ubuntu liveCD or USB.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

If you have UEFI it is a lot different.

---

### Post by YannBuntu on 2012-10-30
Hello

Oldfred has provided the links you will need, but I want to add a little remark concerning the title of this thread:

- When installing Ubuntu after Windows, Ubuntu will install a bootloader that gives access to both Ubuntu and Windows.
- But when installing Windows after Ubuntu, Windows will install a bootloader that will NOT give access to Ubuntu.

So:

> Simplify Dual Boot Please

is something you should ask to Microsoft ;)

---

### Post by Jcpayne on 2012-10-30
Is there a way to take a snapshot of all your system settings in Ubuntu?

Perhaps I could just take that snapshot, then uninstall ubuntu in its entirety and install windows over top, then reinstall ubuntu and load my settings?

---

### Post by Rebelli0us on 2012-10-30
You can do better than dual-boot, you can run both OSes **simultaneously**. Open Ubuntu Software manager and type "virtualbox", install it, then install Windows as a virtual machine.

---

### Post by Jcpayne on 2012-10-30
Another question: Am I able to install windows on to entirely different harddrive, and then have my computer boot from that harddrive, but then also install the ubuntu loader into there to give me the option of which OS I boot in to?

Not sure if this made sense, let me try to clarify

I have 4 harddrives in my computer - 2 are regular disk harddrives that I use for storage, another is a solid state that I keep my OS on (which ubuntu is currently installed on), and I have another solid state that is really just being used for storage at the moment...  Could i install windows onto that storage SSD, and still somehow create the option at startup to choose my operating system?  The two boot drives will be on different harddrives (ubuntu, windows)

---

### Post by oldfred on 2012-10-30
I have 4 hard drives & a couple of flash drives. And an operating system on everyone.

I follow this logic but use Ubuntu.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

Windows often prefers to be sda. Many suggest disconnecting other drives. Both Windows & Ubuntu may install boot loader to a different drive. Windows seems to install its hidden boot partition to the drive set to boot from in BIOS or if not disconnecting be sure to first see that drive as boot hard drive. Ubuntu defaults its install of grub2's boot loader to sda, but if you use manual install you can choose. With Windows there is no choice. 

If you have a new system with UEFI it is different but also doable.

---

