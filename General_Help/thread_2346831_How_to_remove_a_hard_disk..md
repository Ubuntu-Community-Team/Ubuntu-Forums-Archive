---
title: "How to remove a hard disk."
date: 2016-12-19
forum: General Help
---

### Post by Ifaistos on 2016-12-19
Hello :-)

I have installed Ubuntu on a rig with 3 HDs.
One of them I want to move to a new machine.

However when I removed the HD, my machine does not start.
It get's me to emergency screen.

What do I need to do in order to be able to boot this machine?
It seems that Ubuntu is looking for it, although the HD does not have a boot sector or any data.
I was only using it for store data from Bitcoin Core, which I have uninstalled.

Thanks for your help!

ps.  By the way ... can someone explain to me why Ubuntu does not boot?

---

### Post by leunam12 on 2016-12-19
Hi, if there were no boot files on that drive, the only reason I can think of is that maybe you disconnected something else while removing the hard drive.
Also if the drive that you removed was set to be mounted automatically at boot time, then you have to modify your /etc/fstab file and delete or comment out the line that tells the operating system to mount the drive.

---

### Post by yancek on 2016-12-19
You need to post more information and the boot repair software is the best to run.  Make sure you select the Create BootInfo Summary option rather than trying to make any repairs.  That will provide information on the number of drives/partitions as well as boot files and other information so post a link to the output here after running it.  

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Since you only mention Ubuntu, it is possible that you have boot code in the MBR or an EFI partition on that drive.  This info will show with boot repair.

---

### Post by Ifaistos on 2016-12-19
> **leunam12 said:**
> Hi, if there were no boot files on that drive, the only reason I can think of is that maybe you disconnected something else while removing the hard drive.
Also if the drive that you removed was set to be mounted automatically at boot time, then you have to modify your /etc/fstab file and delete or comment out the line that tells the operating system to mount the drive.

Here is my fstab file contents.
I want to move HD sdc1 that is mounted on to /home/evans/250GB.

What do I need to do?

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=aca434d0-80a4-4065-b268-820ad4f9ea34 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=831c0848-9155-4bc7-8bec-a4cedb5b65ef /home           ext4    defaults        0       2
# /home/evans/250GB was on /dev/sdc1 during installation
UUID=c1782451-64b8-413c-b1b3-02361e5965ce /home/evans/250GB ext4    defaults        0       2
# /home/evans/400GB was on /dev/sdb2 during installation
UUID=E200FA5900FA33DF /home/evans/400GB ntfs    defaults,umask=007,gid=46 0       0
# /home/evans/Data240GB was on /dev/sdd2 during installation
UUID=33CD91081062AE0E /home/evans/Data240GB ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=6719b691-e3df-43bb-af63-6f296902e7c6 none            swap    sw              0       0
# swap was on /dev/sdd6 during installation
UUID=4380cf7c-fd62-4244-8d2c-a17c8a2962aa none            swap    sw              0       0

---

### Post by The Cog on 2016-12-19
Put a # in front of the line in /etc/fstab that defines that mount, so that it looks like this:
#UUID=c1782451-64b8-413c-b1b3-02361e5965ce /home/evans/250GB ext4 defaults 0 2
Alternatively, just delete the line (and the description line above it). You probably won't want it again.

Next time you reboot, it won't get mounted. You can unmount it without rebooting with this command (note the strange spelling of umount):
```
sudo umount /home/evans/250GB
```

P.S. To edit the file, use the command
```
sudo nano /etc/fstab
```

---

### Post by Ifaistos on 2016-12-19
Worked perfectly !!

Thank you all !!

---

