---
title: "Ubuntu 17.10/kernel 4.13.x cannot recognize hard drive that works fine in 4.10.x"
date: 2017-10-31
forum: General Help
---

### Post by chucksense on 2017-10-31
After upgrading to 17.10 (kernel 4.13.x), the system cannot "see" a drive that works perfectly fine when I boot into 4.10.x instead.

Example, running `sudo blkid` doesn't even list the device in 4.13.x and it doesn't appear in `/dev/sdX` or even `/dev/disks/by-uuid/`.

Anybody have any ideas on how to try to figure out why this disk is nonexistent, but only under kernel 4.13.x?

Thank you in advance!

---

### Post by oldfred on 2017-10-31
Post what it shows with those commands when you boot 4.10.x.

---

### Post by chucksense on 2017-11-01
Here you go.  `/dev/sda1` is the partition in question.  When I boot to 4.13.x, sdb1 and sdb2 become sda1 and sda2 and there is no sdbX nor is the UUID listed at all in the second command.

[FONT=courier new]$ sudo blkid[/FONT]
[FONT=courier new][sudo] password for user: [/FONT]
[FONT=courier new]/dev/sda1: LABEL="drive" UUID="fea81e48-69e8-4c5b-8022-cbb793c04eee" TYPE="ext4" PARTUUID="fcc5a93c-38d5-47c7-90ac-ae2bc00577aa"[/FONT]
[FONT=courier new]/dev/sdb1: UUID="7F39-483A" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="38b9ba9e-a5b2-43ae-8cf6-2c1d8aa133fc"[/FONT]
[FONT=courier new]/dev/sdb2: UUID="qcIT7f-qcrE-Ej7m-aANa-I1UD-5TvA-fUZZPM" TYPE="LVM2_member" PARTUUID="736726e8-5263-4e33-b332-c8c2e5281d1e"[/FONT]
[FONT=courier new]/dev/mapper/ubuntu--gnome--vg-root: UUID="e121a14f-6885-4e5b-8951-593664b7838a" TYPE="ext4"[/FONT]
[FONT=courier new]/dev/mapper/ubuntu--gnome--vg-swap_1: UUID="d6a0a7e9-78fa-4894-a9ab-8a71cd6e572a" TYPE="swap"

[/FONT][FONT=courier new]$ ls /dev/disk/by-uuid/[/FONT]
[FONT=courier new]7F39-483A  d6a0a7e9-78fa-4894-a9ab-8a71cd6e572a  e121a14f-6885-4e5b-8951-593664b7838a  fea81e48-69e8-4c5b-8022-cbb793c04eee[/FONT]

---

### Post by oldfred on 2017-11-01
I do not know LVM installs.
But yours is showing on sdb.
Ubuntu version of Grub's UEFI only installs to ESP on sda, but you are showing ESP - efi system partition on sdb?
What is sda, your flash drive?
Or do you have a standard partitioned install in sda1 using BIOS boot?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by chucksense on 2017-11-02
> **oldfred said:**
> I do not know LVM installs.
What is sda, your flash drive?
Or do you have a standard partitioned install in sda1 using BIOS boot?


I will work on Boot-Info (but it will take be a day or two).  In the meantime, if it's helpful, here is further explanation on the drives.

sdb is the boot/os drive and is a ssd.
sda is a hdd and is actually mapped to my /home/user directory in my fstab (though of course that doesn't work in 4.13.x now, unless I comment that line out, 4.13.x won't even boot)

This is how they were when I installed the operating system.  My understanding is that the determination of sda vs sdb is by where the drives are connected to the sata (though I could absolutely be wrong about that), and unfortunately due to the layout of my computer I cannot easily swap them.

---

### Post by oldfred on 2017-11-02
My systems are mapped by how they are plugged into the SATA ports. And since I use devices in some places I have issues where I skipped a port and on reboot if flash drive still plugged in all the higher ports change and flash drive uses the skipped port as its location.

