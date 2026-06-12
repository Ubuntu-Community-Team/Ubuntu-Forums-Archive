---
title: "Ned help with BIOS"
date: 2015-02-07
forum: General Help
---

### Post by john359 on 2015-02-07
I am having somewhat of a complicated issue. A while back I made a partition on my hard drive to install Ubnuntu alongside Windows 8. I had a load of trouble doing this, i had an issue with the GRUB menu showing up to boot into Ubuntu so i had to disable fast startup in Windows but it didnt show up still. I found a website telling me to do about 15 minutes of just crazy CMD commands and it eventually worked, i got the menu to pop up. I now wanted to move Ubuntu to a separate hard drive on my computer. I deleted the partition Ubuntu was on, i have yet to put Ubuntu on the other drive because my BIOS won't come up. I clicked the del key when it asks but my screen turns black and nothing will happen. Thank you.

---

### Post by v3.xx on 2015-02-08
> I found a website telling me to do about 15 minutes of just crazy CMD commands
What website?

Here's a forum link to efi.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=efi+uefi&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=efi+uefi&sa=Search&cof=FORID:9)

---

### Post by oldfred on 2015-02-08
Is system UEFI or BIOS?
If BIOS you have to install a Windows boot loader before deleting Ubuntu.

Some system have a Windows fast boot, but also have an UEFI fast boot. And then the UEFI does not recheck hardware or for any changes, but reboots as if nothing has changed. Often then a full cold boot or turn off power, remove battery if a laptop and hold power switch for 10 sec or so to drain any remaining power. Then you should be able to use correct key to get into UEFI/BIOS.

---

### Post by john359 on 2015-02-08
It Is UFEI

---

### Post by oldfred on 2015-02-09
If system is UEFI, you should be able to just go into UEFI menu and boot Windows or use one time boot key.

Only if you ran an old version of Boot-Repair where its "buggy" UEFI fix was a rename of the Windows efi file might you not be able to boot from UEFI menu. And then you just need to rerun Boot-Repair now or run Windows fixes from a Windows repair flash drive.

---

