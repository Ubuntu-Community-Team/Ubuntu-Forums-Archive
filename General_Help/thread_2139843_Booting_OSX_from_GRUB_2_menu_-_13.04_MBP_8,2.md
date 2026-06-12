---
title: "Booting OSX from GRUB 2 menu - 13.04 MBP 8,2"
date: 2013-04-28
forum: General Help
---

### Post by Daflippymaster on 2013-04-28
(Pretty green when it comes to ubuntu so bear with me.)

Just got 13.04 (3.8.0-19 kernel) installed on my macbook pro 8,2 via usb drive, then used the live cd to make the necesary changes to grub so that it would only use the integrated graphics on boot as opposed to that power hungry AMD (also it wouldn't boot otherwise)

Everythings running fine except for the fact that OSX won't boot from the grub menu.
The default options return what I believe is a kernel panic.

Tried the solution [here]("http://askubuntu.com/questions/179689/mac-os-x-wont-boot-from-grub-menu-in-ubuntu-precise-on-apple-mba5-2") that suggested making an entry in the 40_custom file of:
```

menuentry "OS X" {     
insmod hfsplus     
set root='(hd0,gpt2)'     
chainloader /System/Library/CoreServices/boot.efi 
}

```

and that returns "invalid root device"

Any ideas?

---

### Post by 2F4U on 2013-04-28
I am not familiar with dual booting Ubuntu and Mac OSX, but most of the tutorials suggest to use rEFind to avoid problems with grub.

[https://help.ubuntu.com/community/ubuntuprecisequantalon2011imac](https://help.ubuntu.com/community/ubuntuprecisequantalon2011imac)

However, there is one tutorial that offers additional approaches to dual booting:

[http://nosemaj.org/dual-boot-mac-linux](http://nosemaj.org/dual-boot-mac-linux)

---

### Post by Daflippymaster on 2013-04-28
Thanks so much, that was exactly what i was looking for

That second tutorial was probably most clear and easy to understand guide i've come accross when dealing with this subject.
Now if I could just get this darn wifi to work :rolleyes:

---

