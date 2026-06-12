---
title: "Broken boot when drives swapped. Long(sorry)."
date: 2017-12-28
forum: General Help
---

### Post by Steve Goodey on 2017-12-28
Hello, I wonder if someone can help with a boot problem I have.

On an ASUS Z97I-Plus motherboard I have a SSD with Mythbuntu 16.04 installed with a SATA hardrive with recordings on.

This is working OK. I wanted to also have a seperate SATA harddrive with Xubuntu 16.04 installed with a Mythtv 29 built from source so I could play with patching files on the Mythtv built from source, leaving the Mythbuntu as a working system.

So I shut down the PC, unplugged the SSD and the recordings harddrive, and then used the SSD connectors for the Xubuntu SSD. Installed Xubuntu and built Mythtv 29 from source OK. 

Swapping the connectors back, now using Mythbuntu SSD and with the recordings harddrive connected the thing wouldn't boot, just a flashing cursor. To cut a long story short, I ran the Xubuntu Live CD and used boot-repair to fix things. The log at [https://paste.ubuntu.com/26272284]("https://paste.ubuntu.com/26272284") says no boot loader is installed in the MBR of /dev/sda. libparted MBR boot code is installed in the MBR of /dev/sdb.

The SSD has:-

/dev/sda1
Boot files: 
/EFI/ubuntu/grub.cfg /EFI/Boot/bootx64.efi 
/EFI/ubuntu/fwupx64.efi /EFI/ubuntu/grubx64.efi 
/EFI/ubuntu/mmx64.efi /EFI/ubuntu/shimx64.efi

/dev/sda2
Boot files:        /boot/grub/grub.cfg /etc/fstab

/dev/sda3 swap

/dev/sdb1
Boot files:

=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s    use-standard-efi-file

Adding boot menu entry for EFI firmware configuration
Unhide GRUB boot menu in sda2/boot/grub/grub.cfg

Boot successfully repaired.

And now Mythbuntu boots and is working fine.

So, was I asking for trouble doing what I did and can someone explain what went wrong and is there a simple way I can do what I want without breaking boot?

If I do this again will boot-repair work OK or was I lucky this time?

Thanks, Steve.

---

### Post by oldfred on 2017-12-28
Typically with UEFI, when you disconnect a drive, the UEFI entries to boot from that drive are lost.
You can probably just recreate with efibootmgr or reinstall grub.
But with new installs in UEFI mode grub only installs into the ESP - efi system partition that is on drive seen as sda.
Not sure if Boot-Repair on reinstalling grub, would install to HDD or just install to SSD, but may depend on which drive is sda?
You may have boot of both drives on drive seen as sda.

In ESP (default mount in fstab is hidden on drive you boot from), you should have a 3 line grub.cfg which configfile (chain) to full grub.cfg in the default install. Then grub should find all other installs and let you boot them. But only install in sda is UEFI boot unless otherwise changed.

When I put a new install in gpt7, it changed my default working system, so I changed it back.
```
#search.fs_uuid ca42543c-3a2e-4465-99b9-b9159d96ae7d root hd0,gpt7 
search.fs_uuid 255a2800-b871-4fdf-a809-16987e64b8b3 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

---

### Post by Steve Goodey on 2017-12-29
oldfred, thanks for your quick reply.

Steve.

---

