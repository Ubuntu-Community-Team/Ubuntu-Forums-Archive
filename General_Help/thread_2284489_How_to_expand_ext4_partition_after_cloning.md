---
title: "How to expand ext4 partition after cloning"
date: 2015-06-29
forum: General Help
---

### Post by rlovi on 2015-06-29
Hi,

I originally installed Ubuntu Studio 14.04 on a 120GB hard drive and recently cloned it to a new 1TB drive using the command "sudo ddrescue -v -f /dev/sda /dev/sdb".  It worked as I was able to boot from the new disk. What I can't seem to figure out is how to expand the ext4 partition into the free space. Right now I have:

/dev/sda1   ext4   106.7GB
/dev/sda2   extended   7.75GB
/dev/sda5   linux swap   7.75GB
unallocated  817.02GB

I can expand the extended partition using GParted but not the ext4 which is the one I should expand, correct?  Any help would be appreciated.

---

### Post by papibe on 2015-06-29
Hi rlovi. Welcome to the forum ):P

You can't do it while you are using the partition, as it has to be unmounted.

The standard practice is to use GParted from a Live media. You can use the Ubuntu installation CD/USB, but instead of installing choose 'Try Ubuntu'. Once you get to the desktop, you can use Gparted to manage your partitions.

Extending a partition is, for the most part fairly, safe, but as usual there's some risks. Be sure to have your data backed up before attempting it.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by matt_symes on 2015-06-29
Hi

Personally I would delete the swap partition and extended partition using gparted from a live CD/USB, expand the ext4 partition and re-add the swap partition at the end of the new hard drive.

You may have to unmount the swap partition before deleting it. You can do this from gparted. 

Another option is to create a new partition in the free space and mount it using a fstab entry.

Kind regards

---

### Post by rlovi on 2015-06-29
> **matt_symes said:**
> Hi

Personally I would delete the swap partition and extended partition using gparted from a live CD/USB, expand the ext4 partition and re-add the swap partition at the end of the new hard drive.

You may have to unmount the swap partition before deleting it. You can do this from gparted. 



So the extended partition is not needed??  BTW, this is the 64 bit operating system.

I tried expanding the ext4 partition using gparted from the live cd and it was a no go though I could expand the extended partition.

---

### Post by ksantr on 2015-06-29
try lvextend

---

### Post by rlovi on 2015-06-29
ok, since I still had the original harddrive I went ahead and experimented on the newly cloned drive. I took matt_symes advice and booted from the live cd again, started gparted, turned the swap off and then deleted both the extended partition and the linux swap partition. I was then able to expand the ext4 partition leaving around 9GB of space to recreate the swap partition. Applied the changes and rebooted and everything seems to be ok. I just don't understand what that 7.75GB extended partition was for.

BTW for anyone else attempting to do what I did; after making the partition changes and rebooting, my swap was off. I needed to change the UUID in /etc/fstab for the swap partition since it was now on /dev/sda2 instead of /dev/sda5.  It is explained here:

[http://askubuntu.com/questions/501698/after-reboot-swap-turns-off-issue](http://askubuntu.com/questions/501698/after-reboot-swap-turns-off-issue)

---

### Post by rlovi on 2015-06-30
I just answered my own question on an extended partition by reading the post here:

[http://askubuntu.com/questions/179362/how-to-create-partitions-in-ubuntu-while-installing](http://askubuntu.com/questions/179362/how-to-create-partitions-in-ubuntu-while-installing)

Quote: "The second partition will be for Swap. The installer will attempt to  create it as a logical partition, but you do not have to. Like /boot, it  could also be a primary partition. The first logical partition of an  extended partition is /dev/sda5. If you create this partition as a  primary partition, it will be /dev/sda2."

So in my original installation, my swap was created as a logical partition in the 7.75GB extended partition and thus was /dev/sda5. When I followed matt's advice, I created my swap as a primary partition and thus it became /dev/sda2. I love Ubuntu. :)  Thanks everyone!

---

