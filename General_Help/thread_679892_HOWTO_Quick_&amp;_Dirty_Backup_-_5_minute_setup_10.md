---
title: "HOWTO: Quick &amp; Dirty Backup - 5 minute setup 100% guaranteed. (2 Steps, No Fuss)."
date: 2008-01-27
forum: General Help
---

### Post by SilverWave on 2008-01-27
_________________________________________

**HOWTO:**

**A Simple Backup Solution based on grsync (or the command line rsync).**
Keeping It Simple - The 5 minute setup time will protect 90% of what you value (/home).

Two commands allow you to verify that it worked independently of the backup application.
The advanced section shows how to save Synaptic Markings and sources.list
(this enables you to update a newly rebuilt machine with the same packages and source lists as your old machine).

Partly based on: [http://ubuntuforums.org/showthread.php?p=4205911](http://ubuntuforums.org/showthread.php?p=4205911) and [http://ubuntuforums.org/showthread.php?p=3795689](http://ubuntuforums.org/showthread.php?p=3795689)

OS: Ubuntu 7.10
Architecture: 64bit.
Backup media USB external hard drive formatted to ext3
Tested using grsync on my own machine. The full rebuild and restore was tested on a Ubuntu VM.
_________________________________________

**Plan A: Quick & Dirty Backup - 5 minute setup.**

**1 -** Issue these commands:
sudo apt-get install grsync

**2 -** Copy your /home directory to /media/medion1/dr/gusty/home using sudo grsync
(Basic options: preserve time, owner, permissions, group. Advanced options: Copy symlinks as symlinks )
or

sudo rsync -r -t -p -o -g -v --progress -l /home /media/medion1/dr/gusty/home 

Note: Replace /media/medion1/dr/gusty/home with your backup directory.


Done :)

Cheers
_________________________________________


**Plan B: Bullet Proof Backup - 100% Guaranteed.**

(Warning - sudo -i gives you root access, if you are not comfortable with this level of access, or do not know what I am talking about, do not follow this section).

**1 -** Create md5sum's for each file in /home (save the list to check.md5).

Issue these commands:
sudo -i
cd /home
find . -type f 2>/dev/null -exec md5sum {} \; >check.md5

(after noting the error information close this terminal down).

**2 -** Copy your /home directory to /media/medion1/dr/gusty/home using sudo grsync
(Basic options: preserve time, owner, permissions, group. Advanced options: Copy symlinks as symlinks).
or

sudo rsync -r -t -p -o -g -v --progress -l /home /media/medion1/dr/gusty/home

**3 -** Confirm files in target directory against check.md5 (output to results.md5)
Issue these commands:
sudo -i
cd /media/medion1/dr/gusty/home
md5sum -c check.md5 > results.md5

(after noting the error information close this terminal down).

**Restoring**
If you need to restore a file you can copy it from your backup directory.
If you have had a serious problem and have lost all of /home then you would need to restore all files from your backup directory using grsnyc as detailed below.

***Warning be very careful that you don't overwrite the wrong files ;)**

**1 -** Restoring
Copy your /media/medion1/dr/gusty/home directory to  /home using sudo grsync 
(Basic options: preserve time, owner, permissions, group. Advanced options: Copy symlinks as symlinks).
 or

sudo rsync -r -t -p -o -g -v --progress -l /media/medion1/dr/gusty/home /home


Note: Replace /media/medion1/dr/gusty/home with your backup directory.
_________________________________________




**Advanced Section - how to save Synaptic Markings and sources.list.**

This enables you to update a newly rebuilt machine with the same packages and source lists of your old machine.

Backup

**1 -** Backup Synaptic Markings.
Synaptic > File > Save markings and check Save full state, not just changes.
save to /home/YOU/save_markings_full_state

**2 -** Backup apt information keys, 3rd party repositories and sources.list
Copy your /etc directory to /media/medion1/dr/gusty/etc using sudo grsync
(Basic options: preserve time, owner, permissions, group. Advanced options: Copy symlinks as symlinks).
or

sudo rsync -r -t -p -o -g -v --progress -l /etc /media/medion1/dr/gusty/etc

Note: Replace /media/medion1/dr/gusty/etc with your backup directory.

**3 -** Now do the 3 steps detailed here > "Plan B: Bullet Proof Backup - 100% Guaranteed."
_________________________________________




**Plan C: Disaster Recovery - How to rebuild from scratch.**
_________________________________________

Resources:

Rescue CD1 -> Ubuntu Live CD
Boots off the CD to a full Ubuntu OS - Connects you to the web so you can trouble shoot any problems. Allows you to reinstall and repartition if needed.

Rescue CD2 -> Super Grub Disk
You can restore Grub on your MBR automatically.

Your Backup directory and files.
_________________________________________


Restoring.

***This is assuming you have lost everything except the backup drive and that the new machine can be wiped!**

**1 -** First boot the live cd and install Ubuntu.
After Ubuntu has installed and rebooted to the HD, set up the restricted drivers for your graphics card if applicable, there is no need to reboot yet. 

**2 -** Replace the existing sources list with the one from your lost system.
 Now copy your /media/medion1/dr/gusty/etc/apt directory to the new system using sudo grsync 
(Basic options: preserve time, owner, permissions, group. Advanced options: Copy symlinks as symlinks).
 or

sudo rsync -r -t -p -o -g -v --progress -l /media/medion1/dr/gusty/etc/apt /etc/apt
sudo apt-get update

**3 -** Import Synaptic Markings from file.
Synaptic > File > Read markings > /media/medion1/dr/gusty/home/YOU/save_markings_full_state

**4 -** Copy your /media/medion1/dr/gusty/home directory to /home using sudo grsync
(Basic options: preserve time, owner, permissions, group. Advanced options: Copy symlinks as symlinks).
or

sudo rsync -r -t -p -o -g -v --progress -l /media/medion1/dr/gusty/home /home

**5 -** Log off and back on to see your restored desktop and settings. 


Best of Luck :)
_________________________________________

---

### Post by K.Mandla on 2008-01-30
Moved to General Help.

---

