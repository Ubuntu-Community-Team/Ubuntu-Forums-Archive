---
title: "Accidently deleted Windows"
date: 2013-09-01
forum: General Help
---

### Post by evan5 on 2013-09-01
I accidentally installed Ubuntu over my pre installed Windows 8 on my new computer! I made a repair disc for my Windows 8 but now I don't know how to access my BIOS to make booting from my CD/DVD RW drive the priority! :'( Please help me.
PS-I am completely new to Linux, so please describe things as simply, and as detailed as possible.

---

### Post by evan5 on 2013-09-01
UPDATE: I was able to access BIOS finally, but telling it to boot from the CD/DVD RW drive just takes me to a page for system restore or recovery. The problem is, it says neither is possible, and when I go to Advanced Settings, all the options in there come up empty too. It says the "partition is locked" where the files it needs are. Also, Ubuntu removed any data from Drive C (the primmary)
and put it all into a partition that it created upon installation called Boot X. I'm really desperate here....I accidentally clicked the wrong area while installing this OS and now I fear that I have totally ruined my computer......

---

### Post by james40 on 2013-09-01
Hi Evan,
What are you trying to do exactly? If you over written your windows 8 installation, you wont be able to recover it with a system restore/recovery. If you are just trying to reinstall windows 8 create a windows 8 install disc/USB (if you don't have one you can download the windows 8 ISO from microsoft's website, remember to get the correct version).

---

### Post by evan5 on 2013-09-01
I am trying to get Windows 8 back, but I am unable to access my hard drive partitioning in order to create a partition for Windows 8 (if I can even re-install, seeing as it was pre-loaded, and therefore I have no activation key) Any suggestions?

---

### Post by james40 on 2013-09-01
There should be a label somewhere on your laptop with installation key. Otherwise if you still have the OEM windows 8 CD it may include the VLK used by the manufacturer. I must ask do you have any files you want to recover from you PC? As re-installing the OS will lower your ability to recover files from the drive. Are you able to delete the partition entirely?

---

### Post by QIII on 2013-09-01
The key may also be in your documentation rather than on the machine.  The little "hologram" sticker on the machine itself may not have the key printed on it.

Please note:  If you want to recover data from the machine, [I][B]stop using it.

[/B][/I]The more you use it, the less likely it will be that you will recover your data, since what you are currently doing may overwrite what has not already been overwritten.

---

### Post by Impavidus on 2013-09-01
In my experience those activation keys are usually on a sticker in the battery bay.

On the live disk you used to install Ubuntu you can find a program called gparted. It allows you to delete any partitions and create new partitions, including windows partitions. If you want to dual boot and reinstall both systems, it may be best to start preparing all partitions you need. If you need to recover data, do that first.

---

### Post by buzzingrobot on 2013-09-01
This is from distant memory, but if/when you can boot a Windows install DVD, you are given the option to delete existing partitions and create new ones.  That won't help if you want to recover data, of course.

Also, doesn't Win8 have a "recovery partition"?  Is that the "locked" partition, I wonder? Googling for a way to unlock it might turn up something useful.

---

### Post by evan5 on 2013-09-01
The Key isn't anywhere on the laptop :/ I searched for the mentioned sticker and haven't come up with anything. Since it's new, all the files I had on it I'm not worried about losing.
Win8 did come with a "recovery partition" but when I try to do a recovery it says that it I need to unlock the partition or that the partition required is missing. I've tried using the suggested Gparted, unfortunately it will only allow me to to resize/move these:
Partition      File system       Mount point       Size              Used               Unused                    Flags
/dev/sda1    fat32                /boot/efi            190.00MiB      3.07Mib           186.93MiB    
/dev/sda2    ext2                 /boot                 244.00MiB      47.49MiB        196.51        

but I can't access :
/dev/sda3    lvm2 pv           ubuntu-vg          698.21MiB      698.21MiB       0.00B                      lvm

I'm unsure as to why the third partition has almost all of the available space (I have a 750 gig hard drive) and why it's all being "used"

---

### Post by SantaFe on 2013-09-01
According to this [Windows 8 moves to bios based product keys]("http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/"), it's now embedded in the computers BIOS.  I assume you could just start the installation process as long as you still have Your Windows 8 product key, which should be in your computers documentation.

At least that's what I'm guessing, don't have Win 8 myself. ;)

---

### Post by Jonathan Precise on 2013-09-01
> **evan5 said:**
> I accidentally installed Ubuntu over my pre installed Windows 8 on my new computer! I made a repair disc for my Windows 8 but now I don't know how to access my BIOS to make booting from my CD/DVD RW drive the priority! :'( Please help me.
PS-I am completely new to Linux, so please describe things as simply, and as detailed as possible.

Try testdisk (from the ubuntu software center).

---

### Post by oldfred on 2013-09-01
It looks like you used encrypted install which uses LVM which is another logical layer of partitioning over the physical partitions.
But Windows will not be able to see any of the LVM and you need to remove it. You may need to have the standard layout or the recovery disk may recreate everything as it should.
With LVM you often need special tools as it is more advanced. But I would think gparted may let you just delete the entire thing. But all data in the LVM will be gone.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

      
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by evan5 on 2013-09-02
The problem with getting it installed again is mostly the hard drive. I can't unmount the main partition, which says it has 698.21GiB (my hard drive is 750GiB) and that ALL 698.21GiB in that drive is used (even though there is nothing in it) and that it has 0GiB of space left.

---

### Post by oldfred on 2013-09-02
If gparted will not remove the LVM, you then have to use the LVM tools. If from standard desktop you may have to install the lvm2 drivers.
sudo apt-get install lvm2

I do not know LVM, someone who does may be able to post the exact commands.
 lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)

---

