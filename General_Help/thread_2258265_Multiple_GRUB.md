---
title: "Multiple GRUB"
date: 2014-12-26
forum: General Help
---

### Post by Jonners59 on 2014-12-26
I seem to have more than one hard drive with Grub installed.  Not a major issue in terms of the PC working, but it makes for a lot of uncertainty when making changes and an untidy installation to boot.  I would therefore like to remove one of the GRUB installs and make sure the remaining one works before shutting down.


1 is installed on /sda and the other /sdb

```
sudo dd bs=512 count=1 if=/dev/sda 2>/dev/null | strings
```

Shows GRUB installed on both and I know from gparted both hard drives are set as boot

I assume I need to turn off boot on sda, some how delete GRUB on sda and then somehow check/reinstall GRUB on sdb. Can anyone please tell me how to go about this?

---

### Post by hal8000b on 2014-12-26
> **Jonners59 said:**
> I seem to have more than one hard drive with Grub installed.  Not a major issue in terms of the PC working, but it makes for a lot of uncertainty when making changes and an untidy installation to boot.  I would therefore like to remove one of the GRUB installs and make sure the remaining one works before shutting down.


1 is installed on /sda and the other /sdb

```
sudo dd bs=512 count=1 if=/dev/sda 2>/dev/null | strings
```

Shows GRUB installed on both and I know from gparted both hard drives are set as boot

I assume I need to turn off boot on sda, some how delete GRUB on sda and then somehow check/reinstall GRUB on sdb. Can anyone please tell me how to go about this?

[COLOR=#ff0000]WARNING:  DANGER![/COLOR]

Never use that command as it will not only erase grub but also the partition table! You will end up with no OS at all!

I have grub on 2 drives, its a good thing really as if one is messed up you change the boot order in BIOS and boot from the other drive.
If you really want to remove grub then the first 446 bytes ONLY should be erased

```
sudo dd if=/dev/zero of=/dev/sdx bs=446 count=1
```
Replace sdx with correct sda or sdb and make sure you are booting from correct drive in BIOS

You cant tell if grub works before shutting down, so only way is to change drive boot order in BIOS and boot from
each grub system in turn, hope that helps.

---

### Post by yancek on 2014-12-26
Is Xubuntu the only operating system or do you have multiple systems?  If you have multiple systems, you will have the /boot/grub directory in each and they take up very little space.  If you only have Xubuntu, you would first need to ascertain which drive (sda or sdb) and make sure that the drive with Xubuntu has its Grub in the master boot record and is bootable.  I'm not sure why you think having two Grubs installed is a problem unless you only have one OS.

---

### Post by oldfred on 2014-12-26
Grub can easily be installed from one install to all MBR's.
       sudo grub-install /dev/sda
sudo grub-install /dev/sdb
etc

But if you have multiple installs often better to have a different grub in every MBR. Having grub in second drive should only be seen if BIOS cannot boot first drive and if you cannot boot first drive then you may want second drive to boot. BIOS controls drive boot order.

Also grub does remember which drive's MBR to reinstall to on major updates. You may need to reset that also with every install. 
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

If you need to change drive:
      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

I have multiple installs and just to keep track of them I use bootinfoscript and/or Boot-Repairs summary report which also uses bootinfoscript as the first part of its report.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Jonners59 on 2014-12-27
Ok, so basically, don't be a plonker... Leave it alone, is what you are all saying!

How do I know which one is being used, then for the system updates, because that may not be the one used by the BIOS at boot.  Certainly changes I make to the grub appearance using grub customizer do not take effect.

---

### Post by oldfred on 2014-12-27
See previous post. That shows which drive grub will reinstall into, and how to reset it if desired.

I actually run bootinfoscript as part of my rsync backup, so I always have a current copy of which drive has which boot loader and entire boot configuration.

This user has made a few fixes to standard boot info script.
 [https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript) 

      
 Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)

---

