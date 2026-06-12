---
title: "Software raid on scsi and boot problem"
date: 2006-11-10
forum: General Help
---

### Post by karaluh on 2006-11-10
I've got scsi Adaptec controler with 2 drives. The only raid this controler suports is HostRAID, wchich in fact is a fake-raid. Because there are still issues with fake-raid in linux, I've decided not to use fake-raid and build software raid instead. So, I've disabled raid in bios, created regular ext3 /boot partition outside raid at the begining of the sda disk and set the bootable flag. On sdb I left an amount of free space equal to the /boot size unalocated. The rest of the disks is configured in RAID 0 (5 partitions). Kubuntu (Eft) and grub install fine, after reboot grub starts, splash is displayed and nothing more happens. On tty1 i've got:

STARTING UP... 

circa one minute of inactivity and then:

mdadm /dev/md0 has been started with 2 drives 
mdadm /dev/md1 has been started with 2 drives 
mdadm /dev/md2 has been started with 2 drives 
mdadm /dev/md3 has been started with 2 drives 
mdadm /dev/md4 has been started with 2 drives 

and nothing more happens.

I just installed dapper and here is what happens on tty:
Uncompresing Linux... Ok, booting kernel

couple seconds of inactivity

mdadm /dev/md0 has been started with 2 drives 
mdadm /dev/md1 has been started with 2 drives 
mdadm /dev/md2 has been started with 2 drives 
mdadm /dev/md3 has been started with 2 drives 
mdadm /dev/md4 has been started with 2 drives 

*INIT: No inittab file found.

Enter runlevel:

Is there someting i can do with it? It will be production ltsp server, so i would like to get it work on dapper.

---

### Post by yota on 2006-11-10
The complain is that the init process can't load the /etc/inittab file.
Most probably you're telling the kernel the wrong root=/dev/md* device. Notice that the md number is chronological (sooner the device is detected and added the lower the number will be) and can be different from the one you've seen during installation or manual creation.

So please check that the device you pass as root=/dev/md* in the /boot/grub/menu.lst file is actually the one containing the root filesystem; eventually cycle trough them all and see.

You can edit boot options directly in grub (press e), without modifying and saving the file each tima.

Hope this helps!

---

### Post by karaluh on 2006-11-13
> **yota said:**
> The complain is that the init process can't load the /etc/inittab file.

When I read this, I started to wandering if grub mounts all md devices. It doesn't, so you cannot put /etc on separate partition, and that was what I did. Big thanks for your help. :cool:

---

