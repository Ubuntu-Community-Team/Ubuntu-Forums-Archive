---
title: "LVM errors during bootup after trying software RAID5"
date: 2006-09-06
forum: General Help
---

### Post by ethereal on 2006-09-06
Hi,

I recently installed kubuntu 6.06 and tried to setup a raid 5 array of 4 250GB drives. I was following along with the guide here: [http://gridpt1.fe.up.pt/mlopes/blog/index.php/software-raid-in-ubuntu/]("http://gridpt1.fe.up.pt/mlopes/blog/index.php/software-raid-in-ubuntu/"). After I fdisk'd the 4 drives, I rebooted and got errors during bootup, specifically when reaching: starting Enterprise Volume management System... The error is "*** glibc detected *** corrupted double-linked list: 0x0000000000530c20 ***". I think I may have made the logical partition occupy the same space as the primary partion on the drives. (the reason for the logical partition was so that I could used the linux auto-raid fs during fdisk.) Is there anythink I can do to skip LVM loading and bootup so I can correct this error? ](*,)  I tried rebooting with the livecd, but I got a similar error, except the hex code after double-linked list was slightly different.

Thanks for any help

---

### Post by Ocxic on 2006-09-06
I think you just screwed your filesytem, boot with a l ive cd and run fsck from a terminal on you disks, that'll hopefully get you a bootable os.

most likly you'll have to re-install. scince you say u used fdisk it's possible that you just hosed you partition table, you can use testdisk (it's in the repositories) to recover your partions, but you'll still prolly end up re-installing.

---

### Post by ethereal on 2006-09-07
Thanks for the reply Ocxic.

I actually have ubuntu on a separate drive.  The raid 5 array is completely separate, and will only be used for mass storage.  I tried booting with a livecd of ubuntu already, and it ran into errors at the same point during bootup.  Is there some way I can do a low level type init with ubuntu, such as a single-user mode so that only a minimal amount of services are started?  (hopefully enterprise management won't start, and I'll be able to boot.)

---

### Post by kyke on 2006-09-07
Hello,

I have a similar problem, installing LVM over Software-RAID1. I created the RAID1 volume /dev/md1 and later the LVM scheme over it. Then I reboot to test everything was okay, but I think the RAID1 was still under construction (it takes some time to replicate), so when booting is hangs after the EVMS message, just like you, with glibc error.

I booted with a "install CD" from breezy I got at hand, in 'expert' mode so I got full control in the menu, loaded the modules, activate LVM and MD on the menu and then opened a shell and fixed the problem. Just 'stopped' the RAID1 (remove it!) and reboot. My box worked again, after the obvious LVM error in the boot process.

After login I recreate the RAID1 with same conditions and the LVM start working again! Lovely linux!

Hope this helps.

---

### Post by Ocxic on 2006-09-07
[ethreal] post the output of "sudo fdisk -l" and what your partition table looked like b4 you setup the raid. What is this auto raid-fs thing you speak of??

[kyke] LVM will "raid" the drives you add to your volume groups, ex:

volume group 1 uses hda(100GB) & hdb(100GB), you can create a 200GB logical volume to use for you files.

in short you don't need to use raid and LVM to get the "raid" effect, LVM will take care of that, and also allows you to expand your filesystem to new disks, if you wish to expaned your memory.

---

### Post by kyke on 2006-09-08
> **Ocxic said:**
> of??

[kyke] LVM will "raid" the drives you add to your volume groups, ex:

volume group 1 uses hda(100GB) & hdb(100GB), you can create a 200GB logical volume to use for you files.

in short you don't need to use raid and LVM to get the "raid" effect, LVM will take care of that, and also allows you to expand your filesystem to new disks, if you wish to expaned your memory.

Thanks for your comments. 

I didn't want a "LINEAL" raid but a failover solution, like RAID1 / RAID5, that's why I got the "md" solution, so in case one hdd crashes the system will keep running 100%. 

Over the RAID1/5 I installed LVM for its commodity to manage logical volumes... so got both simplicity and availability in the same score.

---

