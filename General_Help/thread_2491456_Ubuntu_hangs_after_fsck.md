---
title: "Ubuntu hangs after fsck"
date: 2023-10-09
forum: General Help
---

### Post by johnster001 on 2023-10-09
Good day,
I'm running Xubuntu 22.04 and recently implemented a nightly shutdown using a cron entry (shutdown -h) to save on energy usage.  Today I came down to see the system sitting at the boot screen (the one with the little spinning circle below the Xubuntu logo).  The last boot message I can see if a successful fsck of /dev/sda5.  I've tried recovery mode -> repair packages, nomodeset in Grub, and even tried "sudo apt-get install --reinstall ubuntu-desktop but so far no difference. The last change I made to the system was to add a line to fstab to automatically mount a share from my NAS, but I've disabled that line now and it made no difference.  Can anyone kindly suggest something I can try next?

---

### Post by MAFoElffen on 2023-10-09
Halt stops the system and CPU, while poweroff also sends an ACPI signal to turn off the motherboard and PSU.

Sidenote: Instead of shutdown -h, I use either
```

shutdown -P now
# OR
systemctl poweroff

```
Did you try, from the Rescue menu, "fsck"?

I'm wondering if it actually had a filesystem problem, but still needs to correct it(?) The state where is is at now, couldn't hurt.

You could check that by looking at the jounalctl before last boot, sorted reverse, filtered on systemd, last 200 lines, to see what happened
```

journalctl -b 2 -g 'systemd*' -r | head -n 200

```

---

### Post by johnster001 on 2023-10-09
> **MAFoElffen said:**
> Halt stops the system and CPU, while poweroff also sends an ACPI signal to turn off the motherboard and PSU.

Sidenote: Instead of shutdown -h, I use either
```

shutdown -P now
# OR
systemctl poweroff

```
Did you try, from the Rescue menu, "fsck"?

I'm wondering if it actually had a filesystem problem, but still needs to correct it(?) The state where is is at now, couldn't hurt.

You could check that by looking at the jounalctl before last boot, sorted reverse, filtered on systemd, last 200 lines, to see what happened
```

journalctl -b 2 -g 'systemd*' -r | head -n 200

```

Thanks for replying.

Also for the tip on shutdown, if I can get the system back up I'll revisit that.

journalctl output is mixed,

there are a ton of audit messages with Apparmor DENIED referring to dbus_signal
I did see some messages referring to ClamAV, I tried running systemctl disable clamav-daemon but no joy
I also saw a lot of errors related to cups, so I've disabled that as well, but no joy with that either
I dont see any messages with fsck in them, can I manually run the fsck on all filesystems?

*EDIT* sorry, I missed your fsck advice, I tried running it but I get an error /dev/sdc5 is mounted, cannot continue, aborting. 

Is there a way to repair the system using a Live boot USB?

---

### Post by MAFoElffen on 2023-10-10
Yes. 

Boot from the Installer LiveUSB. Use "Try". Open a browser to get back to these instructions. Open a Terminal session... Do this to see the drive names and layout:
```

lsblk -e7 -o name.label,size,fstype,type

```
Use the output of that to figure out how to form your fsck command. The format of the command is
```

sudo fsck <dev_name>

```
Example for say, if the filesystem in /dev/sda5 was linux(ext4), then 
```

sudo fsck /dev/sda5

```
If the type says lvm and it has something like "ubuntu--vg-root", then you have to activate the lvm members first, so for that you would do
```

sudo lvscan
# If LVM is there, then that is going to return output similar to this
  inactive          '[COLOR=#ff0000]/dev/ubuntu-vg/root[/COLOR]'
  inactive          '/dev/ubuntu-vg/swap_1'

```
Use that name to make it active
```

sudo lvchange -ay /dev/xubuntu-vg/root

```
The you can use fsck on it:
```

fsck /dev/ubuntu-vg/root

```
Is that enough info to get started?

---

### Post by johnster001 on 2023-10-10
> **MAFoElffen said:**
> 
Is that enough info to get started?

Yes, thank you!

I ran fsck on the home and root filesystems, both came back clean.  Also, once I booted to the recovery USB both filesystems were mounted and browsable.  Are there any next steps you would recommend?

I'm almost at the point of just reinstalling, in preparation for that, I'm trying to access my home folder while booted to the live USB stick, it's giving me an access denied.  I've run chmod 666 on the folder to give me access, and I can see the folders, but they all appear empty, so I'm guessing I dont have perms for all the subfolders and files.  I have a secondary drive installed and can access it, Is there a way to copy my home folder to that drive so I can restore those files in a fresh install?

---

### Post by MAFoElffen on 2023-10-10
Can you browse it from an Installer LiveUSB? 

You never have posted any output of your storage layout, so am in the dark on your details there. My ESP is rusty. LOL

If you posted the results of 
```

lsblk -e7 -o name,lable,size,fstype,mountpoint,model

``` 
Posted within CODE Tags, then that would fill in those blanks.

---

### Post by johnster001 on 2023-10-10
> **MAFoElffen said:**
> Can you browse it from an Installer LiveUSB? 