Is HDD gpt partitioned?
While gpt not essential for UEFI boot, better to use gpt. And then add an ESP on sda so grub can install correctly. I wanted to understand grub UEFI installs better and differences, but noticed Fedora's install actually installed to ESP on sdb, so something Ubuntu has done to grub installer is the issue.

I do not use LVM, but I thought one of its advantages was you volumes could span drives. Only issue was when one drive fails you lose all data from both drives, so good backups are required.

---

### Post by chucksense on 2017-11-02
I was able to swap the drives connection order in SATA.  Now the ssd (which works fine under both kernels) is always sda.  The hdd is now sdb under 4.10.x and still doesn't appear at all under 4.13.x.

It is gpt partitioned.

The hdd hardware is a 3TB WD Green WD30EZRX if that makes some kind of difference (I'm starting to think it must).

---

### Post by oldfred on 2017-11-02
Large HDD should not matter, seen many others with installs to large drives.

Did you post this before?
       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by chucksense on 2017-11-05
Hi oldfred, I'll have the boot-info as requested for you tomorrow.  However, in the meantime I'm almost certain it's not relevant.  I formatted the drives and removed all partitions and the WD30EZRX drive still isn't recognized by the system under 4.13.x kernel.  It causes GParted to hang even trying to open.  When booted under 4.10.x everything works as expected.  So I believe it's something unrelated to boot at all, but something to do with either kernel support being bad of this drive or perhaps of my SATA controller.  Still, as soon as the OS image finishes downloading (slow connection), I'll run the boot-info for reference as requested.

---

### Post by oldfred on 2017-11-05
Did you also update UEFI from vendor?
That would reset many settings to defaults which may make a difference.

What are drives set in UEFI, should be AHCI, not RAID, IDE nor any Intel SRT type that looks like RAID to Linux.

What brand/model system?

---

### Post by chucksense on 2017-11-06
System is an HP Z420 Tower Workstation.  Some specs are [available here]("https://support.hp.com/us-en/product/hp-z420-workstation/5225033/document/c03277050"), mine has a XEON E5-1620 @ 3.60 GHz chip.  8GB Ram.  No overclocking or other tinkering.

I have not tried to update UEFI from the vendor, but will look into that, great idea!

In troubleshooting this issue, I earlier discovered my drives were set to RAID+AHCI and I switched it to just AHCI, however this made no difference.  Gparted still hangs trying to even "see" the unformatted/unpartitioned drive (again under 4.13.x only, 4.10.x sees it just fine).

I'll have that boot-info for you today (download has 1 more hour to go) just in case it turns out to be relevant.

Thank you for all of your help.

---

### Post by oldfred on 2017-11-06
RAID settings may leave meta-data on a drive.

If you are not running RAID.

 sudo mdadm --detail-platform
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings, should be AHCI 

I know in past many users have used above command. But mdadm has replaced dmraid for many uses.
In the pdf from Intel on newer NVMe drives was the only place I have seen what looks like the equivalent command.

 sudo mdadm --detail-platform
[http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf](http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf)
sudo mdadm --zero-superblock /dev/<nvmeXn1>

---

### Post by chucksense on 2017-11-06
Here is boot-info as promised: [http://paste.ubuntu.com/25903357/](http://paste.ubuntu.com/25903357/) -- This was run from a Ubuntu GNOME 17.04 live disk.  The same boot-info process hangs (just like GParted et all) on Ubuntu 17.10 live disk.

I've completely reformatted and repartitioned all drives on this system since switching from RAID+AHCI to just AHCI, is there any reason then to still attempt the above commands?

Also, when I completely reformatted and reinstalled Ubuntu GNOME 17.04, I could not for the life of me get it to boot in EFI mode so it's using legacy mode (I reinstalled the OS a dozen times using various combinations AND have tried repairing the boot using boot-info).  Earlier, I assumed this shouldn't matter too much but now I'm learning I may not be able to update the machine firmware without booting into EFI mode.  ](*,)

---

### Post by chucksense on 2017-11-06
FYI I had the specs on the machine wrong (dislexic moment, had it has Z240 instead of Z420).  Updated the above.

---

### Post by oldfred on 2017-11-06
You show gpt partitioning which I do suggest.
Gpt is standard with UEFI, but can be used with Ubuntu and BIOS boot, but needs another partition.
With UEFI you have to have an ESP - efi system partition (FAT32).
And if gpt and BIOS you have to have a bios_grub partition. It is unformatted and only needs to be 1 or 2MB and can be anywhere on drive.
Grub in BIOS mode will not correctly install to MBR on gpt drive unless you have the bios_grub partition.

I started using gpt with my BIOS only system back in 2010.
When UEFI became the new thing, I started converting all drives to gpt, but added both an ESP & bios_grub, even though still booting with BIOS. 
Now even with my new UEFI systems I still add a bios_grub more from habit than a requirement as I do not expect to BIOS boot ever again.

These are the first two partitions I add to every drive. On my larger flash drives (still small drive), I make ESP 100MB.
       Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

I do not know if your HP is like other HP desktops that have modified UEFI.
HP violates UEFI standard that says NOT to use description. And only allowed description is "Windows Boot Manager". 
Some only booting Ubuntu add a new entry to UEFI boot that says Windows but actually uses the Ubuntu/grub/shim boot file. It seems to check description, but not actual boot file.

       sudo efibootmgr -v 
man efibootmgr

 
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1 or additional parameters required.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

---

### Post by chucksense on 2017-11-06
So interestingly, my firmware does show it up in the UEFI section of the Boot Menu:
[IMG]https://i.imgur.com/iB81yxU.jpg?1[/IMG]


And yet it essentially skips that one and proceeds to boot it using the Legacy method:

[FONT=Menlo]$ [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS[/FONT]
[FONT=Menlo]BIOS[/FONT]
[FONT=Menlo]$ sudo efibootmgr -v[/FONT]
[FONT=Menlo]EFI variables are not supported on this system.[/FONT]



Here is `sudo efibootmgr -v` when booted from the Ubuntu GNOME 17.04 live disk.

[FONT=courier new]$ sudo efibootmgr -v
BootCurrent: 0008
Timeout: 0 seconds
BootOrder: 0000,0001,0002,0008,0003,0004,0005,0006,0007
Boot0000* ubuntu    HD(1,GPT,050f9f81-279c-42e7-a50b-01482564912d,0x800,0x112000)/File(\EFI\ubuntu\grubx64.efi)
Boot0001* DTO UEFI USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)AMBO
Boot0002* DTO UEFI USB Hard Drive   VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)AMBO
Boot0003* DTO UEFI ATAPI CD-ROM Drive   VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0300000001)AMBO
Boot0004* CD/DVD Drive  BBS(CDROM,,0x0)AMGOAMNOO.......+.S.A.T.A.:. .P.M.........................rN.D+..,.\.........AMBO
Boot0005* DTO Legacy USB Floppy/CD  VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000000)AMBO
Boot0006* Hard Drive    BBS(HD,,0x0)AMGOAMNO?.........F.a.k.e. .U.s.b. .O.p.t.i.o.n...............AMBOAMNO[.......+.M.a.x.t.o.r. .6.L.0.8.0.M.0.........................rN.D+..,.\.........AMBOAMNOq.......+.S.a.m.s.u.n.g. .S.S.D. .8.5.0. .E.V.O. .2.5.0.G.B.........................rN.D+..,.\.........AMBOAMNOg.......+.W.D.C. .W.D.3.0.E.Z.R.X.-.0.0.D.8.P.B.0.........................rN.D+..,.\.........AMBO
Boot0007* IBA GE Slot 00C8 v1556    BBS(Network,,0x0)AMBO
Boot0008* Maxtor 6L080M0    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(1,MBR,0x4294967282,0x14a80,0x1200)AMBO[/FONT]


I tried renaming to the "Windows Boot Manager" and same result as above (only now the boot menu shows that instead of "ubuntu").  I intentionally used `grubx64.efi` and not `shimx64.efi` as I have Secure Boot disabled (enabling it causes the system to not boot due to an unsupported video card).  That said, I tried it with `shimx64.efi` instead for giggles and that didn't work either (the UEFI boot was bypassed in favor of other devices of later precedence).

---

### Post by chucksense on 2017-11-07
@oldfred I was able to properly boot UEFI using the following steps.  Documenting it here in case it's useful for others, HOWEVER, this unfortunately does not at all fix my underlying issue of the OS not recognizing my HDD in Ubuntu 17.10.

All this done while booted in the Ubuntu-GNOME 17.04 live disk environment.

1. Removed *grub-pc* and installed *grub-efi-amd64*

[FONT=courier new]$ sudo apt-get remove grub-pc
$ sudo apt-get install grub-efi-amd64[/FONT]


2. Mount all drives in the necessary locations and CHROOT 
[FONT=courier new]$ mount /dev/sda3 /mnt
$ mount /dev/sda2 /mnt/boot
$ mount /dev/sda1 /mnt/boot/efi[/FONT]
[FONT=courier new]$ mount -o bind /dev /mnt/dev[/FONT]
[FONT=courier new]$ mount -o bind /dev/pts /mnt/dev/pts[/FONT]
[FONT=courier new]$ mount -o bind /proc /mnt/proc[/FONT]
[FONT=courier new]$ mount -o bind /run /mnt/run[/FONT]
[FONT=courier new]$ mount -o bind /sys /mnt/sys[/FONT]
[FONT=courier new]$ sudo chroot /mnt[/FONT]


3. Reinstalled and reconfigured grub:
[FONT=courier new]$ grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=grub
$ grub-mkconfig -o /boot/grub/grub.cfg[/FONT]

Dropped back out of chroot/super user by Ctrl-D.

4. Reconfigured efibootmgr by removing the existing entry and adding back the newly installed

[FONT=courier new]$ sudo efibootmgr -b 0000 -B
$ sudo efibootmgr -c -L "ubuntu" -l "\EFI\grub\grubx64.efi"[/FONT]

5. Reboot and now I'm booting into UEFI (woohoo!)
[FONT=courier new]$ [ -d /sys/firmware/efi ] && echo UEFI || echo BIOS[/FONT]
[FONT=courier new]UEFI[/FONT]

Now back to the original issue.  I have since upgraded my firmware, but still no luck getting kernel 4.13.x to see my HDD which again works perfectly fine under 4.10.x.

---

### Post by oldfred on 2017-11-07
Glad  you got UEFI working.
Did you see if you had RAID settings on drive, post #12?

---

### Post by chucksense on 2017-11-07
Yes, as mentioned in #13:

> I've completely reformatted and repartitioned all drives on this system since switching from RAID+AHCI to just AHCI,  is there any reason then to still attempt the above commands?

---

### Post by chucksense on 2017-11-07
[FONT=courier new]$ sudo dmraid -E -r /dev/sda
no raid disks and with names: "/dev/sda"
$ sudo dmraid -E -r /dev/sdb
no raid disks and with names: "/dev/sdb"[/FONT]

---

### Post by oldfred on 2017-11-07
Because you created extra partitions for folder in /, I think Boot-Repair cannot repair your system.
Boot-Repair was updated to add /boot if you check that and the ESP, but I think /var also has to be mounted.
You probably had to use chroot and make sure you mount all partition (except /home) to make sure any repairs work.

Do not understand why one kernel sees drive and other does not.
Usually newer kernel fixes issues with older kernel, but sometimes there are regressions.

---

### Post by chucksense on 2017-11-07
While I appreciate the help getting UEFI working properly, I don't think this has anything to do with boot.  When booting from the Ubuntu 17.10 live disk, my drive is still not at all detectable and causes boot-info, parted, and gparted all to hang when trying to access it.

Thank you for your time anyway!

---

### Post by chucksense on 2017-11-07
Filed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1730746](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1730746)

---

