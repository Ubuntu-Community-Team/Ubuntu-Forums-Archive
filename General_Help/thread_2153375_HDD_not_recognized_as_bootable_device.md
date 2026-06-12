---
title: "HDD not recognized as bootable device"
date: 2013-06-10
forum: General Help
---

### Post by ttcpl on 2013-06-10
Hi,
First timer here. Not completely sure this belongs here but I could not decide.

THE PROBLEM
Ubunutu 10.04 lts  64 bit server does not boot with error  "Gave up waiting for root device"

THE BACKGROUND
This is a VM running on Xenserver 6.1
It was originally running on  xenserver 5.6 but it (together with 5 other vms)  was moved to a 6.1 server. The 5.6 server is still available for a day or two.
I don't know when was the last time this vm was successfuly run. Must be 1+ years. So this could have been a problem on the old server.
There is another 10.04 lts vm with the exact same problem and background. This second machine is non critical.
All other VMs (non ubuntu) work properly on the new 6.1 server.


WHAT I HAVE DONE SO FAR (I have done a lot more but much of it was fumbling around)
I. Boot using live CD  (I have used 10.04 and 12.xx desktop with the same results). 
Ia. I can see the file system, directories, root folder, etc.

II. Used boot-repair utility
IIa. Boot repair can see the partition, root, etc and save grub to the drive
IIb. Still does not fix the problem. Reading the pastebin it complains somewhere about a partition called SR not being inside the disk. But still says the machine is ok to be rebooted.
IIc. [http://paste.ubuntu.com/5753075/](http://paste.ubuntu.com/5753075/)
IId. Before using boot-repair I used the 10.04 server install disk to do the same (repair grub) with the exact same results.

III. Installed a second disk and put 10.04 lts on it while leaving the original drive in.
IIIa. Machine boots fine. Can see the original disk files, etc.
IIIb. Remove new drive and boot. Get "Could not find device xxxx" errro (obviously looking for the new drive)
IIIc. Put back the new drive. Machine boots to new drive no problem. 
IIId. Run boot-repair from live CD. It can see both installs. Change default root to the original drive's root and use the option to put grub on all disks. Machine does not boot with the same "gave up waiting for root" error.
IIIe. [http://paste.ubuntu.com/5753231/](http://paste.ubuntu.com/5753231/)


IV. Removed new drive, increased size of original drive and run boot-repair again
IVa. Same results.
IVb. [http://paste.ubuntu.com/5753267/](http://paste.ubuntu.com/5753267/)



WHAT I WANT TO ACCOMPLISH.
This machine has a custom version of SugarCRM installed. We tried reproducing this install manually on a new VM and lots of stuff doesn't work. 
So the value of this machine is in that as far as we know this custom SugarCRM install works. But the stupid thing does not boot..... :-(
I will consider extracting the files onto another drive but having failed (after many hours) to get the SugarCRM install reproduced on another VM I am leaving that as the very last option.
I much rather get this machine to boot.

I greatly appreciate any forthcoming help.

---

### Post by ttcpl on 2013-06-10
SOLVED
Turns out that whilst the NON ubuntu VMs had been created using "Another Install Media" the two ubuntu machines were created using the 10.04 template in xenserver 5.6.
For some reason we could not get the 5.6 server to see the new storage server when doing the migration, so we moved the Server HDD as second repository on the new server. This only gave us the option of moving the virtual drives and not the VM with all its glorious settings. So we manually created the machines using "other install media". Worked for all the others but not the ubuntu machines.

In the end we:
I put back the HDD in the old server
II detached the drives from the vms
III exported the vms to USB (no disk = very small export)
IV imported machines to new server
V re-attached the disks

voila the ubuntu machines boot!!!


**tl,dr  It was the bios string settings in the vm that were wrong. Copied from old xenserver via usb stick and all is good now**

---

### Post by ttcpl on 2013-06-10
BTW... in case you were wondering the machine had not been booted for one year and 360 days!

---

