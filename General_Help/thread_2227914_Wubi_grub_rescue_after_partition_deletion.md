---
title: "Wubi grub rescue after partition deletion"
date: 2014-06-04
forum: General Help
---

### Post by Rylux on 2014-06-04
Hi, everyone, I installed ubuntu 14.04(originally 12.04) with Wubi in addition to my Win 7, I had to use a boot rescue thing to being able to boot on both of them, and it worked fine. recently, i've deleted a small unallocated partiton, and integrated it to y main part, and I fall in grub rescue with the line unknown filesystem. I've tried many ways to fix it: with Super Grub disk (reuturned error 15) with boot rescue (here is the log: [http://paste.ubuntu.com/7589009](http://paste.ubuntu.com/7589009)) and i'm still on grub rescue, i used "ls" on all my partition and it retruned "filesystem is unknown" each time. I have booted on a ubuntu secure live USB 13.04 and I saw that i can reinstalle grub on my main part. I wanted to know if this is the best solution, and if i will loose all my data( i've got a really important project i must acesss on my wubi disk) Can someone with more knowledge please help me?

---

### Post by monkeybrain20122 on 2014-06-04
Wubi is dead, it has always been more of a "try it out" gimmick back in the days when Ubuntu was completely unknown than a serious way to use Ubuntu. Ubuntu is not a Windows application and not meant to be installed inside Windows. Please do a real install by giving Ubuntu its own partition.

---

### Post by oldfred on 2014-06-04
You have Windows booting in UEFI mode from a gpt partitioned drive.
But wubi does not work from a gpt partitioned drive. Because of that, the last supported version of wubi is 12.04. It is available it you want to install it but since it does not work easily on any new computer you are totally on your own.

And you now have grub installed in UEFI mode? Not sure how?
And you installed grub to sdb, which looks like your flash drive installer, which would have syslinux not grub in MBR. And you should grub legacy in the sdb drive?

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Because you have Windows 7 you will not have any secure boot, or fast boot issues. But may have hibernation which should be off.

---

### Post by Rylux on 2014-06-04
I don't undestand everything you said... 
I don't know what sdb or grub leagcy is... if i thnk right MBR is the first part be read in the hard drive, right? 
and when it worked, I was able to start Linux but not Windows directly, i had to boot a "Windows UEFI Loader"  which loaded 7...

---

### Post by oldfred on 2014-06-04
If  you turn UEFI on or choose the UEFI Windows boot loader it still should work.
But wubi should not.

---

### Post by Rylux on 2014-06-04
UEFI is turned on in my BIOS, I neverd changed it. I tried to start Win UEFI loader, and had grub rescue saying "No such device"

---

### Post by oldfred on 2014-06-04
Are you sure you are booting from sda, not the external drive which now seems to have grub?
You may have USB drive as first in boot order.
Or you should have a one time boot key, often f12 but varies by vendor to let you choose what to boot without going fully into UEFI/BIOS.

---

### Post by Rylux on 2014-06-04
I only boot on the key, i override boot at each start, i can't boot on sda, I get grub error

---

### Post by oldfred on 2014-06-04
Missed that you ran the 'buggy' UEFI fix from Boot-Repair. That replaces the Windows boot file with grub and renames Windows to be a bkp file.

       /EFI/Microsoft/Boot/[COLOR=#ff0000]bkp[/COLOR]bootmgfw.efi

You need to use Boot-Repair and undo the rename.

      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by Rylux on 2014-06-05
Mmh this should put Windows UEFI  loader working right? But he can't run my Wubi part...

---

### Post by oldfred on 2014-06-05
wubi does not work with gpt partitioned drives. You have to use Windows tools to shrink the NTFS partition. Then install Ubuntu into the unallocated part.
If the installer does not say it sees Windows, only use Something Else or manual install.

       Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)


 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by Rylux on 2014-06-05
Wubi worked before, and i don't think i had changed the gpt partitons stuff, my hard drive have always benn like that, I also have files i need on my Wubi disk

---

### Post by Impavidus on 2014-06-05
The wubi disk is a file named root.disk located somewhere on an ntfs partition. You can create a backup of that file, store it somewhere else, whatever. Using an Ubuntu live disk or an installed Ubuntu (or any other Linux for that matter) you can mount the root.disk file as an ext4 file system and extract your files from it.

---

### Post by Rylux on 2014-06-05
I mounted the file, but the home folder is empty

---

### Post by Rylux on 2014-06-05
I saw this post: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
Do you think the solution 2 for the first problem should work?

---

### Post by Rylux on 2014-06-05
ok I restored EFI steetings and got Win UEFI working... I wanted to use a soft to explore my Wubi disk, and my home file is empty
where are my data?

---

### Post by oldfred on 2014-06-05
Do you have root.disk in your NTFS partition. Or did you save that?

Missing root.disk
[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
[http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted](http://askubuntu.com/questions/228709/ubuntu-12-04-wubi-not-starting-root-disk-corrupted)
How-to: Recover files from Wubi install with LiveCD
[http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)
[Script] Mount Wubi Disk from Linux mount old wubi in new install
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

---

### Post by Rylux on 2014-06-05
I have root.disk I opened it with Ext2exploer but my home polder is emmpty

---

### Post by oldfred on 2014-06-05
Many of those third party Linux tools in Windows do not work with ext4 format. 
Try using an Ubuntu live installer DVD or flash drive.
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Rylux on 2014-06-05
i  tried in live usb with root.disk mounted
the home folder is empty here too

---

