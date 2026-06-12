---
title: "Hit enter after reboot"
date: 2008-01-02
forum: General Help
---

### Post by rgorby on 2008-01-02
I have Gutsy installed on a USB stick, I need to be able to change the shutdown/reboot  procedure to not require you to hit enter.  Also, after rebooting the machine I have to reinsert the USB drive before it is recognized again.  We are setting up an environment of around 30 servers that will run from these USB drive it will be located offsite, so we wouldn't be able to reinsert the drives when they are rebooted.  Any help would be appreciated, I have only being using Linux for about 3 weeks.

---

### Post by pointone on 2008-01-03
The "quickreboot" boot option will disable the enter prompt. As for re-inserting the drives, that is likely a BIOS / power problem. See if there's an option in the BIOS to force harder (colder) reboots.

---

### Post by rgorby on 2008-01-03
Thanks for your input, could you give me any more information on the quick reboot option (where to change the configuration)?  I reboot with 'reboot -fn' and it works but I don't think that is what I want to be doing.

---

### Post by pointone on 2008-01-03
It's a live-initramfs option, which I only assume you're using (you may not be, though). You enable it as a boot option; i.e., enter it as a kernel boot parameter as you would "noacpi" or "quiet" or "single", etc. Depending on which bootloader you're using, exact usage will differ.

---

### Post by rgorby on 2008-01-07
Problem solved [http://www.pendrivelinux.com/2007/10/17/ubuntu-remove-the-prompt-to-eject-cd/](http://www.pendrivelinux.com/2007/10/17/ubuntu-remove-the-prompt-to-eject-cd/)

---

