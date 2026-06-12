---
title: "Correct way to recreate EFI entry after bios reset?"
date: 2019-11-01
forum: General Help
---

### Post by Krause on 2019-11-01
I have Ubuntu and Pop OS (Ubuntu based) installed on 2 different systems and after resetting the bios on them, the named "Ubuntu 19.10" or "Pop!_OS 19.10" boot entries are gone, and do not get recreated at first boot again like windows will with its boot manager (they still boot fine because the bootloader is installed right to the base NVMe drive, not a custom location so simply booting to the drive boots the OS).

After a few different things I came across recreating it with bootctl:
```
sudo bootctl --path/boot/efi install
```

And it creates an EFI entry, but  its a generic "Linux Boot Manager" entry. Still works though.

Is there a better way to do this that names it properly like the OS does on first install? Ive tried efibootmgr quickly to create one since that seems to have a custom label switch, but it was giving me trouble with the "Pop!_OS 19.10" name because even in quotes it didn't like the "!" so im not sure that was what was used to create it to begin with.

Anyone have a better way to do this that recreates the same entry that was made when installing, aside from ridiculously backing up the drive, reinstalling fresh, then wiping it and restoring the drive image?

Thanks!

---

### Post by oldfred on 2019-11-01
You should be able to use efibootmgr or you can do a full reinstall of grub which uses efibootmgr to create new UEFI entry.

To see current entries:
sudo efibootmgr -v 

Commands details:
man efibootmgr

Default is first drive, partition or sda. If any other partition is ESP, you must be explicit. 

sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.
If NVMe:
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

The switches and options state: -c create new entry on -d disk, on -p partition, -w write unique signature into MBR if needed, and use -L label to mark the new entry. You can use any label you want. The partition number must match your ESP. 

If you have old entries remove them.
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Wth Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B

---

### Post by Krause on 2019-11-01
> **oldfred said:**
> You should be able to use efibootmgr or you can do a full reinstall of grub which uses efibootmgr to create new UEFI entry.

To see current entries:
sudo efibootmgr -v 

Commands details:
man efibootmgr

Default is first drive, partition or sda. If any other partition is ESP, you must be explicit. 

sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.
If NVMe:
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\shimx64.efi" -d /dev/nvme0n1 -p 1

The switches and options state: -c create new entry on -d disk, on -p partition, -w write unique signature into MBR if needed, and use -L label to mark the new entry. You can use any label you want. The partition number must match your ESP. 

If you have old entries remove them.
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Wth Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
Thank you! That worked!

Any idea how I can use a "!" in the label name?

When I use "Pop!_OS 19.10" it says:
```
bash: !_OS event not found
```

I could of sworn they had it written like that before i reset the bios on the Pop os installed machine.

[edit]

got it, need to use single quotes to make bash ignore it so instead of
"Pop!_OS 19.10" I used 'Pop!_OS 19.10' and it worked!

---