### Post by Jonners59 on 2014-12-29
Thanks Guys...  I didn't get a chance to look in to your suggestions, the PC has now failed all together, just after GRUB.  Maybe you can help.

The reason I was looking in to the GRUB scenario was on the back of another issue I have on this machine, covered in another thread and a BUG report, namely that I can't shut it down.  It can through the reboot process, but the shutdown stops short of complete closure.  I was asked in the BUG to replace the kernel, which I have no idea how to do and all the instructions look far to complicated.  I also have a Sky DVB card that has proprietary drivers that I had trouble installing, but for some reason stopped working about 4 days ago.  You are asking, so what?  The DVB is dependent on the kernel, so that is two items faulty that are kernel dependent, and before I started to look deeper in to the kernel change, I wanted to tidy up the GRUB, hence I was worried about having two, so 3 things dependent upon the kernel, and now the error I am getting is something like.." trouble syncing kernel..  rebooting in 30 seconds...".

So any ideas...?

PS:  Thanks again "oldFred"  I remember this script for a couple of years or so back when i had some GRUB issues.  Worked well then.

---

### Post by oldfred on 2014-12-29
I know with video drivers you have to run the initrd updates to update kernel. As long as installed from repository the updates are run automatically, but if externally installed you have to manually update with every kernel update.

  man mkinitramfs
sudo update-initramfs -u 
or
sudo update-initramfs -k all -c

---

### Post by Jonners59 on 2014-12-30
Thanks OldFred
What I am going to do is try and restore by using demo CD and then running the kernel update, I think this is correct...

```
cd /tmp/
[FONT=Verdana]wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc2-vivid/linux-headers-3.19.0-031900rc2-generic_3.19.0-031900rc2.201412290135_amd64.deb
[/FONT][FONT=Verdana]wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc2-vivid/linux-headers-3.19.0-031900rc2_3.19.0-031900rc2.201412290135_all.deb
[/FONT][FONT=Verdana]wget [/FONT][FONT=Verdana]http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.19-rc2-vivid/linux-image-3.19.0-031900rc2-generic_3.19.0-031900rc2.201412290135_amd64.deb
[/FONT][FONT=Verdana]sudo dpkg -i linux-headers-3.19.0-*.deb linux-image-3.19.0-*.deb[/FONT]
```

[FONT=Verdana]Then do a grub update 
[/FONT]```
sudo update-grub
```[FONT=Verdana]

Then run [/FONT]```
[COLOR=#000000][FONT=Verdana]sudo update-initramfs -k all -c[/FONT][/COLOR]
```[FONT=Verdana]

Then ```
sudo shutdown -h now
```[/FONT][FONT=Verdana]

Then fingers crossed it will boot up...[/FONT]

---

### Post by oldfred on 2014-12-30
I have never installed new kernel.
Good luck.
Is not the 3.19 kernel very new? Like still being tested?

---

### Post by Jonners59 on 2014-12-30
Its not the "dailey" I was told to steer clear of, anyway, too late, managed to get the pc up and now at last throws of install of new kernel...

---

### Post by Jonners59 on 2014-12-31
OK, all done!  Delayed getting back as I had resolution problems.  Had the "Default" only option in the Desktop displays, and none of the solutions I could find worked.  Still not 100% happy with the resolution fix, but it is at the correct level for now.  The problem was that I had nomodeset and acpi=off in GRUB, removed them and it would at least boot to a reasonable resolution.

Now I have sync issues with Netflix, Skype, etc.  I am wondering if it has something to do with the HDMI lead settings and
I also have an issue that the DVB card has lost its drivers, which is a pig to fix...

---

### Post by oldfred on 2014-12-31
At least some progress. :)
Good Luck & Happy New Year.

---

### Post by Jonners59 on 2014-12-31
Thanks OLdFred
Yes, plenty...  still probs with these last two bits, but inching my way forward.

Happy New Year

I am going to close this thread as no real action was taken....

---

