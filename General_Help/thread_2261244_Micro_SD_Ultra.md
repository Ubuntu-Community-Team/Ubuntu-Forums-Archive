---
title: "Micro SD Ultra"
date: 2015-01-17
forum: General Help
---

### Post by old_dog on 2015-01-17
Formatted micro Ultra SD in Windows(hiss boo) in Ubuntu 14.04 extracted RPIB+ start files onto it.
Fired up RPI ok some slight oddities, saw there was a later version of NOOBS available.
Re-formatted sd in windows and while I was there extracted NOOBS to it.
RPI wouldn't boot
Tried to look at SD in Ubuntu can't see it............... Put a different SD in Ubuntu could see that OK

NB. Windows and Ubuntu  use the same reader Dual boot m/c

Windows could see it, my Nexus can see what is on it as well.
Ubuntu can't, Canon Camera can't and I'm guessing as RPI didn't boot it can't 

Don't make sense to me any clues anybody???

---

### Post by ajgreeny on 2015-01-17
Can you see it in the output of **sudo fdisk -l** in Ubuntu?  That assumes you are not formatting it to a gpt partition, as fdisk will not read that properly.

I have not used Windows for some time but I'm aware that it can do strange things to partitions in some situations; I don't know what those situations are, unfortunately, but I suggest that you format the partitions that you need for NOOBS, whatever that is, using gparted in Ubuntu; it has never let me down and is my choice of partitioner now that I use Xubuntu.

---

### Post by DuckHook on 2015-01-17
SDCards are weird. They are weirdly formatted with a translation layer between what is presented to OSes and what is actually written to the physical card. It's a DRM thing imposed by the entertainment cartel, so this time it's not MS's fault so much as the RIAA/MPCA thought police.

What *is* MS's fault is that Windows will format bigger SDCards in *exfat*. *Exfat* is proprietary to MS and Linux doesn't read *exfat* unless you install a module that taints the kernel. Ergo, it is not a part of most regular installs. To install *exfat*, do:```
sudo apt-get update && sudo apt-get install exfat-fuse exfat-utils
```**NOTE** The Linux *exfat* module does not give you kernel-level access. It uses FUSE, so be aware of its limitations. Also, *gparted* will not work with *exfat*, so again, must use caution. If monkeying with *exfat* in Linux (i.e. formatting), must use *exfat-utils* extensions. You will need to refer to its *man* pages for details.

Of course, if you reformat the whole card to *EXT2* or simple *FAT32*, this would work too and make your life much simpler, but don't use the Windows formatter to do this, as it will default to *exfat* (for larger capacity cards).

*Exfat* may not even be the problem here (aforementioned DRM garbage could be), but without further info it is hard to tell.

---

### Post by old_dog on 2015-01-18
Thanks guys .......... Once you know the problem it is easy to solve
Cheers Old Dog

---

### Post by efflandt on 2015-01-18
Not sure how NOOBS works (never tried it but supposed to be easier for people not familiar with dd, or similar), but in the past for the regular RPI Debian image you simply used dd (or suitable equivalent in Windows) to write it directly to beginning of SD in my case, or microSD for newer models. Then the first time you boot it on the Raspberry Pi it offers to expand the partition to fill the SD/midroSD (or you can use gparted in Ubuntu to expand the Linux partition that is after the FAT32 partition with config files).

---

### Post by DuckHook on 2015-01-18
Just a few further observations. If you are using this for RPi, exfat won't work even if you download the modules to format properly . Reason: RPi kernel does not have exfat baked in and therefore cannot bootstrap. Therefore, you must use either Fat32, or one of the EXTs. You can use EXT4 if you turn off journaling, but EXT4 has no advantage over the simpler EXT2 on external flash media. Since SDcards and USB sticks write to the chip through their own firmware, the enhancements and better efficiencies of EXT4 get lost in translation.

If formatting for RPi use, you really don't care about interchangeability, so EXT is far superior to Fat32. Max file size of Fat32 is 4GB vs 16+GB for EXT. EXT is relatively immune to fragmentation whereas FAT32 is notorious for it, though this is not a concern in flash drives. EXT is also demonstrably more robust to all manifestations of FAT which are brittle file structures due to overreliance on its primitive allocation table.

Last but not least, if you want to reformat the sdcard so that your Canon camera can see it, then you must use a special formatting tool from the SD Association which only runs in Windows or OS-X and available for download [here]("https://www.sdcard.org/downloads/formatter_4/"). This special formatter writes a special partition on the card that allows DRM to work. You will then need to have your *Canon camera* (yes, seriously) complete the installation of the actual file system. This will write the DRM crippleware back into the DRM partition, after which, purposefully DRM-crippled appliances like your camera will be permitted once again to see the card. If your camera cannot format (some of the cheaper models lack this function), you will have to use a friend's device. Most SLRs have this capability. Your Nexus doesn't care either way and is built to read both standard formats and DRM-crippled ones.

Unless you are repositioning the card for non-RPi use, you don't need to go through this nonsense. Just repartition the damn thing using a clean app like gparted, install EXT2 on it, and you will be flying.

Good luck and Happy Ubuntuing... or Raspianning!

---

