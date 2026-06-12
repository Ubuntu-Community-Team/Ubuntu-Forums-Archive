---
title: "xenial dead after booting off external drive with bionic"
date: 2018-04-30
forum: General Help
---

### Post by monkeybrain20122 on 2018-04-30
xenial is dead on one of my laptops and bionic appeared to have killed it. 

I installed bionic in an external hd and boot it off on my Toshiba labtop (with xenial installed) for testings. I have done this kind of operations many times and never had a problem. But today after shutting down bionic and removing the external hd, I can't boot into xenial anymore.

When I hit the power button, the toshiba logo appeared and then black screen, there was no error (not even grub-rescue) and I couldn't start the grub menu by pressing/tabbing esc, just nothing. Normally this thing booted in 5 secs with 16.04 but now there was nothing forever.

 I thought it might be hardware, maybe the hd died or the mobo was fired, but I could got into bios so maybe it wasn't completely dead. Then I found out  I could boot a bionic live usb and access the files in xenial's home. So it was not dead yet. After saving all my files I thought I had  nothing to lose so I just reformatted the drive and tried to install Bionic in it. I didn't expect it to work, but it did and now this machine is running Bionic quite smoothly. so hardware was ok all along.

I didn't plan to install Bionic so soon after it is released, but it is almost like it murdered xenial so it could get ahead...A murder mystery!

Does anyone have a theory what might have happened? 

Thanks.

---

### Post by Irihapeti on 2018-04-30
Might you have installed GRUB to the external HD?

---

### Post by monkeybrain20122 on 2018-04-30
> **Irihapeti said:**
> Might you have installed GRUB to the external HD?

No, I should add that this is not the first time I booted after installing bionic on the external drive. I have booted between the internal and external drives several times before this happened. Moreover if grub is missing you'll get a blanking grub-recue prompt instead of a black screen.

---

### Post by Irihapeti on 2018-04-30
If you're running MBR partitioning and GRUB has been installed to the MBR of the external drive, then once it's removed, there's nothing to create a grub-rescue> prompt.

I'm not that familiar with the UEFI system (yet), but I imagine that if the EFI partition is on the external drive, something similar might happen.

---

### Post by monkeybrain20122 on 2018-04-30
> **Irihapeti said:**
> If you're running MBR partitioning and GRUB has been installed to the MBR of the external drive, then once it's removed, there's nothing to create a grub-rescue> prompt.

I'm not that familiar with the UEFI system (yet), but I imagine that if the EFI partition is on the external drive, something similar might happen.

It is mbr, but it is impossible that grub has been overwritten because I have booted into xenial many times after I installed bionic in the external drive **and with the external drive removed**.

---

### Post by Irihapeti on 2018-04-30
It looks like it's not the problem. Still, it was worth ruling out.

Hopefully, someone else can provide a more useful explanation.

---

### Post by monkeybrain20122 on 2018-04-30
Wonder if it is possible that the file system (in the internal drive) somehow got corrupted because of a faulty usb port which I connected the external drive to. I remember when I plugged the bionic live usb the second time to recover my data it wouldn't boot from that port and I had to plug it into another one.

---

### Post by ajgreeny on 2018-04-30
Running the Boot-info script from my signature below should tell us what is going on here, where grub really is, and what you can do to get everything up and running as you want.

Do not run the default repair until we have seen the script output which you can link to with the Pastebin link which you will see after running the script.  Let us see that output and someone will get back with recommendations, I am sure.

---

### Post by monkeybrain20122 on 2018-04-30
> **ajgreeny said:**
> Running the Boot-info script from my signature below should tell us what is going on here, where grub really is, and what you can do to get everything up and running as you want.

Do not run the default repair until we have seen the script output which you can link to with the Pastebin link which you will see after running the script.  Let us see that output and someone will get back with recommendations, I am sure.

There is no problem now, I have wiped the hd and installed Bionic and it is very smooth, hence "I didn't plan to install Bionic so soon after it is released, but it is  almost like it murdered xenial so it could get ahead...A murder mystery!." 

I just wonder what happened (past tense) and hopefully can learn something and prevent it from happening again.

---

### Post by yancek on 2018-04-30
The best thing that could have been done to try to resolve the problem would have been to run the boot repair software with the Create BootInfo Summary option.  This outputs a link which shows very detailed information on your drives/partitions and boot files.  If both systems were MBR, it would have been best to install Grub to the MBR of the external allowing you to boot it from another machine.  You should also have been able to run sudo update-grub on both systems and get entries for 16.04 and 18.04.  If both were EFI, creating and EFI partition on the external would have kept them separate and bootable also.  If you were able to boot both initially and then could no longer do so adds a complicating factor.  Good luck with the new system.

---

