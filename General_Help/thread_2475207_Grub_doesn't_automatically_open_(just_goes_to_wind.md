---
title: "Grub doesn't automatically open (just goes to windows directly)"
date: 2022-05-19
forum: General Help
---

### Post by poxeled on 2022-05-19
Grub doesn't automatically open unless i go to the "boot options" in the bios and select ubuntu, I also copied a "boot repair" thing

[FONT=monospace][COLOR=#000000]boot-repair-4ppa200                                              [20220519_1404] [/COLOR]

============================== Boot Info Summary =============================== 

 => No boot loader is installed in the MBR of /dev/sda. 

sda1: __________________________________________________________________________ 

    File system:       vfat 
    Boot sector type:  Windows 8/10/11/2012: FAT32 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:   
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi  
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi  
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi  
                       /efi/ubuntu/grub.cfg /efi/HP/BIOSUpdate/BiosMgmt.efi  
                       /efi/HP/BIOSUpdate/CryptRSA32.efi  
                       /efi/HP/BIOSUpdate/CryptRSA.efi  
                       /efi/HP/BIOSUpdate/HpBiosMgmt.efi  
                       /efi/Microsoft/Boot/bootmgfw.efi  
                       /efi/Microsoft/Boot/bootmgr.efi 

sda2: __________________________________________________________________________ 

    File system:        
    Boot sector type:  - 
    Boot sector info:  
:


Edit: I also get the following message when I select "Recommended Repair"

"Please use this software in a live-session (live-CD or live-USB). This will enable this feature." [/FONT]

---

### Post by oldfred on 2022-05-19
HP often requires you to go into UEFI settings (not menu) and change boot order there. You should be able to always boot either system from UEFI boot menu.

Both systems must be in UEFI boot mode, which it looks like you have since you have both Windows & Ubuntu/grub boot files in ESP. 

Many HP also need UEFI firmware update.

---

