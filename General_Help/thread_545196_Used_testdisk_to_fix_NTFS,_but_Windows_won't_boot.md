---
title: "Used testdisk to fix NTFS, but Windows won't boot"
date: 2007-09-07
forum: General Help
---

### Post by Jimmey on 2007-09-07
I accidentally set GRUB's root to my NTFS partition when I was retrying to recover GRUB, and in doing so, broke the NTFS drive that held Windows. I used Testdisk, rightly or wrongly, to fix the boot sector of the NTFS drive, and that made the drive readable, at least.

But when I try to boot into Windows, I see
> 
Starting up...
GRUB

And it just stays there.

I tried using the Windows recovery prompt to "fixmbr", but that just threw up the same thing. > GRUB, and nothing more.
Any ideas how to fix this?

Thanks.

---

### Post by thelocust on 2007-09-07
You need the Super Grub Disk. It's all over the forums if you do a quick search you'll find everything you need. (sorry no links I'm at work)

---

### Post by Seisen on 2007-09-07
Here is the link to SuperGrub.

[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by confused57 on 2007-09-07
You might want to try "fixboot", as well as "fixmbr".

---

### Post by amgat on 2007-09-07
I did the same mistake once. I solved the problem by downloading Hirens boot cd:
[http://homepage.ntlworld.com/hiren.thanki/bootcd.html](http://homepage.ntlworld.com/hiren.thanki/bootcd.html)

I used one of the tools from the MBR tools section

Good luck!

---

