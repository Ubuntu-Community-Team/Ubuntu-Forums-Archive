---
title: "Bootable Ubuntu external hdd, how?"
date: 2021-03-30
forum: General Help
---

### Post by susan2021 on 2021-03-30
In the good old days of the bios, I've installed Ubuntu in any number of ways w/o any problem. It was simple as long as you weren't too drunk to misidentify where you were installing to. I've installed it to USB sticks, external USB HDDrives (that I could plug into a Windows computer and boot my external drive from), created dual boots (Ubuntu partition encrypted with native Linux encryption and the Windows partition encrypted with TC or VC), as well as installing /boot to a USB stick for added security. With my more recent laptop, with its UEFI replacement for the bios, I am far less certain. I ended up dumping Windows that came with my new laptop and just installed Ubuntu. That wasn't any real loss. 

Can I plug in an old external HDD with a bios version of Ubuntu into my UEFI computer and mount and run it without buggering something up? How would that be done?

What I'd really like to do is create a new external HDD with a "clean" copy of 20.04 (the version I'm running on my laptop now) that I can mount as my ultra secure Ubuntu - i.e., that hasn't been used for any gratuitous surfing, link clicking, installation of programs or browser extensions - and that I can use for sensitive financial work. 

Can someone point me to a definitive tutorial on how I can create an external, bootable Ubuntu HDD drive, using my current Ubuntu laptop, that isn't going to bind that external drive and my laptop into a dual boot? It doesn't even really need to mount from another computer just as long as I can plug it in to my current laptop and press "esc, esc, esc" and get to the option to mount it over the internal SSD and it doesn't get tied to my laptop to where I have to have it plugged in just to run my internal SSD.

Thanks.

---

### Post by dragonfly41 on 2021-03-30
Based on what you have specified I would aim for an external SSD .. not HDD.

