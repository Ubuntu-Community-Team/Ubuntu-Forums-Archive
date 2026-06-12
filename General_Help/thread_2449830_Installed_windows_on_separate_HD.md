---
title: "Installed windows on separate HD"
date: 2020-09-02
forum: General Help
---

### Post by livelyc on 2020-09-02
Forgive me if this is the wrong place for my question,  but I'm having an issue after installing Windows 10 on a separate SSD after linux was configured on another drive.

I needed Windows to be able to participate in my online classes this semester and My machine which I've had configured to run Ubuntu 20.04 from an NVMe drive, has a second SSD that was unused.  I installed Windows on the second SSD thinking that I could just manually boot into the drive that already had Ubuntu installed on it, then run update-grub and be in business with a prompt to load Ubuntu or Windows.  Not so fortunate.  my machine simply refuses to boot from the drive that has Ubuntu already installed.  

Do I need to reinstall Ubuntu on the NVMe drive from scratch in order for grub to see that there are two drives one with windows and one with Ubuntu? or is there a way to correct this with a live image?

---

### Post by oldfred on 2020-09-02
Grub only boot working Windows.
And that means Windows default setting of fast start up must be off as it sets hibernation flag. Note that Windows keeps turning this back on with updates.

Are both systems installed in UEFI boot mode?

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

