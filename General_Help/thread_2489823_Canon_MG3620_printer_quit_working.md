---
title: "Canon MG3620 printer quit working"
date: 2023-08-10
forum: General Help
---

### Post by michael-h-williamson on 2023-08-10
Hi, my Canon MG3620 quit working with Ubuntu 20. It works with Chromebook. It's connected via USB cable, but it's also wireless. On Ubuntu, I get this message in the cups error_log file when I try to print:

E [10/Aug/2023:16:04:34 -0500] [Client 31] Returning IPP client-error-not-possible for CUPS-Create-Local-Printer (ipp://localhost/) from localhost.

I tried installing samba and smbclient, but that didn't fix it. Does anybody have an idea how to fix this?

Thanks,
-Mike

---

### Post by michael-h-williamson on 2023-08-11
I also tried printing with Ubuntu 20 from a live DVD and that didn't work. Using Mint 21.2 from a live DVD (on the same computer) works.
I'd still like to know why Ubuntu doesn't work.

-Mike

---

### Post by michael-h-williamson on 2023-09-17
Well, Mint doesn't always work either. In Ubuntu, I now get this GTK warning in syslog:

 Unknown paper size na_letter_8.5x11in_borderless

Try other paper sizes doesn't work. Also, the CUPS web interface shows this message:

*No suitable destination host found by cups-browsed.*

The same computer, which is pretty old, has another problem now. The sound cuts out intermittently and when it does the S/PDIF port light comes on exactly when there's no sound. The S/PDIF is some kind of digital audio port. I muted it with alsamixer, but that didn't fix it.

-Mike

---

### Post by michael-h-williamson on 2023-09-19
Replying to my own post again - 

Installing Ubuntu 18.04 fixed both problems - the printer and the sound. Previously, I had tried Ubuntu 22 and EndeavorOS, also without success. The computer is a ZAreason brand with a B350M MORTAR motherboard. It's pretty old. The video controller is an NVIDIA GT218. 

Downgrading is an acceptable solution, but I'd like to know if Canonical cares if new Ubuntu releases are compatible with old hardware. There must be changes between Ubuntu 18 and 20 that broke the sound and the printing on my computer.

-Mike

---