Crucial examples here .. [https://uk.crucial.com/products/ssd/portable-ssds](https://uk.crucial.com/products/ssd/portable-ssds)

and to create a custom ISO (stripped back) use Cubic in your laptop Ubuntu to create your custom ISO to install in external SSD.

I now avoid laptops (too tricky to repair internals) and my Dell PC has two external SSD's in a docking bay with its own power supply.

You could apply that to your laptop if you don't need to lug around a dual docking bay.

In fact the StarTech dual docking bay I use can take old HDD's too with the appropriate container (IcyDock).

Just an added note .. ensure that you create an EFI partition (FAT, 500mb) in each SSD so that it can be independently booted without relying on laptop EFI. I use rEFInd in there with custom GUI.

---

### Post by Paddy Landau on 2021-03-30
> **susan2021 said:**
> Can I plug in an old external HDD with a bios version of Ubuntu into my UEFI computer and mount and run it without b******** something up?
If you just plug in the device, it's only data unless you do something with it. Only if you try to boot with it will something happen.

However, if I understand you correctly, you want to reformat the external HDD with a bootable Ubuntu installation completely independent of your laptop (so, you should be able to boot it from any UEFI computer).

I have done such a thing more than once, and it's reasonably easy but it has a few tricky bits. It would be like having a dual boot. When it's not plugged in, your computer will just boot as usual. But when it's plugged in, depending on how you set your laptop's BIOS, one of the following will happen:

[LIST]
[*]The laptop boots straight into your external device.
[*]The laptop asks you which device to boot into.
[*]You have to press a key (maybe F10 or Delete, or something else depending on your laptop's BIOS) to tell the laptop which device to boot into.
[/LIST]
> **susan2021 said:**
> How would that be done?
**Warning**

Any installation runs a (small) risk of unexpected data corruption. Therefore, **run your full backups** before proceeding.

**Set up your HDD**

[LIST=1]
[*]Plug in your external HDD, but don't mount it. If your system mounts external devices automatically, you'll have to unmount it.
[*]Format your HDD as follows. My preferred tool is GParted, but you can use Disks or some other app if you prefer, or even the command line if that's your thing.
 **Warning: This will erase your HDD**, so take a backup first if you have important data on it.
Also, when you use GParted, Disks, command line or whatever, **be certain to correctly chose which drive you are playing with**, otherwise you'll erase your laptop's drive!
[LIST]
[*]Create a new device partition table on the external HDD as [FONT=courier new]gpt[/FONT] (not as [FONT=courier new]msdos[/FONT]). This will *immediately* erase your HDD.
[*]Create a new partition, size 512MiB (the exact size isn't important, as long as it's about 512 MiB). I recommend that you name the partition *EFI System Partition*.
[*]Create a second partition, size 700MiB (the exact size isn't important, as long as it's at least 700MiB). I recommend that you name the partition *Boot*.
[*]Create a third partition to fill the rest of the drive. If you prefer to reserve space for something else, that's fine; in that case, create the partition with a minimum size of 20GiB. Name the partition whatever you want; say, *Susan*.
[*]Don't bother formatting any of these partitions.
[/LIST]
[/LIST]
**Set up for installation**

[LIST=1]
[*]Create a Live USB with Ubuntu.
[*]Plug in both the Live USB and your external HDD.
[*]Reboot your laptop into the Live USB (not your external HDD).
[*]Choose to install Ubuntu.
[*]Go through the installation, following the process that I describe below.
[/LIST]
**Installation process**

[LIST=1]
[*]When asked between erasing your drive or doing something else, choose "Something else."
[*]Where it says, "Device for bootloader installation", choose your external HDD. This prevents it from mucking about with your laptop's boot process. Note that you choose the device, *not* the partition. So, if your device is /dev/sdb, that's what you choose; you don't choose /dev/sdb1.
[*]Select your **laptop's** EFI partition (probably something like /dev/nvme0n1p1, but double check) and then "Change…"
[LIST]
[*]Select "Use as: do not use this partition"
[/LIST]

[*]Select your **HDD's** new EFI partition (probably /dev/sdb1, but double check) and then "Change…"
[LIST]
[*]Select "Use as: EFI System Partition"
[/LIST]

[*]Select your **HDD's** new Boot partition (probably /dev/sdb2, but double check) and then "Change…"
[LIST]
[*]Select "Use as: Ext4 journaling file system"
[*]Tick "Format the partition"
[*]Select "Mount point: /boot"
[/LIST]

[*]Select your **HDD's** new data partition (probably /dev/sdb3, but double check) and then "Change…"
[LIST]
[*]Select "Use as: Ext4 journaling file system"
[*]Tick "Format the partition"
[*]Select "Mount point: /"
[/LIST]

[*]If you think that you might have made a mistake, go through steps 2–6 again, or even Quit and try again.
[*]Double check step 2 — it's easy to forget.
[/LIST]
Then you can install.

Once complete, reboot.
Remove your Live USB when prompted.
Boot into your external HDD using whatever method your BIOS uses (as described above) to check that your HDD works.
Reboot again, but this time remove your external HDD to check that your laptop still works correctly.

Have fun!

---

### Post by yancek on 2021-03-30
One problem you need to consider is that the Ubuntu Ubiquity installer will by default install the EFI files to the first EFI partition it finds so that in your case that would overwrite the EFI files for your current Ubuntu on the laptop.  Do you want to do an EFI install on the external drive?  If that is the case, the safest solution would be to remove the internal hard drive which is problematic with a laptop.  Disabling it in the BIOS firmware would be the 2nd option if possible.  Another possibility is to  use GParted to Manage Flags and remove the efi and boot flags from the internal drive, create an EFI partition on the external drive  and set the boot and efi flags on the EFI partition of the external drive.

---

### Post by susan2021 on 2021-03-30
Thank you for your reply.

Aye and thanks.

You say to format my (external) HDD with GParted but conclude by saying,  "Don't bother formatting any of these partitions" which has me a bit  confused.

It would seem to me that step 3 of "Installation  Process" is the crucial step in avoiding having the external HDD  married to the internal SSD.

Thanks for the reply. It would be nice if I could somehow disable the internal drive. When I first started researching this subject a couple of years ago, when I got this new laptop, that was one of the things that was mentioned. What is your opinion of Paddy's procedure?

---

### Post by dragonfly41 on 2021-03-30
Not sure who you are replying to.  One approach I have used is to open laptop and physically (carefully) remove internal drive.
Then plug in LiveUSB  and external HDD/SSD and where I differ from Paddy's procedure is that I do use GParted in LiveUSB to format partitions in advance of installation. Of course with only external drive(s) plugged in through USB port, the located drive is now /dev/sda instead of /dev/sdb. I favour using rEFInd installed in the external drive but that is your choice.  After you get Ubuntu working you need to shut down replace the internal drive and reinstall Grub/rEFInd in external drive since /dev/sda now drops to /dev/sdb.  A reinstall of Grub/rEFInd fixes that wrong addressing of drives.  If rEFInd is installed (usually from LiveUSB instance) it asks where you want to install and you select the only drive plugged in at that time (other than LiveUSB).

---

### Post by susan2021 on 2021-03-30
I was replying to you and thanks for your reply. Sacré bleu! I might as well go to Wally World and just get a cheap laptop for my ends.

---

### Post by DuckHook on 2021-03-30
Firstly, welcome to the forums, susan2021

From a technical perspective, the advice already given is excellent and I have nothing more to add.

From a "meta" perspective, perhaps the following observation: I gather that your ultimate objective is to have a reliably secure OS that is "untainted" by other apps or activities like general surfing.

Rather than go to the trouble of creating an external boot SSD (please don't misunderstand—that is also a good solution), why not strictly segregate your activities within your existing OS while keeping it as pristine as it was at first install?

Many of us achieve this by doing all of our surfing in browsers that are jailed within VMs or containers. The same strategy can be extended to most apps so that they too run inside highly secure sandboxes. Your banking/financial work can be confined to a VM/container used only for sensitive stuff. Encrypt the entire VM/container for added privacy.

This is a more versatile/convenient strategy than an external drive (though it lacks portability).

Not trying to confuse you, but just another option I thought you may wish to consider.

---

### Post by oldfred on 2021-03-30
The selection of location of grub bootloader on install partition screen only works with BIOS installs.
Ubiquity installer only installs to first drive's ESP - efi system partition.
As Paddy mentions, you must partition in advance and include an ESP on external drive. And it should be gpt partitioned.
Best then to do a work around to get grub to directly install to external drive's ESP, but it can be repaired afterwards, only if you have ESP on external drive.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive.

---

### Post by dragonfly41 on 2021-03-30
> **DuckHook said:**
> I gather that your ultimate objective is to have a reliably secure OS that is "untainted" by other apps or activities like general surfing.
.

Another cocktail .. [dedicated Raspberry Pi]("https://ubuntu.com/raspberry-pi")

...

[Later thought]  .. Why not just a simple Ubuntu LiveUSB on flash SansDisk .. but configured to be *persistent *to hold KeePass etc with passwords?

---

### Post by susan2021 on 2021-03-30
Yes, that (a virtual machine) was something I was also considering and looking into prior to posting this thread. I played around with Virtual Box on a now departed desktop's HDD years ago and I'm familiar enough with it. Thank you for your reply and suggestion.

Thank you Oldfred for this additional information.

> **dragonfly41 said:**
> Another cocktail .. [dedicated Raspberry Pi]("https://ubuntu.com/raspberry-pi")

...

[Later thought]  .. Why not just a simple Ubuntu LiveUSB on flash SansDisk .. but configured to be *persistent *to hold KeePass etc with passwords?

I'll have to look into that. I'm vaguely familiar with hearing about such things. I seem to remember doing a TOR browser install on a thumb drive with persistent memory.

> **oldfred said:**
> 
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.

Incidentally, when I first got this laptop a couple of years ago, I tried to find a way to disable the first SSD drive via the UEFI settings but there was no obvious way that I could see. I still have an old functional bios based laptop with an uber-secure external HDD installation of Ubuntu that I created to work with it. I suspect that the Ubuntu version on that external drive is so old that it won't update via the internet anymore so I'll just have to manually update/re-install a later version of Ubuntu on it. I might go that route.

---

### Post by C.S.Cameron on 2021-03-30
I have put together a step by step for installing Ubuntu to External Drive. The method creates a USB HDD, SSD or Flash drive that boots BIOS or UEFI, see: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step)

---

