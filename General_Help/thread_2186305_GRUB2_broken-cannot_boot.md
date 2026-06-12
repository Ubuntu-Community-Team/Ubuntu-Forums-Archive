---
title: "GRUB2 broken-cannot boot"
date: 2013-11-06
forum: General Help
---

### Post by jlh68 on 2013-11-06
My grub2 is broken as I cannot boot on this netbook. It started with the last kernel update.  I am able to boot with Rescutux on a flash drive.

I tried to use Rescutux to repair the grub, but it would not work due to no WiFi connection.  The wifi  manager on Rescutux  does not work and Rescutux will not use the computer wifi manager, which does work as evidenced by this post.

I hope soemone will provide some solution to this problem.

Thanks

---

### Post by Bashing-om on 2013-11-06
jlh68; Hi !

Show us what we are working toward, as to where grub should be installed.
Post the output - from the liveFlashDrive - of terminal codes:
```

sudo fdisk -lu
sudo blkid

```
Then we can try and install grub properly maybe have to install grub from scratch. But, can be done !

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jlh68 on 2013-11-06
Is this the infor you need? It is from the hard drive.
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe282769

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27469824   101197823    36864000    7  HPFS/NTFS/exFAT
/dev/sda4       101199870   625141759   261970945    5  Extended
/dev/sda5       101199872   102174719      487424   83  Linux
/dev/sda6       102176768   110376959     4100096   82  Linux swap / Solaris
/dev/sda7       110379008   168970239    29295616   83  Linux
/dev/sda8       168972288   625141759   228084736   83  Linux


john@Nighthawk:~$ sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="0CA20080A200708E" TYPE="ntfs" 
/dev/sda2: LABEL="WindowsBoot" UUID="F07602097601D0F0" TYPE="ntfs" 
/dev/sda3: LABEL="WindozeData" UUID="F82A04532A0410F4" TYPE="ntfs" 
/dev/sda5: LABEL="Boot" UUID="f62ec458-671d-4fd2-a09d-a49a4b221b72" TYPE="ext4" 
/dev/sda6: UUID="546f9a8e-a173-41ff-8d94-8886cf8d5d37" TYPE="swap" 
/dev/sda7: LABEL="Ubuntu 12.04LTS" UUID="0a007cf4-5612-4e65-b1ba-ea3b04d16e44" TYPE="ext4" 
/dev/sda8: LABEL="John's Data" UUID="f63eadad-6024-4da2-a3cb-725b9e93db45" TYPE="ext4" 
john@Nighthawk:~$ 


---

### Post by jlh68 on 2013-11-06
sda5 is where the GRUB should be.  As you can see it is a dual boot computer with Ubuntu 12.04LTS and Windows 7.  The first partition is the windows recovery partition, the second partition is the windows operating system and data, the thirs is the windows loader, then we get to the EXT4 partitions, sda5 is the GRUB boot one, then a swap partition, then the Ubuntu OS, and finally sda8 is my data partition.  

I cannot mount the Rescutux flash drive once I have removed it.  So I cannot get anython from it.  I just use it to find an OS, and then boot, after that I can remove it fromt he computer and the computer works just like it had been booted with it self.

---

### Post by jlh68 on 2013-11-06
Another bit of info, my laptop died and I have to replace the mother board, so I am using the laptop hard drive in the new netbook (0725).  The netbook hard drive has a boot problem also, that hard drive is dual boot, bu it will not boot into windows 7, it will boot Ubuntu.  I will figure out that one later.  I hope o have the laptop M/B installed tomorrow or Friday, and return the hard drive to it.  Then I will tackle the other (netbook) problem.

---

### Post by Bashing-om on 2013-11-06
jlh68; Hi !

The info provided is great. We do know what/where must be done.
Now comes a maybe problem:
> 
In command prompt, do not install grub loader when your are inside the /mnt directory or the directory where your target hard disk is mounted.  It doesn't work sometime.

Which means we need to do this from a liveMeDium/ as in a liveDVD. // "Rescutux" is that only a boot loader / boot rescue ?

I would be the more comfortable passing instruction on to install grub from the perspective of booting from a ubuntu liveDVD of the same version that you have installed. An area I have a bit of experience with.

Else: it might be possible to cheat and install directly, I do not consider there would result any additional harm (??). But in all honesty, I would prefer to install from the liveDVD. 

_____________
Wait a bit ! Are you saying that you have the laptop's hard drive installed into the netbook ? Problem "might" arise if the laptop hard drive is set as the boot drive in the netbook... will have to change the UUIDs in /etc/fstab  ... if that is the case to even begin to boot.

