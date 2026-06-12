---
title: "Laser Printer"
date: 2014-09-22
forum: General Help
---

### Post by box02-0 on 2014-09-22
Ubuntu 12.10

Hi. 

I am in the process of purchasing a decent laser printer/fax/copier, preferably wireless/usb. Can anyone here suggest a printer that would work with Ubuntu?

Thanks,

M...

---

### Post by rbmorse on 2014-09-22
HP is a good bet. They support Linux through the HPLIP project.  I have a CP2025DN and it's fine with Ubuntu.

---

### Post by buzzingrobot on 2014-09-22
Here's the link to the HP Linux unofficial Linux support site:  [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html).  Might be useful to verify there that a driver is available for a prospective purchase. (HP apparently doesn't permit distributions to package its Linux drivers.)

In my experience, Ubuntu will detect a printer and appear to set it up even if the correct driver is not installed.  I've had good luck using "hplip-gui" -- install it from the repos -- which is an HP tool that downloads and installs the correct driver.  Once that's done, I set the printer as the default in Ubuntu.

---

### Post by box02-0 on 2014-09-23
Thanks for the input. I'll start investingating HP ASAP. 

I've also heard that DELL makes a good laser - any thoughts?


Thanks,


M....

---

### Post by rbmorse on 2014-09-23
Dell tends to rebrand units from other OEMs.  If the base unit is an HP or Brother, you can probably get it working under Linux,but sometimes they install custom firmware and that can complicate things.  If you're considering buying a Dell printer, you should probably confirm the specific model (and options) are supported under Linux.

---

### Post by QIII on 2014-09-23
There are few things I recommend outright because I don't want to spend peoples' money for them, but HP printers are one of the things I will recommend.

Before you purchase, though, it would probably be worthwhile to ask about any particular model here on the forums.

---

