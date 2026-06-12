---
title: "Failed boot on Ubuntu 22.04.4"
date: 2024-02-20
forum: General Help
---

### Post by robert48 on 2024-02-20
Running fine for years then:-
"Failure: File system check of the root filesystem failed
The root system on /dev/sda1 requires a manual fsck"
How do I do that please?

---

### Post by oldfred on 2024-02-20
Is drive old?
Do you have good backups?
You may want to also check drive's status with smartmontools

[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

o see all the ext4 partitions, using live installer, may change drive from sda to sdb, check before running fsck.
Partition must be unmounted:
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p3
sudo e2fsck -f -y -v /dev/nvme0n1p3

---

### Post by robert48 on 2024-02-21
Thanks oldfred, the SSD that the system is on is old and I have ordered a new one. I always keep Home on a separate drive and then have a third drive for Backups. This should have protected all the data. I'll refresh the install usb with the latest version and then have a go with your commands as suggested. Failing that, I think I'll try putting in a new drive and installing the system on to it. From memory, I need to be careful and specify Home as the existing Home SSD when installing. I'll let you know when I surface next! Many thanks again, good to see you are still around!

---

### Post by robert48 on 2024-02-21
Back up and running! This is what worked for me. Much will depend upon the state of your system drive if you follow this. I consider myself lucky.

Plug in an 8GB or bigger USB memory stick into any working computer.
Go to Ubuntu.com and download the latest LTS (long term support) onto your USB stick. In my case this was ubuntu-22.04.3-desktop-amd64.iso. 

To turn your download file into a bootable USB drive use the 'StartUp Disk Creator' application. It is found on any Ubuntu system, search for it in 'Show Applications' using the bottom left grid icon.
Open StartUp Disk Creator and provide the 'Source disc image (.iso)' file by navigating to the where you downloaded it to.
Then select 'Disk to use:' This will show in the list provided the USB stick is attached to your working computer.
Then click on 'Make Startup Disk' button.
Make a refreshing drink while it does it stuff.

It is now your Ubuntu USB Start Up - Live Installer stick.
Make sure the PC/laptop that will not boot is turned off.
Put the USB Start Up stick into the computer that failed to boot.
Then turn on the machine and interrupt the start-up by entering the BIOS. In my case, with an ASUS motherboard, I had a flash screen informing me to press del to enter the BIOS screen.
Once you have the BIOS screen up, look for the USB stick and make it the first boot device, then save and exit.
Your computer will start up using the system on the USB stick. Choose the 'Try Ubuntu' option and a default Ubuntu 'Desktop' will come up.

Now you can access some tools. Open 'Show Applications' from the bottom left grid icon.
Search for 'Disks' and open the application.
It will show you your HDD and/or SSD drive(s). Using the left menu click on a drive and it will show you the state of the drive. In my case I had one failed sector showing, which normally is not too serious but if that sector has anything to do with booting up then you end up with my issue.
Fortunately, there is a settings icon, the gear wheel, that helps. Click on it and you can analyse the selected drive. It will ask you if you want to repair the drive. Read the caveat displayed and if you want to proceed (data might be at risk!) then click on the 'repair' option.
You will get a report hopefully informing the disk is repaired. If so turn off the computer using the top right menu, remove the USB stick when prompted, confirm and hey presto your machine will boot up as normal. You'll feel lucky!

If the drive cannot be repaired using the above process then you will need to dig deeper and follow oldfred's advice above. Thank you oldfred.

Thanks to all at Ubuntu too. The 'Ubuntu USB Start Up - Live Installer' is a brilliant tool!

---

