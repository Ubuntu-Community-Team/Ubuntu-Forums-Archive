---
title: "Operating System not Found"
date: 2015-02-10
forum: General Help
---

### Post by nebular2 on 2015-02-10
Hi
I've Xbuntu installed on a 128GB SSD that boots and runs without issue on my desktop. (Even on its own with all other drives disconnected) 
I want to now use it in my laptop (preferably) without reinstalling the OS. I have set SATA mode to ACHI in the BIOS and although the PC sees the disk, I receive a " Operating System not Found" error during boot.
Below is the output of my boot-repair dump. I have run the repair several times but it has unfortunately not (yet) been successful in resolving the issue. There is / was no dual booting of any kind going on. Any suggestions very much appreciated, thanks.

[http://paste.ubuntu.com/10158465/](http://paste.ubuntu.com/10158465/)

---

### Post by TheFu on 2015-02-11
Welcome to the forums.

In my experience, if boot-repair didn't work the 1st time, it never will.
Boot off a liveCD/flash drive.

Whoa .... you didn't think to mention the encryption or efi?

I'd put the disk back into the other system, create a non-encrypted backup, do a fresh install into the laptop, then restore the stuff I wanted there.
There might be ways to do what you want, but the encryption tells me it isn't worth it.

Hopefully someone else with encryption experience will reply in a day or two.

---

### Post by oldfred on 2015-02-11
You only show one drive, is that the SSD?

And if laptop is older and only BIOS, then the UEFI install will not work. You could convert it to BIOS  boot, but lose some of the advantages of UEFI. Boot-Repair does the conversion to BIOS boot if you add a bios_grub partition with no format and have bios_grub flag. It only needs to be 1 or 2MB. You actually are uninstalling grub-efi-amd64(UEFI) and installing grub-pc(BIOS). Then efi partition will not be used and grub will use MBR for BIOS boot.

---

### Post by nebular2 on 2015-02-17
Thanks for the replies / suggestions.
After a lot of trying different suggestions I ended up formatting, as was running out of time.
Thanks again.

---

