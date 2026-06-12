---
title: "Boot problems/data recovery"
date: 2017-10-27
forum: General Help
---

### Post by shain on 2017-10-27
I am trying to recover data from my encrypted home folder on a Xubuntu machine. My goals are to either repair the boot to access my data normally so I can back it up or to recover the data within the encrypted home folder some other way.

The boot:
I think I messed up somewhere when I installed linux. The first boot after install worked great. When I rebooted several days later, it wouldn't boot up. 
```
Reboot and select proper Boot device
or Insert Boot Media in selected Boot device and press a key
```
I believe that I either did or didn't use efi boot when I should have done the opposite. I remember having made this same mistake before, and the solution was to reinstall with different boot settings. I don't want to reinstall until I rescue the data on the machine. 
I tried to run boot-repair-disk, but it didn't work when I rebooted. Here is the paste dump it gave me. 

[http://paste.ubuntu.com/25833186/](http://paste.ubuntu.com/25833186/)

The data:
I didn't set up my passphrase for my encrypted home folder during the first boot, so I don't know how to recover the protected home folder. Is there anything I can do?

Can you please help?

---

### Post by oldfred on 2017-10-28
No, the entire purpose of encryption is to prevent anyone who does not know pass phase from accessing data.
You had to have given a pass phase to install. Do not know if it lets you use login as phase or not, never used LVM with Encryption.

And if you are going to use encryption, you must have very good backups.
The encryption only prevents access when booting system, once booted all data is then accessible to anyone using the system.

Boot-Repair cannot fix install as you also have to mount / (root) which is inside the encryption. It has to be mounted using pass phase.
But UEFI is not showing an ubuntu entry. See this part:
sudo efibootmgr -v

What brand/model system?
Some need Boot-Repair to copy shimx64.efi to boot the fallback entry. 
Or since only booting Ubuntu we can rename entry to "Windows Boot Manager".
       
 **d1**:  If Description has to be Windows then change UEFI description, and then boot "Windows" which really now is shimx64.efi to boot Ubuntu. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

But you will not boot without pass phrase.

---

### Post by shain on 2017-10-28
I can mount the encrypted drive just fine. I just cannot log into the account to access the home folder. I will try your boot method. If I can boot into this install, I can access my data.

---

### Post by shain on 2017-10-28
The computer is a Toshiba Satellite. I am not sure what you mean what brand. I am installing xubuntu. Why wouldn't boot repair copy that when I ran it? Will it not repair a non-functioning boot from a live session?

When I ran efibootmgr -v, I got ```
BootCurrent: 0003
Timeout: 0 seconds
BootOrder: 0000,0006,0002,2003,2001,6F08,5F96
Boot0001* UEFI: IP6 Realtek PCIe FE Family Controller    PciRoot(0x0)/Pci(0x1c,0x
2)/Pci(0x0)/MAC[MAC],0)/IPv6([::]:<->[::]:,0,0)..BO
Boot0002* UEFI: IP4 Realtek PCIe FE Family Controller    PciRoot(0x0)/Pci(0x1c,0x
2)/Pci(0x0)/MAC[MAC],0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)..BO
Boot0003* UEFI: PNY USB 2.0 FD PMAP     PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/USB(
1,0)(HD(1,MBR,0x4294967228,0x800,0x3503800)..BO
Boot2001* EFI USB Device      RC
Boot2003* EFI Network   RC
```

> Or since only booting Ubuntu we can rename entry to "Windows Boot Manager"Rename which entry?
> **d1**:  If Description has to be Windows then change UEFI  description, and then boot "Windows" which really now is shimx64.efi to  boot Ubuntu. Assumes ESP is sda1. I don't understand this. I am not sure what you are referring to that it has to be windows. If you are referring to the dump, I put it here because I don't know what to make of it or what it contains.

---

### Post by oldfred on 2017-10-28
Some brands like HP, Sony and some models of Toshiba violate UEFI standards. The standard says NOT to use description as part of UEFI boot, but they modify UEFI to check description when booting, and only valid description is "Windows Boot Manager".  
Multiple work arounds including using fallback entry for those dual booting, but if only booting Ubuntu we create an entry using the description UEFI wants (Windows), but actually uses the Ubuntu/grub/shim file to boot. They only check description, not actual file used to boot.

If you run the UEFI entry, it will create a Windows desription but Ubuntu boot file(shimx64.efi). Then when you boot "Windows" it will actually boot Ubuntu.

---

### Post by shain on 2017-10-28
> **d1**:  If Description has to be Windows then change UEFI  description, and then boot "Windows" which really now is shimx64.efi to  boot Ubuntu. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" Where do I do this?

---

### Post by shain on 2017-10-28
What if I picked the wrong setting when I installed it? What if I picked the other option than **UEFI install**? I remember that I had done that once before and that a reinstall fixed it to where it would boot every time on this machine. I didn't have to run a boot repair. However, this time I do not want to just reinstall over it. Is there a way to fix it or get it to boot just once?

---

### Post by oldfred on 2017-10-28
You have a UEFI install currently. Boot-Repair could convert to BIOS if you had a bios_grub partition. But it would need you to also mount the / (root) partition from inside your encrypted partition.

You just need to use Live Installer in terminal mode and copy & paste the efibootmgr command. That should update UEFI with an entry that will boot.
You can check that entry is added to UEFI:
sudo efibootmgr -v

---

