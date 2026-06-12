---
title: "Questions viz. UEFI enabled post Ubuntu Mate installation while the Partitioning is s"
date: 2020-03-29
forum: General Help
---

### Post by Saptarshi_Roy on 2020-03-29
Question: Questions viz. UEFI enabled post Ubuntu Mate installation while the Partitioning is still MBR

Hi!


If 'UEFI Boot Support' is enabled in BIOS (was previously disabled) and if the 'Partitioning' is still 'MBR' then:


1. Would the OS boot?
2. If it boots, would there be any performance improvement?
3. Are there any potential complications that one should be aware of?

Thanks!

---

### Post by TheFu on 2020-03-29
1.  it depends on the hardware and BiOS.  I’ve not had any issues using UEFi boots to MBR disks.  The normal problem with that is for MS-Windows, which decided that UEFi boots would require GPT on their 64-bit OS, so some computer/MB vendors only support that mode and ignored the standards.
2. Depends. UEFi can provide fresh firmware for different chips on the MB and for the CPU that otherwise would need a to be re-flashed the old-school way we did it in 2005 - from a boot floppy/usb flash drive running MS-DOS or FreeDOS.
3. Yes, but really going with GPT should be the default these days.

---

### Post by Saptarshi_Roy on 2020-03-29
Thank you. Considering Ubuntu MATE is the only OS on this PC and there's no intent of using another OS in conjunction with this one, would you recommend keeping the 'UEFI BOOT Support' as 'enabled' or 'disabled'?

---

### Post by TheFu on 2020-03-29
> **Saptarshi_Roy said:**
> Thank you. Considering Ubuntu MATE is the only OS on this PC and there's no intent of using another OS in conjunction with this one, would you recommend keeping the 'UEFI BOOT Support' as 'enabled' or 'disabled'?

It depends. There are very good reasons to choose either BIOS/UEFI, but understand that the OS must be installed in the mode you choose and configure. Switching isn't really possible later. At least that's what I believe.

The Linux Foundation workstation security standards say to go with UEFI boot + secure boot.  There are times when that prevents some handy capabilities last, however.  Just depends on the sort of user/admin/tweaker you are.  I don't know that, so cannot make a suggestion and you cannot write the 20 pages to explain all the things you do (and don't do) here which would be needed to have the background for a good answer.
[https://www2.thelinuxfoundation.org/ebook_workstation_security](https://www2.thelinuxfoundation.org/ebook_workstation_security)

Sorry.

---

### Post by Saptarshi_Roy on 2020-03-30
Thank you TheFu.

---

