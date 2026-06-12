---
title: "Can i fix UEFI grub v2 with bios booted Ubuntu live cd?"
date: 2019-06-01
forum: General Help
---

### Post by levion62 on 2019-06-01
Hello I had my latest LTS installed on UEFI Mode past week Everythings were fine. Later i noticed i wasnt able to boot with literally anything via Usb drive  when  i was about to  boot into TAILS OS.  
 Then
Just unChecked secure boot option under grub software menu because i thought it has something to do with this. now it gives Grub rescue console even No rescue commands worked like setroot or setprefix as explained in instructions. It probably deleted some important files in /efi folder anyways Switched to live usb Today for hope i cant still boot via gpt partitioned Ubuntu live usb unless i am on CSM Mode. Now im trying to repair A uefi bootloader via normal bios booted Ubuntu live cd.... Boot-repair software already gives error like " while you have /efi partition do the process in UEFI mode" 

How i get things back to work?

---

### Post by oldfred on 2019-06-01
Most new UEFI systems have both Secure boot which restricts BIOS boot or external drive boot, but then another setting to allow USB boot or full USB access. You may need to allow USB boot in UEFI even with Secure Boot off.
Often updating UEFI will cause some settings to revert to defaults, so even if you changed settings before, best to double check.

---

