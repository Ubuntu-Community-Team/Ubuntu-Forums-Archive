---
title: "Removed RAID5 array and now no boot"
date: 2007-07-27
forum: General Help
---

### Post by Child of Wonder on 2007-07-27
I'm having a great time with this little problem!  :mad:

My home server is running Ubuntu 6.10 server and had the following disk configuration:

/dev/md0 = 3x500GB RAID 5, /storage
/dev/md1 = 2x20GB RAID 1, /
/dev/md2 = 2x20GB RAID 1, swap

I'm migrating to a VMWare ESX server and now that I have the file share aspect of it set up, I copied all my data off the /storage share and removed the 3x500GB drives.

However, now my system can't boot since mdadm now labels the 2x20GB drives as /dev/md0 and /dev/md1, respectively.

My system is using lilo as a bootloader.  I've even gone so far as to plug the 3x500GB drives back in but all I seem to get is initramfs prompt.  I did get it to boot normally once but then the 3x500GB drives were /dev/md0 again and I could not execute /sbin/lilo to boot to md0 in the future (which would be my RAID 1 array after I power down and remove the 500GB drives again) because the 3x500GB drives are currently RAID 5 and lilo won't apply the changes.

I know all I need to do is change lilo.conf to reflect the correct md0 to boot to, however I have no way of running /sbin/lilo to apply the changes.  Any suggestions?

---

### Post by dando80 on 2007-07-27
Hi there,

Try booting from a livecd and using the "vol_id /dev/mdx" command to get the ID_FS_UUID. I know that you can use this to specify your root partition in grub so I guess you can do it in lilo also. If you run the "mdadm --detail /dev/mdx" command you will get another UID which you can use to tell lilo which partition you are bootstrapping to??

Sorry for not having the exact details. I havent used lilo in 4 years.

---

### Post by Child of Wonder on 2007-07-27
That's where the problem is -- how do I apply the changes from lilo.conf to the MBR from a LiveCD or initramfs?

---

### Post by dando80 on 2007-07-27
Does lilo not let u edit the options you are passing the kernel before it starts booting? Is there a key you can hit to change the current

---

### Post by Child of Wonder on 2007-07-27
No, there's no option to enter any options at boot that I can see.

---

### Post by dando80 on 2007-07-27
You might be able to do this with an ubuntu livecd. Else any of the rescue cds you find in google should work. Basically you want to boot the livecd and mount your old partitions. Then you can use the chroot command and reinstall the boot loader after patching it lilo.conf  to work ok with your current devices. Then when you next boot from the hard disk you should be ok.

---

### Post by Child of Wonder on 2007-07-27
That's exactly what I ended up doing.  Great minds think alike.

Thanks for the help.

---