You never have posted any output of your storage layout, so am in the dark on your details there. My ESP is rusty. LOL

If you posted the results of 
```

lsblk -e7 -o name,lable,size,fstype,mountpoint,model

``` 
Posted within CODE Tags, then that would fill in those blanks.

I am able to browse my root and home filesystems from the Live USB so I'm guessing they are ok. I've also managed to copy my home folder to another local drive just in case.

Other things I've tried:
Boot the previous version of Ubuntu in GRUB
Successfully boot the Windows OS that is dual-booting with Ubuntu on the same drive
unplug all peripherals
uninstall a VPN package that was problematic

Here's the output of that command:

```
NAME   LABEL      SIZE FSTYPE    TYPEsda             931.5G           disk
&#9492;&#9472;sda1 Storage  931.5G ntfs      part
sdb             894.3G           disk
&#9500;&#9472;sdb1             16M           part
&#9492;&#9472;sdb2 SSD2     894.2G ntfs      part
sdc             447.1G           disk
&#9500;&#9472;sdc1            100M vfat      part
&#9500;&#9472;sdc2             16M           part
&#9500;&#9472;sdc3          219.1G BitLocker part
&#9500;&#9472;sdc4            530M ntfs      part
&#9500;&#9472;sdc5           74.5G ext4      part
&#9492;&#9472;sdc6          152.9G ext4      part
sdd              59.8G           disk
&#9500;&#9472;sdd1 ESD-USB     32G vfat      part
&#9492;&#9472;sdd2 writable  27.8G ext4      part

```

As you can see, I have multiple hard drives in this system. SDC is the main boot drive and has Windows and Ubuntu on it. There are a couple of secondary drives that are formatted in NTFS and I use those to make files available between the OS's. I'm replying to this on the same machine booted to Windows, and it looks like all the hardware is functioning normally. I'm happy to tray any suggestions you may have. Windows is working fine but I really want my Linux install to be my Daily Driver.

Thanks again.

---

### Post by MAFoElffen on 2023-10-10
Back everything up... Everything.

Go into Windows. Backup your bitlocker encryption key. After that "Suspend" bitlocker. (This will just be temporary.) -- Click Start > Type Control panel. > Open Control Panel. > Select System and Security > Bitlocker Drive Encryption > Select 'Back up your recovery key. > backup the key... Go back to BitLocker Drive Encryption > Select 'Suspend protection.' You might have to enter your security recovery key to confirm and/or Select Yes

Make sure fastboot hibernation is turned off, just in case your updates switched it back on: Click Start. > Type Control Panel > Start Control Panel > Select 'Power Options.' > Choose 'Choose what the power buttons do.' > Click on 'Change settings that are currently unavailable.' > Under 'Shutdown settings,' ensure that the 'Turn on fast startup' checkbox is unchecked.

Click Start and then select Settings. > Click Update & Security. > On the left side, click Recovery. > Under Advanced start-up, click Restart Now. > Click Troubleshoot. > Click Advanced options. > Select UEFI Firmware Settings. In our UEFI BIOS Settings > Security > Ensure 'Secure Boot' is disabled. Some Windows updates will turn this back on, preventing an (K)unbuntu installation that was installed with it turned on from booting. We just want to rule that out. (That may the whole problem there.) The reason you suspended bitlocker, is that somethings if you change this while bitlocker is active, it has the possibility of corrupting the bitlocker encrypted filesystem on that partition... Save the settings and exit. Boot to Windows...

Download the Xubuntu 22.04.3 LTS iso image and create an Installer LiveUSB. If in Windows and the target is going to be UEFI boot (like yours), I prefer using Rufus, and select GPT/UEFI only...

 After you are through, reboot on from that media. Start a browser so you can get back to the forum and these instructions: [https://ubuntuforums.org/showthread.php?t=2491460&p=14160511#post14160511](https://ubuntuforums.org/showthread.php?t=2491460&p=14160511#post14160511) 

Of course, you would substitute the nvme drivethere in those instructions to /dev/sdc5... I am assuming that is the root partition(?)

I just wrote those  those last night... If, at any point, there is an error or something doesn't work at planned, post back here. i will check this thread from time to time to see how it went.

When done testing, start Windows again and turn bitlocker back on. I know it's a 64 digit key, that is why I asked you to back up your encryption key. A fallback for that is that your key is usually attached to your MS Account you registered with (if you did that)... But the you have to copy if done or print it, then enter it manually. PITA.

Tell me how it goes. Do not hesitate to stop at any point to ask any questions.

---

### Post by johnster001 on 2023-10-13
Well, I followed all the steps, everything went well, and it still hangs at boot.  I think I'm going to reinstall and see if that clears it up.  Fortunately, this wasn't an old install and I should be able to get back up without too much trouble.  Thanks for all the help, if a reinstall doesn't fix things I'll likely post back looking for more assistance.

---

### Post by MAFoElffen on 2023-10-13
I think (if it were me), just to be sure everything is okay... I would look at the SMART logs on the NVMe to verify the disk itself is not throwing errors. That way you at least know that you aren't chasing ghosts and wasting your time installing fresh onto a bad disk.

---

