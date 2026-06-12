---
title: "How to manually partition drive for Lubuntu install?"
date: 2020-09-15
forum: General Help
---

### Post by ihavenoname123 on 2020-09-15
Soo I just installed Lubuntu on a HP Stream 14 following these steps..

"Select ‘New Partition Table’ and ‘Master Boot Record’. Click ‘OK’  Click on the Free Space entry, then click on Create.  Change the following parameters: Size: 512 MiB; File System: fat32; Mount Point: /boot/efi; Flags: boot esp. Click ‘OK’  Click on the Free Space entry, then click on Create.  Subtract 4096 from the size value (for a 4GiB swap) and replace the existing value with that result. Change the following parameters: Mount Point: /; Flags: root. Click ‘OK’  Click on the Free Space entry, the click on Create.  Change the following parameters: File System: linuxswap; Flags: swap. Click ‘OK’"

Is this correct? It seems to be working OK..but still I'd like to know what someone with more experience doing this thinks. Manually partitioning the drive was the only option I had when installing. I read somewhere to unmount the drive and then try...but was still only given the option to manually partition.

The computer has 4g of ram and 25g hard drive..also what does apply full upgrade do? Does Lubuntu update itself or should I be manually updating it? Thanks

---

### Post by CelticWarrior on 2020-09-15
Clearly a UEFI system so GPT instead of MBR is preferable. There's really no point in using MBR unless installing Windows in Legacy mode. But yes, it works for Linux.
Also a swap partition is no longer needed because Ubuntu uses swapfile by default now.

---

### Post by Enigma12 on 2020-09-15
I am a big believer in good partitioning of hard drive(s). But how I configure the size of any partition is my choice, based on the size(s) of the hard drive(s) and personal preference. There is really NO one ideal way to partition. What works for me may not appeal to anyone else. It's a choice situation for each of us. 

First, if your hard drive is actually only 25GB in size, as you stated, why even bother partitioning something that small? I've never partitioned any hard drive smaller than 80GB, and one of my recently retired computers had a 40GB sda, which I left unpartitioned for my / and /home. That computer also had a 300GB hard drive that I made into two roughly equal partitions for storing files. That 40GB drive has worked as / and /home for at least 4 installations, leaving the other two partitions unaffected. But, as I said, how anyone partitions is a personal choice. 

FWIW, I prefer using Gparted, which I installed onto a CD to do partitioning. The only thing that I've done with the Parted that comes with a distro is wipe down a / and /home when I replaced or upgraded a distro. Again, that's my choice. 

If you are loading any recent distro, you may not benefit from even having a Swap partition, especially if you only have 25GB to store everything. With 4GB RAM, you can only do a few things at any one time anyway, unless that is in a 32-bit computer. My recently retired 32-bit computers only had 2GB of RAM, and I didn't have any swap partition or any problem running out of RAM, but I also always knew that I simply couldn't run too many things at one time. 

Full upgrade to me means replacing the operating system with the next version, rather than an incremental upgrade, e.g., going from 18.04 to 20.04. I could be wrong about that, though.

---

### Post by guiverc on 2020-09-15
You haven't mentioned (or I missed it if it was there), which Lubuntu you're talking about.

Lubuntu has 3 installers still supported for 2 releases and 2 desktops. Lubuntu 18.04 LTS using the LXDE desktop offers `ubiquity` by default & *di* (debian installer) as it's alternate install option. Modern Lubuntu 20.04 LTS uses `calamares` installer. 

There are differences between the releases, so I see the release as critical (inc. how they use *swap* by default). Both will use *swapfiles* however, so with only 25GB disk I'd not create a *swap* partition at all, and just use swapfile.

If using the *live* installer (only option on 20.04), you can partition first using "KDE Partition Manager" on 20.04, or `gparted` on 18.04, which personally I find easier. Then I use the "*something-else*" option of 18.04, or "*Manual Partitioning*" on 20.04 to select prepared partitions and install.

Note: If you install and use Lubuntu 18.04 LTS, you'll need to fresh install when *release-upgrade* time comes due to change in desktop & significant changes. Refer release notes for later release for specific details.  But provide your release would allow more specific response.

---

### Post by Impavidus on 2020-09-16
> **Enigma12 said:**
> I am a big believer in good partitioning of hard drive(s). But how I configure the size of any partition is my choice, based on the size(s) of the hard drive(s) and personal preference. There is really NO one ideal way to partition. What works for me may not appeal to anyone else. It's a choice situation for each of us.
I agree with that, but there are some inaccuracies in the rest of that post.

Best to use GPT partitioning these days (not MBR), in particular on UEFI systems. On a non-UEFI system you don't need an EFI partition. In most cases the installer will propose to do something automatically, but it may not if the installer doesn't see a sensible way to do this. An upgrade during installation means that the installer doesn't use the versions of the packages present on the live disk, but the latest versions from the repositories, if the package has been updated after release of the live disk.

---

### Post by ihavenoname123 on 2020-09-16
HP Stream - 14-cb011wm is the model with Lubuntu 20.04 (LXQT) installed..specs are 32gb emmc hard drive and 4gb ram. How do I know if my system is UEFI? I am understanding to use GPT and not to make a swap because it is done automatically? Also, manually partitioning was the only way to proceed with the install. Thanks for you responses!

---

### Post by CelticWarrior on 2020-09-16
Almost all computers of this decade are UEFI. BIOS is a relic of the past, from 1981 to be precise.

Yes, GPT always and no need for a swap partition.

---

### Post by Impavidus on 2020-09-16
You can access the bios or uefi settings by hitting some key when you switch on your computer. On my somewhat older HP laptop it's delete. If it supports uefi (and it most likely does), you can set it to either uefi mode or legacy mode, which emulates bios. Uefi mode is more modern and has some advantages, in particular when dual booting, but that's not something you do. Generally, uefi mode is preferred, but some early devices (and HP was notorious) made booting Linux in uefi mode needlessly complicated by not following standards. It's your choice. The mode you use to boot your live disk is the mode in which you install. I actually use legacy mode on my laptop. It works.

You don't need a swap partition. The installer will make a swap file automatically, which is easy to resize. But if you prefer, you can make a swap partition anyway and the installer will configure your system to use that and no swap file.

---

### Post by ihavenoname123 on 2020-09-16
Appreciate it..saved this little computer

---

