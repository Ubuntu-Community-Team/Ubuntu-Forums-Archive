---
title: "dell inspiron e1405 suspend"
date: 2006-08-09
forum: General Help
---

### Post by newlinuxusr on 2006-08-09
I have a dell insprion e1405 laptop and i am trying to get suspend to work. It suspends correctly and everything but when i go to bring it back out of suspend it says "[some numbers]hci_usb 2-1:1.0:resume error -5" and won't respond to anything and i just have to restart it. i tried adding MODULES="usbhid,hci_usb" but that didn't work. please help.

Thanks

---

### Post by newlinuxusr on 2006-08-09
bomp

---

### Post by newlinuxusr on 2006-08-09
bomp

---

### Post by ctoscano on 2007-02-23
I have the same laptop and suspend works for me using Ubuntu Edgy Eft, Beryl RC2. 

Updating RC2 to let suspend work, along with the following changes to 

> /etc/default/acpi-support file. Adjust the following line to read: 

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES="snd_hda_intel snd_hda_codec ipw3945"
# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true
# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true
 

I found the solution somewhere on-line.

---

