---
title: "No bootable devices found"
date: 2018-09-16
forum: General Help
---

### Post by freddie-breese on 2018-09-16
Hi, whilst trying to trying to solve another issue I made the mistake of trying to resize the boot partition on my system (running Ubuntu 18.04) without following due precautions. Since then when I power up my computer it gives me the message no bootable devices found. I ran the boot repair utility on a live usb and selected the recommended repair, but it hasn't fixed the problem. 
[http://paste.ubuntu.com/p/NhKtzn47dG/](http://paste.ubuntu.com/p/NhKtzn47dG/) here's the info summary when I ran this.
 I've run the dell system assessment and there are no hardware issues. I've tried all of the different boot options I can find in the bios options, with secure boot on and off etc.
These problems really are way over my head and any advice would be really welcome.
thanks

---

### Post by oldfred on 2018-09-16
I do not know LVM & encryption.
But I might try Boot-Repair again, but manually mount your LVM and unencrypt your encrypted volumes first from live installer, so Boot-Repair can see them correctly. That seemed to be the error.

---

### Post by freddie-breese on 2018-09-16
Hi, thanks a lot for your response. Looking back over the info summary I see exactly what you mean with the encrypted volumes, that being said I really don't understand why that would be a problem as the boots files are on sda1 and sda2 which aren't encrypted. I tried decrypting the disk manually whilst running off the rootrepair usb, but it produced a very similar output [http://paste.ubuntu.com/p/VmCt26xchc/](http://paste.ubuntu.com/p/VmCt26xchc/)
Having poked around a bit more it seems to me that the problem is with locating the efi partition on boot. I got a number of error messages related to it whilst trying to reinstall grub2 just as a shot in the dark. I checked the relevant file in /etc and both /boot and /boot/efi pointed to the correct locations for sda1 and sda2 so I'm no closer to finding a solution.
Looks like it could well be time just to cut my losses and have a new install

---

### Post by oldfred on 2018-09-16
When you install/reinstall grub it has to see / (root) as you have this line:
linux	/vmlinuz-4.15.0-34-generic root=/dev/mapper/ubuntu--vg-root ro  quiet splash $vt_handoff

So that is why / must be mounted on grub install or repair.

---

### Post by freddie-breese on 2018-09-17
Right, I tried reinstalling everything completely from a liveusb, but the new system still won't boot. On the new install I selected no encryption. When I run the boot repair drive I do now have access to some more options This is the output I now get [http://paste.ubuntu.com/p/zhFkj7M9sd/](http://paste.ubuntu.com/p/zhFkj7M9sd/)
I'm now totally out of ideas besides running the original dell restore drive I made when I first got the machine and hoping that fixes something

---

### Post by yancek on 2018-09-17
Boot repair shows that you have windows boot code in the MBR of your hard drive.  It also shows that you have EFI files for windows on sda1, your EFI partition but you no longer have any windows OS.  Is your BIOS set to use UEFI rather than Legacy/CSM.  If it is set to boot Legacy/CSM, it will look for windows files which do not exist.  If it is set to UEFI, you do have the correct Ubuntu EFI files on sda1.  Do you have an option in the BIOS or a specific key to select 'Boot Options' and if so, do you see an Ubuntu entry.  If you see this, then you need to select the option recommended in boot repair:

[QUOTEPlease do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!][/QUOTE]

The obvious question, after re-installing Ubuntu, you did remove the usb you used to install and change the boot option to boot from the HD, correct?

The efibootmgr output shows the following entry for Ubuntu:

> Boot0000* ubuntu	HD(1,GPT,046d394b-b55d-4722-9167-395a1d18559a,0x800,0x100000)/File(EFIubuntushimx64.efi)

The series of characters (32) immediately after GPT in that line is the UUID which is not the same as the UUID you see in /etc/fstab which is:

> UUID=b435b4d7-7c0a-4c87-821d-82ea407516cd /               ext4    errors=remount-ro 0       1

This UUID beginning with "b435**" is the same as the UUID in grub.cfg.  I'm not sure this is the problem nor exactly how to change it if it is so hopefully, oldfred will see this post as he has a lot more expertise.

---

### Post by freddie-breese on 2018-09-17
Hi there, to answer your questions
yes the bios is set to use UEFI
in the boot options there is an option to boot to ubuntu. when I select it the screen flashes for about 5 seconds before the no bootable devices found message appears.
And yes, unfortunately I did remove the install media and it is set to boot from the HD.

---

### Post by oldfred on 2018-09-17
The UEFI uses a GUID, and most of Ubuntu uses the UUID. The GUID is relatively new with gpt partitioning which is used with UEFI. Linux tools show the GUID as partUUID to avoid confusion with some other GUIDs include the GUID type of partition.
To see UUID & guid, the Boot-Repair report shows both under blkid section.
lsblk -f -o +partuuid

Your sda1 shows this:
```
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
```

Try this:
       Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

I recently had grub install or efibootmr throw an error. And UEFI would only boot my emergency boot drives, but not my  ESP - efi system partition. Ubuntu & grub would write into it normally so I did not think of repairing the file system with dosfsck or fsck.vfat which are the same.
But when I ran it, it did say it was clearing dirty bit. But on reboot UEFI still did not see ESP, only could use my backup boot. And re-running repair showed it clearing dirty bit again.
So I totally backed up all the folders & refomatted the partition. I totally uninstalled & reinstalled grub/shim and reconfigured it. And that worked.
UEFI seems to be more sensitive about the ESP and that is is correct.

So if dosfsck does not work you may need to reformat partition which will erase all data.
sudo mkfs.vfat -F 32 -t vfat /dev/sda1

---

### Post by freddie-breese on 2018-09-17
Okay, I ran sudo dosfsck -t -a -w /dev/sda1. It gave me the output fsck.fut 4.1 (2017-01-24) /dev/sda1: 15 files 1481/130811 clusters, but the problem is still there unfortunately. I'll try reformatting next
thanks a lot

---

### Post by oldfred on 2018-09-17
Since yours shows a start issue, I might backup & then totally delete partition. Then create new FAT32 partition with boot and esp flags. 
You have to update UUID for the /boot/efi mount of the ESP in fstab. Before reinstall of grub.
You then have to fully reinstall grub and reconfigure grub.

 sudo apt purge grub-efi-amd64  grub-efi-amd64-signed 
      
  sudo apt install shim-signed grub-efi-amd64-signed linux-signed-image-generic 
      
 sudo update-grub 

I then confirmed files were in /EFI/Boot & /EFI/ubuntu folders in the FAT32 partition.
I double checked that fstab had correct UUID.
Verified I have UEFI boot entries.
 sudo efibootmgr -v

When rebooting I first when into UEFI to see that it also showed the same UEFI boot entries and made sure Ubuntu entry was first.

---

### Post by freddie-breese on 2018-09-18
Thanks a lot for your help. When I have time later today I'll run through that and if it fails run the dell factory reset disk. When I install grub can I do that straight from the liveusb or will I have mount and chroot to the hard disk before?

---

### Post by oldfred on 2018-09-18
I had an emergency boot flash drive, actually several. 
One was rEFInd and others are full installs of Ubuntu with grub configured to allow me to easily specify boot if not in menu.
I believe Boot-Repair has you walk thru a mini-chroot that works to reinstall grub.

---

### Post by freddie-breese on 2018-09-18
Hi thanks for your help. I've followed your advice, deleted the old partition and created a new one with the correct flags. I'm now at the stage of updating grub, and I'm getting the error 
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'. I could try just running boot repair at this point?

---

### Post by freddie-breese on 2018-09-18
Got round this stage by mounting the efi partition and running sudo grub-install --recheck --root-directory=/mnt /dev/sda.
sudo efibootmgr -v gives me this output. I switched back to legacy mode because I was trying to get the dell recovery disk to work, but this output looks okay to me
BootCurrent: 0007
Timeout: 0 seconds
BootOrder: 0000,0001,0002,0006,0004,0005,0007
Boot0000* ubuntu    HD(1,GPT,da32080b-2d45-461d-8215-dca560e3199e,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Diskette Drive    BBS(Floppy,Diskette Drive,0x0)AMBO
Boot0002* Internal HDD    BBS(HD,P0: ST500LM000-1EJ162         ,0x0)AMBO
Boot0004* CD/DVD/CD-RW Drive    BBS(CDROM,CD/DVD/CD-RW Drive,0x0)AMBO
Boot0005* Onboard NIC    BBS(Network,IBA GE Slot 00C8 v1538,0x0)AMBO
Boot0006* USB Storage Device    BBS(USB,Generic Flash Disk 5.00,0x0)AMBO
Boot0007* UEFI: Generic Flash Disk 5.00    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x663eb4c4,0x3906b4,0x1240)AMBO

---

### Post by freddie-breese on 2018-09-18
I've rebooted and progress has finally been made. I set the system to UEFI secure boot on and it gives me two options from the BIOS
ubuntu
UEFI: STS00LM000-1EJ162.
Selecting either of these now leads straight to grub. Should I be able to fix this with a reinstall?

edit: boot-repair now gives me this output and seems to have fixed things. Thanks a lot oldfred for your expertise. There'd have been no hope for me by myself [URL="http://paste.ubuntu.com/p/2R9JmkZ6v9/"]http://paste.ubuntu.com/p/2R9JmkZ6v9/
[/URL]

---

### Post by oldfred on 2018-09-18
Glad that worked.
Boot-Repair probably also fixed fstab with correct UUID (or really the full reinstall of grub).

You can change to solved in case others have same issue and search forum.

---

