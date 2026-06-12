---
title: "I have 13.10 installed w persistence on a 4gb flash drive. Can I update it?"
date: 2014-01-18
forum: General Help
---

### Post by Advait on 2014-01-18
Hi All,

I have 13.10 desktop ubuntu ( ubuntu-13.10-desktop-i386.iso ) installed w about 700mb persistence on a 4gb flash drive. Can I update it? I want to know if its OK to update 13.10? Or will updating the OS and apps on a flash drive create problems? If its not possible to update 13.10 on a flash drive then I'll consider installing 13.10 on an external USB hard drive.

Does updating 13.10 require the presence of an MBR, boot partition and swap partition? Does a flash drive have those?

I did a google search and ubuntu forums search and didn't find anything relevant.

Thanks!

Advait

---

### Post by maestrobwh1 on 2014-01-18
Um, you can BUT it will probably max out your storage file.  I'd selectively update things like your browser but would not bother with other packages unless you observe they have a bug.  You can install synaptic package manager because in my opinion, it is the most intuitive graphical manager out there and you can list packages alphabetically and then find things like "firefox."

I WOULD NOT update all, you will run out of space, perhaps before the update even finishes.

Also, when done, open a terminal and do a 

```
sudo apt-get clean && sudo apt-get autoremove
```

This will remove the package files that downloaded for the update and any packages that are no longer needed.  It will recover *some* of the space.  Keep in mind that unlike a traditional install, every update goes into your personal storage file as an overlay; it does not actually replace the files on the system.  It can't.  So if the upgrade says "this will take an additional 678 kb, this is for where it replaces files in the system but again, it actually goes into your overlay and it will really take approximately DOUBLE the size of the downloaded package.  So if firefox is 10MB to download, it will possibly take 15-20 MB of your personal storage space, even after you do a sudo apt-get clean.

You need a more space if you want to accomplish a more extensive upgrade but you can't do this using the USB tool in Ubuntu because it requires FAT and with FAT32, you can't exceed a 4 GB storage file.  FAT sucks this way.

For what you are doing, IF you have a larger USB sitting around, you could **_use a live CD or USB other than your one with persistence_** and use dd to copy the 4 GB one to the larger one AND THIS IS TOTALLY NON DESTRUCTIVE TO YOUR CURRENT USB SETUP:

[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)

This will take a while (like 15-45 minutes, so just go walk away, you will know when it is done when you get the prompt back in terminal) then remove BOTH drives, and reinsert the new larger one, remove the casper-rw file on the NEW one then use gparted (install it if it is not installed in the live CD, obviously the internet needs to be working) to size the FAT partition to the minimum allowed.  In the remaining space, create a ext2 (ext3 is horribly slow on flash media; you could try ext4?) and label the partition casper-rw (lowercase!).  

Reinsert your original drive (now is time to copy files from your personal storage file to the casper-rw partition

Open terminal:
```
df
```

this lists the disks

find the mount point of your disks, it might be by uuid, so your smaller one will probably show up like /media/abcd-wxyz (they will be letters and numbers mixed up actually)
the new one will have two partitions, but you are only concerned about the ext2 casper-rw partition

terminal again

```
sudo mkdir /mnt/loop
sudo mount -t ext2 -o loop /media/abcd-wxyz /mnt/loop
```

note, abcd-wxyz should be replaced by whatever the disk shows up under "df"  Observe lower and upper case!

```
sudo cp -rp /mnt/loop/* /media/casper-rw
```

Now, when that is all done, you should have a bootable new drive, that uses the casper-rw partition and it will have all the files from your original persistence file from your previous disk.

AGAIN, I would not totally do a full on upgrade unless I was using a 16 GB disk and some things like your kernel and things depending on it WILL NOT UPGRADE.  It would also just take forever to upgrade.  USB is notoriously slow writing unless you are using one of the newer drives that have write speeds of 30 M/s

Keep in mind that in April, Ubuntu 14.04 LTS will be coming out.

---

