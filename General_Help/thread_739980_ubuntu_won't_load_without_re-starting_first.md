---
title: "ubuntu won't load without re-starting first"
date: 2008-03-30
forum: General Help
---

### Post by stellabella on 2008-03-30
I used the alt install to load Gutsy on my ThinkPad T20.  I am dual booting Gutsy and Windows2X.  

For some reason, I cannot load Ubuntu unless I have restarted my computer.  Ubuntu also could not power down properly, but I found the acpi=force solution in the forums (Thanks, Ubuntu Community!)  But, I'm not sure if I'm doing that right since I need to add it each time I boot.  

So, this is what I need to do to load Ubuntu:

Power up computer.
On grub menu, choose Windows2x and wait for it to load.
At Windows login prompt, choose 'restart'.
Windows powers down, and I am back to grub.
With cursor on Ubuntu, choose 'e' to edit
Move cursor to kernel command, choose 'e' to edit
Add acpi=force at the end of the kernel command line
Press enter to go back one screen
Choose 'b' to boot
See the "need acpi=force" line (sigh)
Get to Ubuntu log-in screen and everything works great (yeah!)

1- If I don't add the acpi=force, the laptop doesn't power off properly.  Then the only way to turn the laptop off is by pressing the power button.

2- If I try to load without first restarting, everything appears normal, except, after the Ubuntu splash screen, instead of getting the login, I see a flashing cursor for a few seconds, and then the screen goes blank.  

Any ideas?

Thanks

---

### Post by astoltz on 2008-03-30
Once you finally boot to Ubuntu, edit the file /boot/grub/menu.lst and add acpi=force to the end of the line that starts with "kernel": ```
sudo nano /boot/grub/menu.lst
``` Generally, there wll be more that one "kernel" section so be careful to pick the one that is the default boot kernel (not the recovery mode and not the memtest).

---

### Post by stellabella on 2008-03-30
You rock, astoltz!  The acpi=force is in there for keeps and it appears to shut down correctly.  (How newbie can I get?)

Ubuntu still doesn't load properly after a shut down, though.  To get back here I had to do my 'load windows and restart the laptop' thing.  

I'm still looking through other posts for this problem, but any help I can get here is greatly appreciated.

Thanks

---

