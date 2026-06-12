---
title: "Windows Hard Drive Failed, Ubuntu wont boot after removing"
date: 2013-04-08
forum: General Help
---

### Post by zinv on 2013-04-08
So heres the background on what im experiencing: Firstly im running Ubuntu 12.10, now i have 3 sata hd's installed. 

/dev/sda - old windows drive 250gb
/dev/sdb - drive with linux partitions 2tb
/dev/sdc - storage 2tb

Now i had previously seen some smart errors on /dev/hda but paid them no mind. Now that harddrive suddenly failed this morning and no longer even shows in BIOS. This drive was also the location that grub was installed to the mbr. Now since this drive failed i was no longer able to boot into ubuntu. I proceeded to boot from the livecd and install Boot-Repair. After running boot-repair i was once again able to see the grub menu on boot. Now mind you i went to go take care of this on my lunch break and once i saw grub i just pressed enter and left for work. Back at my office i attempted to vnc and ssh into my box at home in order to see what was going on with it. As of now i believe it has hit some kind of error since i am not able to connect or ping it from here now. 

Im just looking for some suggestions on possible files that may need editing or changing. Also wanted to know if since /dev/sda is no longer being detected is there any way that the drive letters may have changed? ie /dev/sdb becoming /dev/sda and /dev/sdc becoming /dev/sdb?

Any insight would be greatly appreciated, also once im able to physically access the machine when i get home i will post any more information i can obtain.

---

### Post by The Cog on 2013-04-08
I know that SystemRescueCD has an option to boot linux from hard disk - it can do that when there is no GRUB at all. It searches for a Linux and boots the first one it can find. I've used it several times to restore a backup - format the disk, un-tar the backup tar file, boot and run the bootloader installer. 
After booting, run
```
sudo update-grub
sudo grub-install /dev/sdb
```
In my case, I also had to fix fstab for the new disk UUID but you shouldn't have to do that bit.

Once booted, **sudo blkid** should tell you if sdb has become sda. Change grub-install to match.

---

### Post by Bashing-om on 2013-04-08
zinv;
In response to your question about changes to drive designators, yep it is possible. That is why using the UUID's of devices was introduced, UUID's do not change. A lot depends on how you set up your system partition access in the config file /etc/fstab.

If in "Boot Repair" you wrote a new grub to sdb , in bios set to boot from this second hard drive, and use UUIDs in fstab, should boot !

That said, how may we serve you ?
[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by zinv on 2013-04-08
I saw that as well when i was going about getting grub back. Figured i should go with the route i was sure of though. Once im home and able to check the blkid's i will do that. Thank you so much for the info :)

---

### Post by zinv on 2013-04-08
I figured it was possible. I'm also pretty sure that my drives were being referenced by UUID's because i had just checked the partitions in webmin when trying to remount the /dev/sda initially when it had failed. I will check though just to make sure. Thank you though for the great information. Hopefully it will be a simple edit of fstab if anything. But i will provide you guys with more information in the coming hours :)

---

### Post by zinv on 2013-04-11
sorry it took so long for me to reply. So it turned out to be that the os was still trying to mount /dev/sda1 on boot. This led to it asking if i wanted to wait or skip waiting for it. But in my quickness to try and alleviate the situation i just decided to reinstall though i probably should have just booted from the live cd  and edited fstab and removed the entry for /dev/sda1. btw they were still being referenced by UUID just for informative purposes lol. but thanks again for the good information and quick replies :)

---

### Post by Bashing-om on 2013-04-11
zinv; All's well that ends well !

Pleased you are up and running, what ever it may take.
Please mark this thread as solved, That aides others and keeps our forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT=3]
mark it up for experience

[/INDENT]

---

