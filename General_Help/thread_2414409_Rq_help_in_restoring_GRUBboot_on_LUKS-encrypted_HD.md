---
title: "R/q help in restoring GRUB/boot on LUKS-encrypted HDD (Ubuntu 18.10)"
date: 2019-03-10
forum: General Help
---

### Post by ApolloSoyuz1975 on 2019-03-10
Hello - I have managed to mess up the boot configuration on my notebook's SSD while creating a bootable Puppy Linux USB stick.  When booting, the PC winds up loading a GRUB rescue prompt.  I have an Ubuntu live CD available, and I found out how to use boot-repair to create a boot info listing, which is as follows: [https://paste.ubuntu.com/p/h7jQTBG8nT/](https://paste.ubuntu.com/p/h7jQTBG8nT/)

I have the encryption passphrase for the HDD, so I basically need instruction in the successful access of the partition(s), along with instruction in repairing GRUB/any other boot configuration... however, even after looking up info on this problem, I'm still very nervous about screwing something up, and I apologize in advance for all the hand-holding that I will need!

---

### Post by oldfred on 2019-03-10
I do not know LVM.
But your fstab shows the mounting of /boot from sda1 and you have no sda1.
And your system is showing MBR partitions, so not UEFI, but older BIOS type install.

You need to create a new ext2 partition at beginning of drive, it may not be sda1, but that is not critical. What is critical is that fstab have same UUID as UUID of new partition and new partition will create a different UUID. So after you create new /boot, edit fstab in your install to have same UUID.
Then you can use Boot-Repair and its advanced options to totally reinstall grub and also check to add latest kernel. With Boot-Repair you probably have to manually mount the LVM to give your passphrase. If not Boot-Repair will not mount / inside your LVM/encrypted volume and that must be mounted for it to be able to fix it.

Did you already run Boot-Repair or manually comment out the /boot? As your /boot is commented out. You need to remove # and change UUID.
       ```
 # /boot was on /dev/sda1 during installation
[COLOR=#ff0000]#[/COLOR]UUID=[COLOR=#ff0000]1be5f2be-cee5-45c2-a99c-0fd6b16c9cb8[/COLOR] /boot           ext2    defaults        0       2 

    
```
To see UUID of new partition:
lsblk -f
Copy that UUID into fstab.

Note this from Boot-Repair:
       You may want to retry after decrypting your partitions. ([https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory))

---

### Post by ApolloSoyuz1975 on 2019-03-10
> **oldfred said:**
> I do not know LVM.
But your fstab shows the mounting of /boot from sda1 and you have no sda1.
And your system is showing MBR partitions, so not UEFI, but older BIOS type install.
Thanks for your reply.  As you note, this is an older PC with a BIOS; my accidental deletion of the sda1 partition is the root of this mess.

> **oldfred said:**
> You need to create a new ext2 partition at beginning of drive, it may not be sda1, but that is not critical. What is critical is that fstab have same UUID as UUID of new partition and new partition will create a different UUID. So after you create new /boot, edit fstab in your install to have same UUID.
Then you can use Boot-Repair and its advanced options to totally reinstall grub and also check to add latest kernel. With Boot-Repair you probably have to manually mount the LVM to give your passphrase. If not Boot-Repair will not mount / inside your LVM/encrypted volume and that must be mounted for it to be able to fix it.
I've just used gparted to create a new ext2 partition on the SSD, including the -boot flag during formatting. 

> **oldfred said:**
> Did you already run Boot-Repair or manually comment out the /boot? As your /boot is commented out. You need to remove # and change UUID.
       ```
 # /boot was on /dev/sda1 during installation
[COLOR=#ff0000]#[/COLOR]UUID=[COLOR=#ff0000]1be5f2be-cee5-45c2-a99c-0fd6b16c9cb8[/COLOR] /boot           ext2    defaults        0       2 

    
```
To see UUID of new partition:
lsblk -f
Copy that UUID into fstab.
I'm currently trying to work out the proper decryption of the disk so that I  can edit fstab to match your input.  I've not used boot-repair to  attempt an automated repair, but I have used it to create the following  update to my boot info summary: [https://paste.ubuntu.com/p/KJZpZYgXH5/](https://paste.ubuntu.com/p/KJZpZYgXH5/)

---

### Post by oldfred on 2019-03-10
Boot-Repair printed blkid. Line 82 shows /boot, new UUID.
      ```
 /dev/sda1        d6071f82-80a0-4100-873d-bbe725896e6b   ext2       


```    

So did you give passphrase to run report, but it wants it decrypted again to make repairs?
The grub.cfg in your install shows no kernels which would be correct since /boot has no files. 
Only use Advanced mode as you need a full reinstall of grub and the new kernel options.

---

