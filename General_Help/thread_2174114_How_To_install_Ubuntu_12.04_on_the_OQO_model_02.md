---
title: "How To: install Ubuntu 12.04 on the OQO model 02"
date: 2013-09-12
forum: General Help
---

### Post by maestrobwh1 on 2013-09-12
No Ubuntu past 10.10 boots via USB stick or USB cd on this machine.  That being said, I wrote this how to  for Precise 12.04 because when I was selling one of these machines on eBay with Precise on it, I was bombarded with people asking how I did it.  If you do not have a docking station, you have to find ubuntu 10.10 and make a bootable USB stick and then boot with the xforcevesa nomodeset flags: After the install, add the items /etc/default/grub below, minus the hda_intel items, and use the xorg.conf below from the get go. then follow the second post at [http://ubuntuforums.org/showthread.php?t=2172074&p=12778288#post12778288](http://ubuntuforums.org/showthread.php?t=2172074&p=12778288#post12778288) in order to upgrade it to 12.04.  Don't install ANY extra packages during the process.  Keep booting the 2.6.35 kernel with each upgrade so that you can use wifi for internet.  Actually, after you boot your first install of Maverick, remove linux-image-generic and linux-headers-generic so that the upgrade process listed there will not install newer kernels at all.  They do not work on this machine.

Wifi and sound will not work with the precise kernel so you will need to connect the dock to ethernet

You can boot the Ubuntu 12.04 CD in a docking station using boot flags, but wifi will not work:  ```
nomodeset xforcevesa via_agp.blacklist=yes via.blacklist=yes pcspkr.blacklist=yes pcspkr.blacklist=yes snd_hda_codec.blacklist=yes snd_hda_intel.blacklist=yes psmouse.proto=bare 
```  The psmouse reference keeps the mouse from going wild and unusable.  The hda_intel blacklisting prevents the boot from locking up bc the kernel does not recognize the sound card properly, and streams an error about this module infinitely and one one has to hold the power button in to stop the machine.   

If you can't get it to boot, try the mini.iso for 12.04 to get the system installed that way using ethernet.

After the install, before rebooting, mount the disk in terminal the old fashioned manual way to some mount point 
i.e. assuming you installed it on the first partition on the internal drive

```
sudo mkdir -p /mnt/sda1
sudo mount -t ext4 /dev/sda1 /mnt/sda1 
```

and make these changes **to the installed filesystem.** i.e. preface all paths with /mnt/sda1 if that was your mount point

to /etc/default/grub before "quiet splash"
```
nomodeset xforcevesa via_agp.blacklist=yes via.blacklist=yes pcspkr.blacklist=yes snd_hda_codec.blacklist=yes snd_hda_intel.blacklist=yes psmouse.proto=baree
```

If you plan on [COLOR="#FF0000"]chrooting [/COLOR]into the system below and NOT reboot until you are done, then omit snd_hda_codec.blacklist=yes snd_hda_intel.blacklist=yes

I'd actually add the above to the kernel entry in /boot/grub.grub.cfg  I know the file screams at you not to edit it, but if you are connected via ethernet cable and can copy paste the above, and know what you are doing, your boot will go better.  You'll even get a splash if you add vga=785 (deprecated but it works and well, honestly, this how to is not exactly idea modding, but it works.

Add to /etc/modprobe.d/blacklist.conf
```
# oqo model 02
blacklist via
blacklist via_agp
blacklist pcspkr
```

These might be redundant, but my system is rock stable.  

My /etc/X11/xorg.conf:

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "openchrome"
	Option 		"VBEModes" "true"
   	Option 		"EnableAGPDMA" "true"
	Option          "AccelMethod" "EXA"
	Option 		"MigrationHeuristic" "greedy"
	Option 		"SWCursor" "true"
EndSection

Section "DRI"
	Group 0
	Mode	0666
EndSection

Section "Extensions"
    	Option 		"Composite" "Enable"
EndSection
```

Open your favorite editor:

```
sudo gedit /etc/apt/suorces.list.d/maverick.list 
```

paste these in

```
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ maverick main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ maverick-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ maverick-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick main universe restricted multiverse
deb http://old-releases.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
```

You could reboot, or my preference would be to[COLOR="#FF0000"] chroot [/COLOR]to do the next steps, assuming the ethernet was still attached (or working usb wifi dongle), then install the Maverick kernel to get the internal wifi and sound card working so...

If you rebooted, modify  /etc/default/grub before "quiet splash" by DELETING the
```
snd_hda_codec.blacklist=yes snd_hda_intel.blacklist=yes
``` 

```
sudo apt-get update && sudo apt-get install linux-image-2.6.35-32-generic linux-headers-2.6.35-32-generic
```

Then either delete the maverick.list or comment out all the lines with a #

REBOOT with that kernel then

REMOVE linux-image-generic, linux-headers-generic, and any linux-image-3.x and those headers... they are useless if you want sound/wifi.  YOU DO NOT WANT THE KERNEL TO UPGRADE.

You should be good for a few years.  Don't be tempted to go to 13.04 or 13.10.  I got the 13.04 iso file to boot from my internal drive... The desktop was slow and unusable.

---