[INDENT][INDENT]look'n for a better way
[/INDENT][/INDENT]

---

### Post by oldfred on 2013-11-06
If you can boot into your system, you can just install grub to the MBR.
       #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub

If that does not work, then run Boot-Repair.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by jlh68 on 2013-11-07
I ran in terminal > sudo grub-install /dev/sda and had NO errors.  Still no grub menu.  I get my grub back ground image but no menu is displayed.

I then tried to download Boot-Repair and I got the following message:  > WARNING: The following packages cannot be authenticated!
  libsigsegv2 gawk python-configobj E: There are problems and -y was used without --force-yes

I also tried the Rescutux Boot Repair function without it helping.

---

### Post by jlh68 on 2013-11-07
FYI: Rescutux has the following options, including Boor-Repair.

> GRUB options:

    Restore GRUB and GRUB2
    (>=0.31 beta 4) Update any GRUB2 menues
    Update Debian/Ubuntu grub menues

Windows options:

    Restore Windows MBR (BETA)
    Blank Windows passwords
    (>=0.31 beta 4) Promote a Windows user to Administrator role
    (>=0.31 beta 4) Unlock Windows user

Password options:

    Change Gnu/Linux Password
    Regenerate sudoers file
    Blank Windows passwords

Filesystem options:

    File System Check (Forced Fix) (BETA)

Support options:

    Help
    Web
    Chat
    Show log
    Share log
    Share log on forum
    Boot Info Script

Expert tools:

    (>=0.31 beta 3) boot-repair 3.199
    (>=0.31 beta 1) Gparted 0.12
    (>=0.31 beta 3) os-uninstaller 3.199
    (>=0.31 beta 3) clean-ubiquity 3.199
    (>=0.31 beta 3) photorec
    (>=0.31 beta 3) testdisk 6.13

CLI Programs:

    (>=0.31 beta 1) Gpart 0.1h-11+b1
    (>=0.31 beta 1) extundelete 0.2.0


---

### Post by oldfred on 2013-11-07
Download the liveCD version of Boot-Repair or upload the bootinfoscript from Rescutux. Boot-Repair runs the boot info script report but also adds a lot more info that is useful.

       LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

I believe this is the same as the copy in Rescutux.

 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Bashing-om on 2013-11-07
jlh68; Hey .

I think linear - one option at a time. Let's see if we can determine what grub is doing and why it is not doing as we think it should.
Post back the outputs of terminal codes:
```

sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo grub-probe -t fs_uuid /boot/grub

```

Now here is the current thought disposition on using a seperate /boot partition:
> 
If you want to install GRUB2 to the boot sector of a partition for some strange reason, you may use something like /dev/sda1 or /dev/sda2 for writing GRUB's boot.img to a partition boot sector. The practice of installing GRUB2 to partition boot sectors is not encouraged. It reduces GRUB's reliability and it could be dangerous to other operating systems if users use the grub-install command carelessly or ill-informed and write GRUB to the wrong boot sector.
//
However, sharing /boot is more complex and generally not a good idea, especially as Ubuntu defaults to using no separate boot partition. A separate /boot is something of an anachronism, dating back to limited PC BIOSes that could only handle small disks, so the boot files had to be at the start of the disk. Nowadays, this is no longer applicable and I don't use a boot partition on anything.


With the above in mind, what we can do is purge the present grub and install grub to the MBR of SDA drive. If you do want to keep grub in the separate boot partition, The only may "I" know how is from the liveDVD.

[INDENT][INDENT]more than willing to help, in my small way
[/INDENT][/INDENT]

---

### Post by jlh68 on 2013-11-23
OK, after some time I am back to the Grub2 situation.  Good News I was able to repair it.  The Application "Boot Repair" on my Rescutus flash drive would not work due to the onboard  WiFi manager on the flash drive, which would not work with my computer WiFi.  One night while updating some applications using Synaptic Packabe Manager, I found "Boot Repair" and downloaded it.  When I ran Boot Repair it worked fine with my computer WiFi manager, so I was able to purge the Grub and reinstall it using the Boot Repair application.

Thanks for all the help.  It looks like Boor Repair is a good program to have, I just wish I could get a different WiFi manager on the flash drive.  One that works.

---

### Post by Bashing-om on 2013-11-23
jlh68; Good job !

Wireless issues are not in the sphere of my interest.
Open a thread on that issue and see what those who know can advise.

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

