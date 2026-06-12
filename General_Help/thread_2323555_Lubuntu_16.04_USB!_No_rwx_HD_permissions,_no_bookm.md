---
title: "Lubuntu 16.04 USB! No rwx HD permissions, no bookmarks restore."
date: 2016-05-06
forum: General Help
---

### Post by Sbininit on 2016-05-06
Hey folks this is a pretty neat system but I'm fixing to delete it if I can't get this stuff working.
Its pretty aggrevating when you can't chmod to change permissions in root.
root has no power in 16.04 to do anything it seems.

I'd like Ubuntu 16.04 live to own every HD on the computer while it is booted and return permissions to normal when not booted. I'd like all video to work.

And I'm not sure what it is with bookmarks restore but it does absolutely nothing. Thats one area that has always simply worked and has never been an issue with previous linux based systems that I have used.

All I really needed was to have an updated firefox  browser in rock solid 10.04 Ubuntu and supported repositories.  I didn't need a system that doesn't work.  Also persistent doesn't seem to be working realiably. 

Thanks if anyone can help.

---

### Post by TheFu on 2016-05-06
Please clearly state EXACTLY what you are doing. It isn't clear, at least not to me.  I'd like to help and can feel your frustration.

How did you boot the system? Is it installed to a HDD?  Is the USB drive formatted with EXT4 or some other file system?  chmod doesn't work on NTFS or FAT-whatever. It also doesn't work on read-only file systems.

I've never had issues with bookmarks.
If you want "all video" to work, you cannot use Linux.  95% of videos will work, provided the correct, proprietary, codecs are available.  Due to license restrictions (which vary by region in the world), many codecs cannot be pre-installed without the user specifically requesting them. It is a legal thing.

Support for 10.04 desktop ended in 2013. Not really an option.

If all you want is a browser, perhaps full Ubuntu is not the best choice?  Check out TinyCorePlus - [http://tinycorelinux.net/](http://tinycorelinux.net/)

---

### Post by Impavidus on 2016-05-06
> **Sbininit said:**
> Hey folks this is a pretty neat system but I'm fixing to delete it if I can't get this stuff working.
Its pretty aggrevating when you can't chmod to change permissions in root.
root has no power in 16.04 to do anything it seems.Root has all powers it had before, which is, indeed, the power to do everything. If this doesn't work, then either something deep is wrong with your system (like a root partition remounted read-only after a disk I/O error) or with your understanding of the system (like you try to use chmod on a partition that doesn't support it).

> I'd like Ubuntu 16.04 live to own every HD on the computer while it is booted and return permissions to normal when not booted. I'd like all video to work.sudo should work on a live system and give you root permissions. There is no password, just hit enter if it asks for one. For videos you may have to install codecs. For license reasons not all of them are installed by default.

> All I really needed was to have an updated firefox  browser in rock solid 10.04 Ubuntu and supported repositories.  I didn't need a system that doesn't work.  Also persistent doesn't seem to be working realiably.Ubuntu 10.04 desktop has been unsupported since April 2013. Until 2015 there have been some upgrades for server, but those didn't include Firefox.

---

### Post by Sbininit on 2016-05-07
> **TheFu said:**
> Please clearly state EXACTLY what you are doing. It isn't clear, at least not to me.  I'd like to help and can feel your frustration.  How did you boot the system? Is it installed to a HDD?  Is the USB drive formatted with EXT4 or some other file system?  chmod doesn't work on NTFS or FAT-whatever. It also doesn't work on read-only file systems.  I've never had issues with bookmarks. If you want "all video" to work, you cannot use Linux.  95% of videos will work, provided the correct, proprietary, codecs are available.  Due to license restrictions (which vary by region in the world), many codecs cannot be pre-installed without the user specifically requesting them. It is a legal thing.  Support for 10.04 desktop ended in 2013. Not really an option.  If all you want is a browser, perhaps full Ubuntu is not the best choice?  Check out TinyCorePlus - [http://tinycorelinux.net/](http://tinycorelinux.net/)  16 Gig Sancruiser USB  /dev/sdc1  has  Grub2 Version 2.02 installed to the 1st vfat partition. It runs a grub.cfg that I have to make up since it does not have an installed OS.  /dev/sdc2 has a dd image of 16.04 32 bit Lubuntu on it which shows up as an iso9660 in blkid command.  /dev/sdc3 is a 12.3 gig vfat32 drive labled casper-rw.  In a nut shell I'm trying to fix my crashed 10.04 system without a DVD drive.  10.04 failed to upgrade and left the most rock solid system I've ever seen broken.  I did mange up finally install 14.04 booting an iso on HD to ram from my USB grub2 and the screen fuzzes up and bookmarks will not load my backed up favorites. I can save new ones, I just can't use my backed up ones.

