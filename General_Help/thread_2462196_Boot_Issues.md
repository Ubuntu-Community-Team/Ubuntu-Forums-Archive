---
title: "Boot Issues"
date: 2021-05-15
forum: General Help
---

### Post by heroquestelf on 2021-05-15
I have a Lenovo Thinkpad Flex3 1580 that's running Kubuntu 20.04. In fact, it's a brand new install. It even has a brand new Solid state hard drive in it. 

I **HAD** Kubuntu 18.04 on there, and I recently upgraded it because it was having boot up issues. Installing a new OS and a new Hard drive did not solve my issues. 

**LI****TERALLY **every other time I boot it up it freezes. I can't figure out what's going on. I hit the power button and the screen powers on, but nothing happens. It sits there until I hit the power button a second time and power the computer down. Then I hit the power button a second time and this time it boots up fine. But it literally does this every single time I go to boot it up and I am flummoxed. 

Every once in a blue moon I get an error code. Sometimes it will freeze at "Loading Initial Ram disk". 

and at one point, it generated this error:

```

 [ 0.274283] ACPI BIOS Error (bug): Failure creating named object [\_PR.CPUD.TPSS],AE_ALREADY_EXISTS {20200528/download2-S26}
 [ 0.274200] ACPI Error: AE_ALREADY_EXISTS, During name lockup/catalog {20200528/psobject220}
  [ 0.399408] platform MSFT0101:00: failed to claim resource 1 [mem 0xfed40000-0xfed40fff]
  [ 0.399416] acp1 MSFT0101:00: platform device creation failed: -16
  
```

any idea what might be going on?

---

### Post by VMC on 2021-05-15
Show output of this command:
```
sudo parted -l
```

---

### Post by heroquestelf on 2021-05-15
```

Model: ATA WDC WDS500G2B0A (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start     End      Size       File system  Name                       Flags
1           1049kb  538MB  537MB   fat32          EFI System Partition  boot, esp
2           538MB   500GB  500GB   ext4

```

sorry about the formatting... i'm copying this from one computer to another.

---

### Post by oldfred on 2021-05-15
What model Thinkpad?
Have you updated UEFI and SSD firmware?

Lenovo ThinkPad E595  re-installed & then it worked?
[https://ubuntuforums.org/showthread.php?t=2454063](https://ubuntuforums.org/showthread.php?t=2454063)
Lenovo ThinkPad X1 Extreme 2019 UEFI settings required.
[https://askubuntu.com/questions/1291280/after-running-boot-repair-and-disabeling-secure-boot-still-not-booting-to-grub](https://askubuntu.com/questions/1291280/after-running-boot-repair-and-disabeling-secure-boot-still-not-booting-to-grub)

---

### Post by heroquestelf on 2021-05-15
Sorry, it's a Flex 3 1580. 

I went into the Boot menu and made sure that Secure boot was turned off--and it was, and I also changed the boot order because the boot from USB option was higher than the actual hard drive... but I don't know why that would matter because "Ubuntu" was still at the top of the list.

Either way, that seems to have cured the problem because now It's loading normally.

---

