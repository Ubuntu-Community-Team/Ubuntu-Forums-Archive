---
title: "can't find lilo.conf file"
date: 2006-12-26
forum: General Help
---

### Post by tyler_roach on 2006-12-26
I am a absolute Linux newbie trying to configure my USB ADSL modem with Ubuntu. I keep on receiving errors when running the setup script, and via research on the net, I've figured out that I'm supposed to edit my lilo.conf file in the following way to get the script to work:
lilo.conf, append:
acpi=on

The problem I'm having is that I can't find my lilo.conf file. It's not in /etc/, and I can't find it using a search. From what I have read, this seems to be an absolutely essential file, but I don't seem to be having any problems other than this modem issue. What should I do?

Thanks

---

### Post by Ramses de Norre on 2006-12-26
Ubuntu uses grub instead of lilo, and grub's config file is /boot/grub/menu.lst.
Acpi should be enabled on ubuntu by default though, I think.

---

### Post by tyler_roach on 2006-12-26
OK, thanks... Now, I looked at the grub file, but couldn't find anything in it about acpi. Assuming that my problem is with my acpi settings, how do I modify them. And what is acpi in the first place?
Thanks

---

