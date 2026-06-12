---
title: "Any way to boot from non-usb-bootable motherboard?"
date: 2007-02-02
forum: General Help
---

### Post by mdurham on 2007-02-02
mobo is an Asus P4S800-MX which doesn't support booting from usb. Does anyone know 'ANY' way of doing it?
Cheers, Mike

---

### Post by god2003 on 2007-02-02
I just did it using this [http://ubuntuforums.org/showthread.php?t=19428]("http://ubuntuforums.org/showthread.php?t=19428")
But be sure with the names, because isolinux is using Iso9660 names i used LINUX.LIN an INITRD.IMG instead to avoid checsum and other errors. But is working. I am booting from a CDRom into my external USB HDD (/dev/sda1).

Just in case you can't boot from cd you can use smart boot to boot from cd and then to the USB HDD. Is a litle tricky but works, both.

I apologize if i am not clear, but i'm spanish.

---

### Post by mdurham on 2007-02-02
Thanks god2003, I'll give it a try when I have some time. It seems to be just what I wanted.
Cheers, Mike

---