---

### Post by Sbininit on 2016-05-07
> **Impavidus said:**
> Root has all powers it had before, which is, indeed, the power to do everything. If this doesn't work, then either something deep is wrong with your system (like a root partition remounted read-only after a disk I/O error) or with your understanding of the system (like you try to use chmod on a partition that doesn't support it).  sudo should work on a live system and give you root permissions. There is no password, just hit enter if it asks for one. For videos you may have to install codecs. For license reasons not all of them are installed by default.  Ubuntu 10.04 desktop has been unsupported since April 2013. Until 2015 there have been some upgrades for server, but those didn't include Firefox.  I'm trying to replace my 10.04 OS on my Desktop without a DVD drive working.  10.04 ran for over 4 years without fail on my HD install  as my main OS with XP and a slew of other linux distros until I tried to do an upgrade to get a new version of firefox which left the OS crippled when upgrade failed.  I was tired of getting the ole your browser is unsupported and may not work with this page message.    My DVD drive is not working so I finally got a copy of 14.04.iso booted from HD by booting with my Grub2 USB.  Because I could not edit grub.cfg or 40_custom on 10.04 and run grub2-update I had to use my USB Grub2 to boot the iso. My control key has quit also and at the time I didnt' know that F10 would boot and edited menu.     I still have the remnants of 10.04 on sda4  that boots half way and leaves me with a shell that says try init = something command. Cant' remember.  I almost recovered 10.04 after the upgrade failure. My min, max, close buttons were gone and while trying to get them back I lost gnome desktop. While trying to get it back I further broke the system to where I don't even have  root shell now.    The 14.04 64bit install on sda7  is fuzzing up the screen every few minutes until I hit the Alt key and wiggle a page with the mouse.  That is actually what I'm trying to fix as my main Desktop OS and grub2 handler. 14.04 also does not load backed up bookmarks.

---

### Post by TheFu on 2016-05-07
> **Sbininit said:**
> 16 Gig Sancruiser USB  /dev/sdc1  has  Grub2 Version 2.02 installed to the 1st vfat partition. It runs a grub.cfg that I have to make up since it does not have an installed OS.  /dev/sdc2 has a dd image of 16.04 32 bit Lubuntu on it which shows up as an iso9660 in blkid command.  /dev/sdc3 is a 12.3 gig vfat32 drive labled casper-rw.  In a nut shell I'm trying to fix my crashed 10.04 system without a DVD drive.  10.04 failed to upgrade and left the most rock solid system I've ever seen broken.  I did mange up finally install 14.04 booting an iso on HD to ram from my USB grub2 and the screen fuzzes up and bookmarks will not load my backed up favorites. I can save new ones, I just can't use my backed up ones.

