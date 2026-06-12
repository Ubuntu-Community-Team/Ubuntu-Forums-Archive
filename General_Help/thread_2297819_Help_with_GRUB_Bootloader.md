---
title: "Help with GRUB Bootloader"
date: 2015-10-06
forum: General Help
---

### Post by robert71 on 2015-10-06
Hello all, 

       I have a situation that requires some help with boot loader, here goes:

I have three disks in my computer, on disk one there is windows, disk two is ubuntu and disk three is also ubuntu.

I needed the space on disk two but need ubuntu for my work (cant be done in windows) so I installed ubuntu on disk three and was going to delete the install on disk two. 

Problem is grub bootloader is coming up with the old install and i need the grub bootlader to point to the new install and also see my win 7. 


Anyone able to help me do that ? 

Many Thanks

---

### Post by sandyd on 2015-10-06
> **robert71 said:**
> Hello all, 

       I have a situation that requires some help with boot loader, here goes:

I have three disks in my computer, on disk one there is windows, disk two is ubuntu and disk three is also ubuntu.

I needed the space on disk two but need ubuntu for my work (cant be done in windows) so I installed ubuntu on disk three and was going to delete the install on disk two. 

Problem is grub bootloader is coming up with the old install and i need the grub bootloader to point to the new install and also see my win 7. 


Anyone able to help me do that ? 

Many Thanks
It is likely that during installation of Ubuntu on drive 2, Ubuntu installed the bootloader (GRUB2) on the boot drive. When you installed Ubuntu on drive 3, GRUB was not installed on the boot drive and therefore did not overwrite the existing GRUB2 bootloader that pointed to the Ubuntu installation on drive 2.

During the installation, assuming you chose "Something Else", you will get a chance to choose the boot drive (which should be set to disk one, assuming disk one is the drive that the machine boots from). If not, you can use boot-repair either from a livecd or the ubuntu installation on the third disk to install the bootloader on disk one.

If you are not sure which device is the boot drive (should be SATA1), you can create a bootinfo summary from the Boot Repair tool and post it here.

---

### Post by robert71 on 2015-10-06
Hello Sandyd, 

            Thanks for the help, here is the bootinfo you requested: [http://paste.ubuntu.com/12700241/](http://paste.ubuntu.com/12700241/)

Quck Question: 

Would doing a boot repair also add the Windows entry for me ? 

Thanks.

---

### Post by sandyd on 2015-10-06
Ok, so your boot drive is /dev/sda.

I can't tell which drive you just installed Ubuntu on, should either be sdc or sdd, that is the only missing part of the puzzle.

Boot using the current grub, and after logging in, run
```

mount -l
```

That should show you which partition is mounted as the root partition (/).
Should be something like below. The partition should be mounted on "/"
```

[COLOR="#FF0000"]/dev/sdd[/COLOR]1 on /
```

You need the red portion. From your partition layout, it *should* be /dev/sdd, but I just want to make sure.

Go back to the liveusb, startup boot repair, and click on "advanced". Make sure "Reinstall Grub" is ticked. Click on the tab that says "Grub Location".

If you got "/dev/sdd" in the above command, choose "OS to boot by default" to "/dev/sdc2" (It should say "Ubuntu 14.04.3 beside it). 
Choose "Place grub into" and change it to "sda", and choose apply.  After it is done, reboot.

After we get grub back to normal, we can make Windows show up.

---

### Post by robert71 on 2015-10-06
Hi here is the output from mount -l 

```
/dev/sdc2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
vmware-vmblock on /run/vmblock-fuse type fuse.vmware-vmblock (rw,nosuid,nodev,default_permissions,allow_other)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=tom)
/dev/sda1 on /media/tom/SSD type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) [SSD]
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2 on /mnt/boot-sav/sdb2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [New Volume]
/dev/sdb3 on /mnt/boot-sav/sdb3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [Store]
/dev/sdb5 on /mnt/boot-sav/sdb5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [PF]
/dev/sdd1 on /mnt/boot-sav/sdd1 type ext4 (rw)
/dev/sdd3 on /mnt/boot-sav/sdd3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) [New Volume]
/dev/sdd5 on /mnt/boot-sav/sdd5 type ext4 (rw)
/dev/sdd6 on /mnt/boot-sav/sdd6 type ext4 (rw)
/dev/sdd7 on /mnt/boot-sav/sdd7 type ext4 (rw)
/dev/sde1 on /mnt/boot-sav/sde1 type vfat (rw) [ElTorito]
.
```

I ran the boot repair and it gave the following error

"GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again."

---

### Post by sandyd on 2015-10-06
I said only if you got "/dev/sdd" above command, go on with the grub install :p

Set the following in the "Grub Location" tab.

In "OS to boot by default", choose the Ubuntu 14.04 install that is **not** "sdc2", should be sdd5

Checkmark "Use boot partition" and choose sdd1

Choose "Place Grub into", and make sure it's sda

---

### Post by robert71 on 2015-10-06
oooh lols....

I have a live usb the one i used to install ubuntu can i run boot repair from that ?

If so pleasse tell me how .

---

### Post by robert71 on 2015-10-06
Hey i got Boot Repair to run off the live CD and did what you said with it. 

the following is the results: 

[http://paste.ubuntu.com/12700932/](http://paste.ubuntu.com/12700932/)

Is more required ??

---

### Post by robert71 on 2015-10-06
Hi Based on what we did with boot repair  i have access to the old and the new ubuntu through the boot menu. 

My, windows access is gone, can we fix that please.  Thanks.

---

