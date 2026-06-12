---
title: "Adding new HD with naming questions"
date: 2016-12-18
forum: General Help
---

### Post by cscj01 on 2016-12-18
I have Ubuntu 14.04 x64 and run a Window VM under VirtualBox.  The main reason I have the VM is because I use TurboTax for tax filing.  So, I need my data to be on something Windows can access, i.e., NTFS.  Because I keep all my data on one disk labelled "Data", that disk is formatted as NTFS.  My data has outgrown the current HD, so I have ienstalled a new HD which is much larger.  I want the new disk to be labelled "Data" when I finish coping all the data, and I want to rename the original HD labelled*"Data" after the copy. I have all my HDs defined in Fstab.  What steps do I need to go through to get this accomplished?

My thoughts are as follows:[*]
[/LIST]
[LIST=1]
[*]Format the new HD as NTFS and label it "New";
[*]Copy the data from "Data" to "New";
[*]Add an entry to Fstab for the old "Data disk with a new name;
[*]Unmount the two HDs;
[*]Rename "New" to "Data";
[*]Rename the old "Data" to whatever I called it in Fstab;
[*]remount the two drives.
[/LIST]
Where am I going wrong?

---

### Post by oldfred on 2016-12-18
Most users do not mount partitions with labels. I do use labels, but mount with UUID for those partitions I permanently mount. But labels help me keep track of partitions I only use occasionally. 

Do you want entire new drive as NTFS. NTFS also requires maintenance like chkdsk which you can only run from Windows. 
Back when I had XP with Quicken & Turbotax, I had a shared NTFS and a shared ext4 data partition as I had multiple Ubuntu installs. I keep all data normally in /home inside my data partitions and link the folders into /home. Not sure if that works with a VM.

I prefer to use rsync, but a cp -a command will also work.

You may just be able to edit fstab entry with new UUID.
Be sure to backup fstab before changes and remount to check you have no typos.

My data partition was ext4, so I had additional commands to set ownership & permissions.
    3  sudo mkdir /mnt/data
    4  sudo mount /dev/sdc4 /mnt/data

This was copying my old Linux data partition from old drive to new system and then old NTFS shared partition. Old drive temporarily mounted /media/fred.
   32  rsync -aruvlP /media/fred/Data/ /mnt/data
   33  rsync -aruvlP /media/fred/Shared/ /mnt/data

       #Edit fstab with your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup 

 sudo nano /etc/fstab 
      
 #Verify entry is ok, if no errors it is:
sudo mount -a

---

### Post by cscj01 on 2016-12-19
All went well.  I had a stale handler message for my NFS shares that I couldn't get rid of with```
sudo mount -a
```so I had to reboot.  That took care of the message.  Thanks for the suggestions.  I did use the UUID in Fstab and also used labels.  I prefer labels because it helps me see with what I'm working. with

---

