---
title: "exFAT USB drive not mounted"
date: 2024-07-01
forum: General Help
---

### Post by ngong on 2024-07-01
Just installed *Ubuntu 24.04* on a new computer.

An *exFAT* 4TByte *Sandisk* "*G40*" SSD USB drive is not recognized by my Ubuntu installation.
Neither if I start it connected, nor if I plug it in after boot has finished.

The *G40* is recognized on the USB port of another *Win10* computer without problems. Even checking the drive with Win10 file explorer leads to "no errors". Hence, I assume there is nothing wrong with *G40*.
Plugging the drive into an USB 3 port leads to this lines when running sudo dmesg:[INDENT][114178.524051] usb 1-1: new full-speed USB device number 6 using xhci_hcd
[114178.685207] usb 1-1: New USB device found, idVendor=4791, idProduct=2066, bcdDevice= 0.00
[114178.685225] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[114178.685230] usb 1-1: Product: PRO G40
[114178.685234] usb 1-1: Manufacturer: SanDisk
[114178.685237] usb 1-1: SerialNumber: 03010A00A1080000B6B0400AB80E0500
[/INDENT]

I expected to see it mounted somewhere below **/media**, as with another 4TB *Sandisk* "*Extreme*" SSD. However that one is formatted to *ext4* instead of *exFAT*.

Running **lsusb** shows the *G40* as[INDENT]Bus 001 Device 006: ID 4791:2066 SanDisk PRO G40
[/INDENT]

**lsblk** does not show a name for the G40, as it does with Extreme,  I expected something like[INDENT]sdx            8:0    0   3.6T  0 disk 
&#9492;&#9472;sdx1         8:1    0   3.6T  0 part /media/rsc/<some uuid>
[/INDENT]

The command[INDENT]**sudo dmesg | grep -e "sd[a-z][1-9]**
[/INDENT]

shows just the *sda1* drive for the *Extreme*, but nothing for *G40*.

What to do next to find the cause why *G40* is not mounted automatically?
Is it possible to assign it manually to drive entry like /dev/sdb1?

---

### Post by oldfred on 2024-07-01
I prefer to label all partitions, particularly those I may only mount occasionally, so default mount is by label, not UUID.
I understand a label, but have no idea which UUID is which. 

Did you use exFAT with Windows?
Windows sets fast startup or hibernation flag on all Windows partitions. That prevents default mount to prevent loss of data. If you write into a hibernated system, the data is lost when hibernation restored.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)

Also while exFAT slightly better than FAT32, it still is not recommended for larger file systems.
The standard exFAT implementation is not journaled and only uses a single file allocation table and free space map. 
But exFAT will store larger files than FAT32. But still should not be used for larger partitions as chkdsk may take forever. 
You can only run repairs from Windows and exFAT does not support Linux ownership & permissions.

you can see lots of details of your partitions:
lsblk -fmp | grep -v snap

---

### Post by srwk2j42 on 2024-11-10
Did you find the solution ?
[beginner here]
This worked for me:

1 install **exfat-fuse**
[[https://pimylifeup.com/ubuntu-exfat/]](https://pimylifeup.com/ubuntu-exfat/])

2 in terminal: 
 check enter: **mount -l **
[usually the last entry is your external drive, notice the starting part with '**/dev/___** ',for example I will use this from now :'/dev/sdc1']
[you can also use sudo fdisk -l alternative just in case if device doesnt show up]

3 command: **umount /media/<your drive> **   
[I usually use tab to autocomplete the /media path]

4 command: **sudo mount.exfat-fuse /dev/sdc1 /mnt/drive1/ **   
[ sudo mount.exfat-fuse -d /dev/sdc1 /mnt/drive1/     if you want to keep terminal intact with file transfer process]

Now I have access to file under /mnt/drive1/ folder path.
5 to unmount : step1: **sudo umount /mnt/drive1**  | step2: the external drive will appear in files system, eject from there to safely remove.

other resources: just in case you get some error: [https://stackoverflow.com/questions/16002539/fuse-error-transport-endpoint-is-not-connected](https://stackoverflow.com/questions/16002539/fuse-error-transport-endpoint-is-not-connected)
............................

I will be glad if you can share your alternative solution . 

Also, for source-ubuntu to target-exfat, can someone guide me to improve file transfer speed, [note formatting is no option]

---

