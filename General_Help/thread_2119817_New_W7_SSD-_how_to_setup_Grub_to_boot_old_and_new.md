---
title: "New W7 SSD- how to setup Grub to boot old and new?"
date: 2013-02-24
forum: General Help
---

### Post by jb0nez on 2013-02-24
Hi All,
My hard drive is failing, I have one on the way to clone this one too, but that's a side issue.
I also just got a 256GB M4 SSD. I set it up (unplugging all hard drives first) with Windows 7 since that's where I do 90% of my work.

I'd like to put Grub on it, and have the option to boot my new W7 install, my old W7 install, and my old Kubuntu 12.10 install. Right now I can change my boot device in BIOS and boot off my old hard drive and get my familiar boot menu -- ubuntu, advanced ubuntu (some older kernels), and windows. Running Kubuntu this way seems fine, haven't tried windows, don't think it will be as forgiving.
I want new Windows (on /dev/sda1) to be my default OS if no key is pressed at Grub menu.
When I run boot-repair and just get info and look at boot options ([http://paste.ubuntu.com/5563640/](http://paste.ubuntu.com/5563640/)), the best it wants to do is "This setting would reinstall the grub2 of sdb5 into the MBRs of all disks (except USB without OS)." Fair enough but does that mean sdb5 will need to be present to boot? I'm expecting a new hard drive soon and will be changing things around, but the constant will be the SSD with W7. If I let boot-repair reinstall grub2 to all disks, will my system then stop booting if sdb5 is unailable? Or will it just install Grub onto sda in such a way I can ONLY boot to my old hard drive's Kubuntu/W7 partition? 
For example I made a change to my grub menu to make /dev/sda5 my default boot (Windows) on the old hard drive - will grub try and do that (and fail at boot time). And what menu entry would I change to make /dev/sda1 the default boot choice?
I've run boot-repair from a live USB and it was similar output, but that's an option if necessary.
Thank!

---

### Post by jb0nez on 2013-02-24
Well I muddled through and got them all booting off of Grub on /dev/sda. But I did confirm the problem  - if my main hard drive is offline (as will soon be the case according to SMART, new one on its way) then Grub on my SSD /dev/sda will NOT load. I just get a black screen. I imagine I could use a Linux live USB with boot-repair and fix it, but is it really necessary to have another drive in the system ( a hard drive no less) to boot Grub on an SSD with only Windows on it? How do I get all of Grub's menu/config info onto just the SSD?

---

### Post by dcstar on 2013-02-24
> **jb0nez said:**
> Well I muddled through and got them all booting off of Grub on /dev/sda. But I did confirm the problem  - if my main hard drive is offline (as will soon be the case according to SMART, new one on its way) then Grub on my SSD /dev/sda will NOT load. I just get a black screen. I imagine I could use a Linux live USB with boot-repair and fix it, but is it really necessary to have another drive in the system ( a hard drive no less) to boot Grub on an SSD with only Windows on it? How do I get all of Grub's menu/config info onto just the SSD?

Grub is part of your Linux installation, it will not function unless the Linux system is functional.

Shrink your Windows partition on the SSD and install fresh Linux or copy the existing Linux partition to it using **gparted**. There are detailed instructions on these tasks already in the forums and on the 'net.

---

### Post by jb0nez on 2013-02-25
But the whole point is that my entire SSD is a Windows partition, and I intend to keep it that way as like I said 90% of my work is done there and the 256g I have to work with is barely enough, certainily not enough to fit the Linux install from 1.5TB HD.

Do I really need to have Linux on installed on sda to boot a linux install on sdb? As I mentioned grub works fine on sda to load W7 from sda, and linux or Win7.

---

### Post by dcstar on 2013-02-25
> **jb0nez said:**
> But the whole point is that my entire SSD is a Windows partition, and I intend to keep it that way as like I said 90% of my work is done there and the 256g I have to work with is barely enough, certainily not enough to fit the Linux install from 1.5TB HD.

Do I really need to have Linux on installed on sda to boot a linux install on sdb? As I mentioned grub works fine on sda to load W7 from sda, and linux or Win7.

You said you were getting a new disk, so Linux has to be **somewhere** for Grub to work.

If you want to change where the Grub boot loader is:

```
sudo dpkg-reconfigure grub-pc
```

---

### Post by oldfred on 2013-02-25
To do a full install of Ubuntu you only need 10 to 25GB and keep data on your rotating drive. Most data is only accessed occasionally so hard drive speed is not a major issue.

You can install all of grub without Ubuntu either to a grub2 only partition or even inside the NTFS Windows boot partition. 

You can have grub2 in the SSD's MBR with grub's files in the Windows /boot partition. You just have to make sure during install that grub and Windows BCD use the same /Boot. In Linux /boot and /Boot are two different folders and in Windows case does not matter and Windows will not work wtih two /boot folders. I did this with a Windows repair flash drive by installing Windows repair ISO then installing grub and chainloading back to the same partition grub and Windows was in. Windows boots from PBR or partition boot sector.

Anther way is to have a small grub2 only boot partition. You can either boot with grub in MBR to grub files in grub partition or install grub to PBR and move boot flag to grub partition to still use grub files in grub partition. Then with grub.cfg you add the chain load entry back to Windows.
       [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)
    
Any install of grub2 without Ubuntu has none of the auto configuration files nor os-prober. You have to create and manually maintain your own grub.cfg.

Somewhat similar install to flash and use Winodows in MBR & grub in PBR of another partition.
[http://ubuntuforums.org/showthread.php?t=2119881](http://ubuntuforums.org/showthread.php?t=2119881)

---

### Post by jb0nez on 2013-02-26
I did a dkpg-reconfigure, grub is now setup perfect - except that since it's pulling its boot.img (I think that's what boot-repair said was the filename) from /dev/sdb5, if I pull my HD out I ca no longer boot off the SSD (yeah when the HD does crash I'll be able to fix my MBR with windows repair). I see no way to change that in the boot-repair program, it just says it will be pulled from /dev/sdb5.

I think I need to do what you were talking about where I get Grub2's config installed onto the 100mb system reserved partition; that way it can the HD can be absent and my system will boot or it can be present and I'll then be able to boot into old windows or ubuntu. That description went way over my head though, I'm a pretty much grub newbie.

The other think I might do is restore my windows MBR and just use the BIOS to boot off my hard drive if I need my old Windows programs or to use ubuntu.

---

### Post by oldfred on 2013-02-26
Then I would suggest to keep Ubuntu live installer with Boot-Repair and a Windows RepairCD handy. Then you can update or restore which ever boot loader you want. 

Boot-Repair will install a Windows work alike boot loader to the MBR of a Windows drive to boot Windows, but cannot run chkdsk. If Windows has corruption you may need to run chkdsk, if you cannot get into repair console, so Windows repairCD is worth having.

         Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

