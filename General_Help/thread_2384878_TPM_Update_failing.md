---
title: "TPM Update failing"
date: 2018-02-13
forum: General Help
---

### Post by wcnackers on 2018-02-13
Hi, 

I am trying to upgrade an Infineon TPM 2.0 chip to the latest verison of the firmware.   When I try to run the TPMFactoryUpd tool we received from Infineon, I am getting the following error:  TPM2.0:  PlatformAuth is not the Empty Buffer.  The firmware cannot be upgraded.  I can do this update from the UEFI shell but I prefer to the update from Ubuntu.   

To update the firmware from the shell, I have to first clear the TPM in the BIOS.  I wonder if when I boot to Ubuntu, the TPM "buffer" is re-initialized so it is no longer empty?  Does anyone have an idea of what I need to do to "Clear the Buffer" in Ubunut?

Thanks!

wcn

---

