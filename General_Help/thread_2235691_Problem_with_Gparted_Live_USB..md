---
title: "Problem with Gparted Live USB."
date: 2014-07-22
forum: General Help
---

### Post by Bobby_James on 2014-07-22
My current partitions are depicted in the attachment.

I want to reduce the size of the Windows 8 ntfs partition in sda4 and increase the size of the Ubuntu ext3 partition in sda5.

I used Unetbootin to install Gparted.iso on to a USB.

However, the problem is that when I boot into Gparted, the sda4 partition does not show the 'used' or 'unused' sizes. Instead, both show '-----'. It is thus impossible to reduce the size of sda4. The flag for sda4 is 'msfdata'.

Also, there is an exclamation mark in a triangle by the partition column of sda4.

How can I - whether with Gparted or not - reduce my Windows partition and increase my Ubuntu partition?

Please note that I have never re-sized partitions before so do not be too technical. (Yes, I have backed up!)

Thanks!

---

### Post by sudodus on 2014-07-22
It is recommended to ***resize Windows partitions with Windows tools***. So do it from within Windows, but do not create partitions with Windows. (Leave unallocated space. Avoid dynamic partitions, because they cannot be managed by linux.)

After that you can use ***gparted*** to create partitions for Ubuntu.

---

### Post by Bobby_James on 2014-07-22
I get it - just use a Windows 8 tool like the built-in Disk Management (e.g. [http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/](http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/)). 

Then, in Gparted, give that unallocated space to Ubuntu.

Thanks for pointing this out to me.

---

### Post by sudodus on 2014-07-22
In ***gparted*** you should make (at least) one big root partition and one small swap partition. Let us talk about the details when we know how much space you need for Windows, and how much can be grabbed for Ubuntu. Remember that Windows needs a fair amount of free space in its partitions to work well. Otherwise there will be severe fragmentation.

See also this link (the second post about UEFI)
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by gedakc on 2014-07-22
If GParted shows an exclamation mark beside a partition then that usually means that it was unable to read the file system for some reason.   With NTFS, this is often because the computer was not properly shut down and NTFS was left in an inconsistent state.  When this occurs, reboot into Windows and then use the "Start -> Shutdown" menu option to ensure a clean shutdown.  After that you should be able to resize the NTFS partition with GParted.

---

### Post by Bobby_James on 2014-07-22
I have now resized the Windows partition from Windows 8 and have 50GB of unallocated space.

I booted into Gparted and expanded the ext3 partition to include the unallocated space.

However, because the unallocated space is located "before" the ext3 partition, Gparted warns me that I will have messed up the boot of ext3 should I continue.

Is there a way to somehow ensure that the unallocated space is placed at the end of the current ext3 partition?

Thanks again!

---

### Post by sudodus on 2014-07-22
Good that you succeeded with the resizing :-)

Please post a screenshot of gparted (if possible). Otherwise post the output of the following command (within code tags).

```
sudo parted -l
```

and it will be easier to 'see' the structure and layout of the partitions ... and give advice.

---

### Post by Bobby_James on 2014-07-22
Here you go - thanks!

---

### Post by oldfred on 2014-07-22
Moving partitions is like the old slide puzzles just only one line not a grid.

I generally do not like moving partitions left as it has a higher risk. But any partition change has some risk as if interrupted for any reason data is corrupted and usually not recoverable. I have not kept a list but reason for power failure and interruption include, dog, cat, child, foot, no battery, low battery, poor power company and many others. 

Or please do a good backup so you do not have to create a new excuse. :)

Just moving partition should not require reinstall of grub, but always best to have live installer for current version of Ubuntu handy just in case. If you delete a partition and create a new one and restore data then UUID will change and you have to restore grub.

Usually you have to move partition left and then expand to the right. You have to use gparted liveCD or Ubuntu installer which also has gparted. And may have to also unmount swap if mounted. Little key symbol shows mounted partitions.

Why ext3? Just about everyone now uses ext4 and it works better for many things.

---

### Post by sudodus on 2014-07-23
I have not much to add to oldfred's advice, I only want to repeat and add bit about backup:

Please ***backup*** your whole drive or at least your important data (pictures, documents, ...) before you continue. You should also make a Windows recovery disk, if you do not backup up your whole drive. It is a good idea to ***test*** your backup. Otherwise you don't know if it really works.

---

