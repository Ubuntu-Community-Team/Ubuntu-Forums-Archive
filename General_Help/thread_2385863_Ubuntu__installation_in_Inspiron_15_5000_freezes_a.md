---
title: "Ubuntu  installation in Inspiron 15 5000 freezes at initial progress bar"
date: 2018-02-26
forum: General Help
---

### Post by geopan14 on 2018-02-26
I just bought a new Dell Inspiron with an Nvidia GeForce GTX 1050. 
I am trying to install ubuntu in a dual  boot setting, but when I boot from the USB and start installation, it freezes in the initial progress bar with the ubuntu logo, and I have to shut it down manually.
I've tried with ubuntu 16.04 and 17.04, secure boot on  and off. 
The system is UEFI and I create the bootable using rufus.
I noticed that just before the logo screen, there is a fast indication, a possible error I guess, but I don't have time to capture it.

Any suggestions?

---

### Post by dockland2 on 2018-02-26
> **geopan14 said:**
> I just bought a new Dell Inspiron with an Nvidia GeForce GTX 1050. 
I am trying to install ubuntu in a dual  boot setting, but when I boot from the USB and start installation, it freezes in the initial progress bar with the ubuntu logo, and I have to shut it down manually.
I've tried with ubuntu 16.04 and 17.04, secure boot on  and off. 
The system is UEFI and I create the bootable using rufus.
I noticed that just before the logo screen, there is a fast indication, a possible error I guess, but I don't have time to capture it.

Any suggestions?

Hi, have you turned off "Secure boot" in UEFI/BIOS?

E: Now i see, you've tried that already. Have you cleared the secure boot keys? I had to do that once, i disabled secure boot, but forgot to clear the keys. Anyhow, i think Ubuntu is able to boot with secure boot enabled.
Is Quick boot enabled, try disabling it.

Can be the nouveau driver, not sure with the 1050, i run 1080ti that works. Try add nomodeset as boot parameter, that have rescued me when i had trouble booting before.

---

### Post by geopan14 on 2018-02-26
Hi,

I just used ubuntu 16.04.1 instead of 16.04.3 and it worked perfectly.

---

### Post by TechnoJunky on 2018-03-06
I just bought the same laptop about a week ago as well.  I had to disable Secure Boot and enable legacy boot options.  I couldn't get it to boot to the USB drive if it were set to UEFI.  Also, I was not able to select the option to boot to a live image, it worked fine with one exception when selecting the install option.  That issue was on the screen asking if you want to download updates and another option.  After clicking that the install would freeze, or seem to.  I found that if I cancelled and ran it again (no reboot), the install would complete just fine.  I had to resintall twice due to an issue I caused, both installs froze at the same point, same resolution worked both times.

---

