---
title: "Need Help - Error 17 ?"
date: 2008-05-04
forum: General Help
---

### Post by Dariusz on 2008-05-04
Hi,

I need help as I have encounted an error during the install of Ubuntu 8.04:

I have vista (32bit) installed on an intel system.
Downloaded the Ubuntu 8.04 64 and installed on CD fine.
Ubuntu verified CD during install and installed on system while in windows mode.
On reboot, after windows mode install, Ubuntu 8.04 I suppose did the final install in its native mode.
On next reboot, when selecting Ubuntu from boot menu, I get the error:

Error 17:

(something to do with a partition error???)

Can some on help please. As I do not know what to do from this point to get Ubuntu started?

Thanks in advance for any assistance.

Dariusz

---

### Post by tinybit on 2008-05-04
```

Error 17: Cannot mount selected partition

```

In your menu.lst file, try to replace (hdX,Y) with (), i.e., a pair of empty parentheses.

---

### Post by Dariusz on 2008-05-05
Hi Tinybit,

Thank you for the reply.

I have searched  the c drive for the menu.lst file, and found 2 locations, being:

1. c:\ubuntu\winboot

&

2. c:\ubuntu\disks\boot\grub.

Both files are different.

The first menu.lst file has no occurance of (hdX,Y) in the file.

Where as the second menu.lst file has many occurances of (hdX, Y).

Do I change the second file, and all of the occurances of (hdX,Y) to ()?

Thanks,

Dariusz

---

### Post by ago on 2008-05-05
Yep it's the second one you have to change

---

