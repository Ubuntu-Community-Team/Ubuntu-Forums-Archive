---
title: "Booting via Grub2 on System built on  Logical Volumes (LVM)  - IEF if that matters."
date: 2020-07-19
forum: General Help
---

### Post by AnotherBrian on 2020-07-19
I cant find any help on booting from grub2.  

This is  a uefi system with 3tb sata drive connected via usb.  

I boot and get grub2.  

ls returns the following: 

(lvm/ubuntu--vg-swap_1) (lv/ubuntu--vg-root) (hd0) (hd0.gpt2)  (hd0.gpt1).   


I don't know the release - maybe 16.04, 17.10 18.04?  

What do I need to do or please point me to documentation.  I haven't found this situation documented.  

Thanks.

---

### Post by oldfred on 2020-07-19
I do not know LVM.

But you need a current version live installer of Ubuntu and can run Boot-Repair to see details of install.
If also encrypted, you need to mount the encrypted / before running Report.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by AnotherBrian on 2020-07-20
thanks for the  reply! 

Here are the results: [https://paste.ubuntu.com/p/DNMQQjBQcz/](https://paste.ubuntu.com/p/DNMQQjBQcz/) 

this was the configuration I ran boot-repair: 

booted on a dell latitude nvme system with boot-repair installed.  (so not by liveusb). 
the damaged boot is on a usb drive which is shown as ST3000 under sda. 

thanks for giving an opinion.

---

### Post by AnotherBrian on 2020-07-20
ok - this time i did it from liveusb to get this pastebin:  
[https://paste.ubuntu.com/p/57mf24vYch/](https://paste.ubuntu.com/p/57mf24vYch/)

last line it states: 
The default repair of the Boot-Repair utility would not act on the boot.I take it I'm am out of the scope of boot-repair.

---

### Post by oldfred on 2020-07-20
You have some old entries in UEFI boot menu that will not work. And an old BIOS boot version of grub in MBR of sdb. It looks like your internal drive got renumbered to sdb, and live installer became sda. My system often does that also.

```
Boot0000* Windows Boot Manager    HD(2,GPT,d5ed97d3-6089-49aa-902e-7e5ddcafbbe4,0xfa000,0x31800)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0002* ubuntu    HD(1,GPT,231006f4-92ca-4be4-99c6-32a692be9117,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* UEFI: KingstonDT Rubber 3.0 PMAP, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(17,0)/HD(1,MBR,0x15f006ae,0x406eb0,0x1f00)..BO
Boot0008* ubuntu    HD(1,GPT,[COLOR=#ff0000]afe9f099-9007-47f7-a65c-188d0ed38787[/COLOR],0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)

sdb1                vfat        6036-2BC5                              [COLOR=#ff0000]afe9f099-9007-47f7-a65c-188d0ed38787[/COLOR]

```

From report or these commands. To see GUID which is also called partUUID.
sudo efibootmgr -v
lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint,partuuid

UEFI has to see GUID to know which ESP - efi system partition to boot from. 
Best to delete old Windows 0000 & old Ubuntu entry 0002 in UEFI, so you are choosing correct ubuntu entry. UEFI boot menu usually does not show details, so often difficult to know which is correct entry.

Also make sure you are booting with UEFI, as grub in MBR will not work, unless you had reinstalled grub in BIOS boot mode.
Report did not show fstab which would have mount of ESP if UEFI boot. You may not have mounted LVM before running report as you have to have it mounted (& decrypted if encrypted) for report or repairs to work.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

Delete old UEFI entries & boot correct ubuntu. If still issues, rerun Boot-Repair, but be sure to mount LVM first.

Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

---

