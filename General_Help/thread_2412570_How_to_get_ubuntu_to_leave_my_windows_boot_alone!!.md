---
title: "How to get ubuntu to leave my windows boot alone!!"
date: 2019-02-14
forum: General Help
---

### Post by jasonmal on 2019-02-14
How do I get ubuntu to leave my windows boot alone;


I'm in 18.04.1.  


I have another drive that I wanted to install win10 on.  (Not a separate partition, no, I mean an entirely separate drive.) 


So, first I disconnected the ubuntu drive entirely, then booted to Win 10 dvd and installed win10. Worked fine.


I reconnected the ubuntu drive, rebooted, set it in bios boot priority to be above the windows drive (UEFI not legacy), and booted into Ubuntu with my fingers crossed.  


Booted into ubuntu just fine.


So, rebooted and went back into bios and made the windows drive priority over the ubuntu drive (both drives connected), 


I got the grub prompt.


Oh no! so I shut down, disconnected the ubuntu drive, rebooted.  


grub prompt.   


What?! That means just by the mere act of booting into ubuntu,  it installed grub on the windows drive?!?  


I don't want either drive to be dependent on the other (That's the whole point of having them on separate drives- if one crashes I can just use the other) hence my idea of a bootloader is just to use bios and switch the boot priority. 

Is that approach reasonably simple to do or is my plan wacky / impossible? I figured it was the safest way...


My biggest fear in general about ubuntu (and I bet I share this with most ubuntu users), is bootloader problesm. The grub prompt is in my nightmare.  So I thought having two separate drives would be the safest way. 


So my question is- how do I tell my ubuntu to leave windows alone. (And btw why isn't that the default behavior?)

---

### Post by oldfred on 2019-02-14
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If both installs are UEFI and you are booting in UEFI, the only issue will be which system does a major update and resets itself as first in UEFI boot order.
But if you have mixed BIOS and UEFI installs, it  could be UEFI settings.
Or if you have an old BIOS grub in MBR of Windows drive, but Windows in UEFI boot mode, and boot in BIOS mode, that will give the error you have.
Best to see details of configuration.

---