I liked 10.04 best too. ;(  But when support for the OS ended, I moved on.  Ran "10.04 Servers" for almost the full 5-yrs of support - my email server was the last to make the change --> 12.04 --> 14.04, which happened quickly (the same day).  Xubuntu is similar to that release.  There's always Mint too.

ISO file systems are read only. You cannot change permissions on those files.

The best way to install any Linux is from a flash drive.  I haven't tried it with 16.04, but with every Ubuntu from 10.04-14.04 I've just used dd to shove the ISO file onto a flash drive, then booted that for the installation process.  Try 

```
sudo dd if=/path/to/ubuntu-16.04.iso of=/dev/sdc bs=1M
```
Then boot off the flash drive.  That command assumes that sdc is the flash drive.  If it isn't and you run it, everything, all partitions, everything on sdc will be gone. Be careful.

I mostly use virtual machines, so don't get much experience on my own equipment with installations, but at my LUG, we install onto member systems almost every week.  Most people like to have multi-boot setups and use yumi [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/) to make those on a flash drive.  1 guy had 15 different Linux distros (installers) on a single flash drive. Some support "live boot" ... but these are all ISO files, so they are read-only too.  I have a USB2 flash drive with 5 or 7 different distros, created by yumi. It is my "save-my-butt" flash disk.   Not all flash drives can be booted from all USB ports.  I've had issues with USB3 flash drives working as boot devices on chromebooks, even when inserted into USB2 ports.  USB2 flash drives don't always work either with every system, so have a few spares to test with. There are incompatibilities between USB chips inside different computers and some versions of USB flash drives.  I've never found a consistent rule - not all from vender A will fail to work.  Just to be clear, this is just about booting, they usually work fine for reading/writing as normal data storage, regardless.

As to your bookmarks - that is a browser thing, right?  Firefox has a bookmarks file. Let me look for it. You can also "export" the bookmarks.  Then on the new system, "import" the bookmarks.  I use them all the time, but only by the awesome-bar method, not looking through a list.  
Found it ... ~/.mozilla/firefox/{insert-your-random-profile-name}.default/bookmarks.html  ... that's the file you need to move around.

Is there a reason you don't just install the OS onto a 20G partition on a real HDD?  Did I miss that completely?  USB will always be slower than a real HDD. I can understand playing around with a USB version, but you've already made the switch.

---

### Post by Sbininit on 2016-05-07
> **TheFu said:**
> I liked 10.04 best too. ;(  But when support for the OS ended, I moved on.  Ran "10.04 Servers" for almost the full 5-yrs of support - my email server was the last to make the change --> 12.04 --> 14.04, which happened quickly (the same day).  Xubuntu is similar to that release.  There's always Mint too.  ISO file systems are read only. You cannot change permissions on those files.  The best way to install any Linux is from a flash drive.  I haven't tried it with 16.04, but with every Ubuntu from 10.04-14.04 I've just used dd to shove the ISO file onto a flash drive, then booted that for the installation process.  Try   ```
sudo dd if=/path/to/ubuntu-16.04.iso of=/dev/sdc bs=1M
``` Then boot off the flash drive.  That command assumes that sdc is the flash drive.  If it isn't and you run it, everything, all partitions, everything on sdc will be gone. Be careful.  I mostly use virtual machines, so don't get much experience on my own equipment with installations, but at my LUG, we install onto member systems almost every week.  Most people like to have multi-boot setups and use yumi [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/) to make those on a flash drive.  1 guy had 15 different Linux distros (installers) on a single flash drive. Some support "live boot" ... but these are all ISO files, so they are read-only too.  I have a USB2 flash drive with 5 or 7 different distros, created by yumi. It is my "save-my-butt" flash disk.   Not all flash drives can be booted from all USB ports.  I've had issues with USB3 flash drives working as boot devices on chromebooks, even when inserted into USB2 ports.  USB2 flash drives don't always work either with every system, so have a few spares to test with. There are incompatibilities between USB chips inside different computers and some versions of USB flash drives.  I've never found a consistent rule - not all from vender A will fail to work.  Just to be clear, this is just about booting, they usually work fine for reading/writing as normal data storage, regardless.  As to your bookmarks - that is a browser thing, right?  Firefox has a bookmarks file. Let me look for it. You can also "export" the bookmarks.  Then on the new system, "import" the bookmarks.  I use them all the time, but only by the awesome-bar method, not looking through a list.   Found it ... ~/.mozilla/firefox/{insert-your-random-profile-name}.default/bookmarks.html  ... that's the file you need to move around.  Is there a reason you don't just install the OS onto a 20G partition on a real HDD?  Did I miss that completely?  USB will always be slower than a real HDD. I can understand playing around with a USB version, but you've already made the switch.    I actually have installed 14.04 on to HD as my main OS and grub2 updater and its only issues are fuzzy screen occasionally and "no" bookmarks restore backup. The screen thing, I can't deal with, I have to find a solution for that as well whether it be a boot command or install another OS. That's 64 bit! The 32 bit that I have on my USB runs beautifully except I can't change permissions on many of the 13 hard drives and OS's that I have booting unless I had already done chmod 777 -R before booting the live 16.04. In other words the live USB would not make much of a rescue tool as it is now.

---

### Post by Sbininit on 2016-05-09
For some reason the screan kept fuzzing out on my 14.04 install, so I downloaded 16.04amd464.iso  and finally got the iso booting toram and installed it in place of my 10.04.
It runs beautifully. 
There are things that I miss though that are so ingrained in me, things that didn't need fixing.
1 desktop button Ever get tired of minimizing 10 pages so you can find one page on the desktop? 
2. terminal windows missing all the goodies like open new tab preferances and so on. I know you can get them at the top of the page but thats a tad far. 
3. ever single time I type sudo I have to type in my password
4 The launcher on the side would be nice on the bottom Im still stuck with a small screen like was sold before the wide ones came out.

In spite of it all, all of linux developers deserve a humongous thank  you for their efforts.

P.S. I'm not updating anymore without a backup. Thanks!

---

